> I want to use _Wishlist row (ProductCard horizontal + meta + actions + onRemove)_ from **ShopTab** for the file **Wishlist**. How can i do that?

Checking import paths against the shop components index

Copy the pattern, not the component. `ShopTab` is a demo page for the UI kit, so you build the same thing inside `Wishlist.tsx` and leave `ShopTab` as it is. This is untested because I can’t see your repo, so check the import paths.

**1. Imports.** `ShopTab` imports these relatively, from inside `src/components`. With your `@` alias they should look like this:

tsx

```tsx
import { useState } from "react";
import { Pagination, Button } from "@/components";
import { CardAction, ProductCard, type CardActions } from "@/components/shop/ProductCards";
import type { Product } from "@/v3/types";
import "./wishlist.scss";
```

If `ProductCard` and `CardAction` are already exported from `@/components`, put them in the first import line instead.

**2. Fake data.** Copy the `base` object and the `PRODUCTS` array from the top of `ShopTab.tsx`, and paste them above `export function Wishlist()`. Rename `PRODUCTS` to `FAKE_ITEMS` if you like. This stays until you connect the real `GET /wishlist`.

**3. State and the `a` object.** Every `ProductCard` needs an `a` prop, the set of card actions. `ShopTab` builds it in `useFakeShop`, which isn’t exported, so write a simple version inside your component. Because everything on this page is already wishlisted, `wished` always returns true:

tsx

```tsx
export function Wishlist() {
  const [page, setPage] = useState(1);
  const [removed, setRemoved] = useState<string[]>([]);
  const [cart, setCart] = useState<string[]>([]);
  const PAGE = 5;

  const a: CardActions = {
    currency: "CAD",
    inCart: (p) => cart.includes(p.id),
    wished: () => true,
    onAdd: (p) => setCart((c) => (c.includes(p.id) ? c : [...c, p.id])),
    onNotify: () => {},
    onWish: () => {},
    onOpen: () => {},
  };

  const items = FAKE_ITEMS.filter((p) => !removed.includes(p.id));
  const visible = items.slice((page - 1) * PAGE, page * PAGE);
  const totalCents = items.reduce((sum, p) => sum + p.priceCents, 0);
```

If TypeScript says `a` is missing properties, open the `CardActions` type in `ProductCards.tsx` and add what it lists.

**4. The rows.** Put this list between your filter chips and `<Pagination>`, with the same markup as the sample:

tsx

```tsx
<div className="ui-kit-shop-list">
  {visible.map((p) => (
    <ProductCard
      key={p.id}
      p={p}
      a={a}
      layout="horizontal"
      meta="Added recently"
      actions={
        <>
          <CardAction onClick={() => {}}>Add a note</CardAction>
          <CardAction icon label={`Share ${p.name}`} onClick={() => {}}>
            ↗
          </CardAction>
        </>
      }
      onRemove={(x) => setRemoved((r) => [...r, x.id])}
    />
  ))}
</div>
```

Replace `ui-kit-shop-list` with a class from your own `wishlist.scss`. The class name suggests it’s styled for the `/ui-kit` page only, so check whether it applies on the Account page.

**5. Fill the placeholders.** Now that you have real values, use them:

- `[total]` becomes `{items.length}`.
- `[PRICE]` becomes `${(totalCents / 100).toFixed(2)}`.
- `total={3}` in `<Pagination>` becomes `total={items.length}`.

**What each piece does**

- `meta` is the small line under the status.
- `actions` holds the extra buttons, built with `CardAction`.
- `onRemove` is the bin at the end of the row. It adds the item’s id to `removed`, the list filters it out, and React re-renders. That’s the `useState` Remove button we talked about earlier.

**Left for later:**

- The “Bring the removed ones back” button from the sample is simple: `setRemoved([])`. It could be your Undo.
- The filter chips need their own state.
- The Grid and Row toggle needs one more `useState`.
- Swap `FAKE_ITEMS` for the real `GET /wishlist` with `useEffect`, once the layout looks right.

> Now, i want the _ProductCard layout="vertical"_ from **ShopTab** for the file **Wishlist**. How can i do that?

The vertical card is the default layout, so you don’t set `layout` at all. The natural place for it on your page is the **Grid** button, with **Row** keeping the horizontal card. That needs one new `useState` for the view. This is untested because I can’t see your repo, so check the props against `ProductCards.tsx`.

**1. Add state for the view.** Next to your other `useState` lines:

tsx

```tsx
const [view, setView] = useState<"grid" | "row">("row");
```

**2. Wire the Grid and Row buttons.** Your two buttons currently have no `onClick`, and `is-active` is hard-coded on Row. Make both depend on `view`:

tsx

```tsx
<button
  type="button"
  className={`sh-chip views-grid ${view === "grid" ? "is-active" : ""}`}
  onClick={() => setView("grid")}
>
  Grid
</button>
<button
  type="button"
  className={`sh-chip views-row ${view === "row" ? "is-active" : ""}`}
  onClick={() => setView("row")}
>
  Row
</button>
```

**3. Show the matching list.** Replace the single list with two conditional blocks, using the same `&&` pattern as your tabs:

tsx

```tsx
{view === "grid" && (
  <div className="ui-kit-shop-grid">
    {visible.map((p) => (
      <ProductCard key={p.id} p={p} a={a} />
    ))}
  </div>
)}

{view === "row" && (
  <div className="ui-kit-shop-list">
    {visible.map((p) => (
      <ProductCard
        key={p.id}
        p={p}
        a={a}
        layout="horizontal"
        meta="Added recently"
        actions={/* same CardAction buttons as before */}
        onRemove={(x) => setRemoved((r) => [...r, x.id])}
      />
    ))}
  </div>
)}
```

**Two things to check**

- **Remove on the grid card.** In `ShopTab`, the vertical sample has no `meta`, `actions`, or `onRemove`, so I don’t know whether it supports them. Open the `ProductCard` props in `ProductCards.tsx` to see. If it doesn’t, you can use the heart instead. Change `onWish` in your `a` object so clicking the heart removes the item:

tsx

```tsx
  onWish: (p) => setRemoved((r) => [...r, p.id]),
```

That works because every wishlist item shows a filled heart, and clicking it to un-save is what shoppers expect.

- **The wrapper classes.** `ui-kit-shop-grid` and `ui-kit-shop-list` sound like they’re styled for the `/ui-kit` page. If the grid looks unstyled on the Account page, copy those rules into your `wishlist.scss` under your own class names.

The fake data and the `a` object stay the same, so nothing else changes. You’re only adding a toggle and a second way to render the same list.