# Banned books badge

Marks banned or challenged books.

| Property | Spec |
| --- | --- |
| Field | `isBanned` (boolean) on each book record |
| Shelf view | Small rounded tag on the lower part of the cover, above the author line |
| Detail card | Larger tag on the cover, plus a "Banned book" label next to the shelf name |
| Color | Deep red `#8B0000` with white text |
| Text | `BANNED`, small uppercase sans-serif, letter-spaced |
| Off | When `isBanned` is false, no badge appears |

## Filter

A **Banned books** toggle sits at the end of the tab row with a count of all banned titles. When on, each tab shows only its banned books. The choice is remembered per browser.

## Editing

The add/edit form has an **ISBN** field and a **Banned or challenged** checkbox that sets `isBanned`.
