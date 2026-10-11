# Prompts

## Update this library (what was done)

1. Add the 13 banned books from "I Love Banned Books" to **Want to read**, each with its ISBN and `isBanned: true`.
2. For any book with an ISBN and no uploaded photo, load the cover from `https://covers.openlibrary.org/b/isbn/{ISBN}-M.jpg?default=false`, falling back to the designed cover.
3. Add the banned badge to the cover and detail card, and a **Banned books** filter beside the tabs.
4. Keep the code, data, cover notes, badge spec and these prompts in this repository.

## Build your own (for everyday readers)

From the "I Love Banned Books" essay, for people who want a personal library without code.

**Option A: a simple catalog.** Ask Claude to act as your personal librarian and build a catalog in a spreadsheet or Notion with columns for title, author, shelf (Read, Currently reading, Want to read, To gift or donate), format, rating, a favorite line, and a "Banned book" checkbox.

**Option B: a visual bookshelf.** Ask Claude to build a personal digital bookshelf web page:

- **The look:** a calm wall in one soft color with wooden shelves and covers face-out.
- **How it works:** hovering or tapping a book lifts it and shows the title; clicking opens a card with the details and the one line you want to remember; a "Banned book" checkbox adds a badge; tabs filter by Read, Currently reading, Want to read, and To gift or donate.
- **Updating it:** an "Add a book" button and an "Edit" option on each book; upload a cover photo, or get a designed cover if you don't have one; changes stay saved; only you can edit, and anyone with the link can look.
- **Getting started:** build it first, then ask for your first few books; if you're unsure of an author or exact title, Claude checks; when it's done, Claude explains in simple steps how to add more.
