# Account page: Wishlist tab never shows, and the title shows the tab's key

## What's wrong

On the account page (`src/v3/account/Account.tsx`):

1. **The Wishlist tab never shows anything.** The tab's key is `"Wishlist"` (capital W) but the page checks `selectedTab === "wishlist"`, so they never match.
2. **The title shows the tab's key in capitals** (`WISHLIST`, `ORDERS`) instead of its name.
3. **`Wishlist.tsx` puts a second `PanelLayout` inside the first.** `PanelLayout` is the whole page (side tabs + top bar); a tab's content should just be cards, tables and so on.
4. A commented-out line (`// let selectedTab...`) is left over.

## Done when

 - [ ] Keys are lower-case and match their checks; clicking Wishlist shows the Wishlist content.

 - [ ] The top bar shows the tab's label ("Wishlist"), not its key.

 - [ ] `Wishlist.tsx` returns plain content (for now one `Card` or an `EmptyState`), with no `PanelLayout` inside.

 - [ ] The commented-out line is gone.

 - [ ] Bonus: keep the tab in the address (`/account#wishlist`), like the admin does, so reloading stays on the same tab.

## Hints

- Look at how `src/v3/admin/Admin.tsx` sets `title` and keeps the screen in the `#hash`.
- Read [START-HERE.md](https://github.com/SpinHobby/spin-hobby/blob/staging/START-HERE.md) and the "Recipe: a page like the admin" in `src/components/README.md`.
- To see it: `npm run dev`, then [http://localhost:3000/account](http://localhost:3000/account) (the `account` flag is on locally and on staging).

A good first issue: small, and it unblocks every other account-page issue.