1. Account page: fix the Wishlist tab and show tab labels
	- Problem: On the account page, the Wishlist tab never showed anything: its key is `"Wishlist"` but the content check looks for `"wishlist"`, so they never match. The top bar showed the raw key in capitals (`WISHLIST`), `Wishlist.tsx` nested a whole `PanelLayout` (the page shell) inside the page's own, and a commented-out `// let selectedTab...` line was left over (Fixes [#42](https://github.com/SpinHobby/spin-hobby/issues/42)).
	[[Error 42]]
	- Fix:
		Follows the "Recipe: a page like the admin" in `src/components/README.md`:
		- Tab keys are lower-case and match the content checks; the `Wishlist` key is now `wishlist`.
		- `title` is the active tab's label (`TABS.find(...)!.label`), not `selectedTab.toUpperCase()`.
		- The selected tab survives a reload through the address hash (`/account#wishlist`), initialized from `location.hash` in the `useState` initializer and kept with `history.replaceState` on select — the same pattern the admin uses.
		- `Wishlist.tsx` returns plain content — an `EmptyState` — with no `PanelLayout` inside.
		- The commented-out line is gone.
	- Testing:
		- `npx eslint src/v3/account/Account.tsx src/v3/account/Wishlist.tsx --max-warnings 0` passes.
		- `npx tsc --noEmit` reports only the pre-existing `BarcodeScanner.tsx` module error (present on unmodified `staging`; this branch adds no new errors).
		- Clicked through the four tabs in `npm run dev` at 1280px and 420px widths: each tab shows its content, the bar shows "Orders" / "Wishlist" / "Addresses" / "Profile", and reloading on `/account#wishlist` stays on Wishlist.