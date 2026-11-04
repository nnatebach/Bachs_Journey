> I also want to use the buttons "All", "Price drop" and "Low stock" to filter the list of product in page Wishlist as well

The filters need one `useState` for the active filter, plus a filtered list that feeds the rows and the Pagination. This is untested because I can’t see your repo.

**1. Add the state and the filter rules.** Put the helpers above your component, and the state next to your other `useState` lines:

tsx

```tsx
type Filter = "all" | "drops" | "low";

const isDrop = (p: Product) => p.compareAtCents !== null && p.compareAtCents > p.priceCents;
const isLow = (p: Product) => p.status === "low";
```

tsx

```tsx
const [filter, setFilter] = useState<Filter>("all");
```

`isDrop` treats an item as a price drop when it has a `compareAtCents` higher than its current price. That’s the “on sale” logic the card already uses. `isLow` uses the `"low"` status from the fake data.

**2. Build the lists in steps.** This replaces the `items` and `visible` lines from before:

tsx

```tsx
const remaining = FAKE_ITEMS.filter((p) => !removed.includes(p.id));
const counts = {
  all: remaining.length,
  drops: remaining.filter(isDrop).length,
  low: remaining.filter(isLow).length,
};
const filtered = filter === "drops" ? remaining.filter(isDrop) : filter === "low" ? remaining.filter(isLow) : remaining;
const visible = filtered.slice((page - 1) * PAGE, page * PAGE);
```

**3. Wire the chips.** Setting the page back to 1 matters, because otherwise you could sit on page 2 of a list that now has one page:

tsx

```tsx
<button
  type="button"
  className={`sh-chip ${filter === "all" ? "is-active" : ""}`}
  onClick={() => { setFilter("all"); setPage(1); }}
>
  All · {counts.all}
</button>
<button
  type="button"
  className={`sh-chip ${filter === "drops" ? "is-active" : ""}`}
  onClick={() => { setFilter("drops"); setPage(1); }}
>
  Price drops · {counts.drops}
</button>
<button
  type="button"
  className={`sh-chip ${filter === "low" ? "is-active" : ""}`}
  onClick={() => { setFilter("low"); setPage(1); }}
>
  Low stock · {counts.low}
</button>
```

**4. Update the Pagination and add an empty state.**

tsx

```tsx
<Pagination page={page} pageSize={PAGE} total={filtered.length} onPage={setPage} />
```

The README requires an empty-state message for every list, and a filter can easily match nothing. Above your two view blocks, add:

tsx

```tsx
{filtered.length === 0 && <p className="ui-muted">Nothing matches this filter.</p>}
```

The kit may have an `EmptyState` component that looks better, so check its props.

**Choices to know about**

- The banner’s `[total]` and `[PRICE]` should still use `remaining`, not `filtered`, because “items you love” counts the whole wishlist whichever chip is active.
- With the demo data, “Price drops” shows 1 item (the Nendoroid) and “Low stock” shows the same one, since it’s both on sale and low.
- A real price drop needs more than a compare-at price. It means the price fell since the item was added, which depends on the wishlist API’s data. Ask him whether `/wishlist` returns something like the price at the time it was added. For now this version is a placeholder you can swap out later.