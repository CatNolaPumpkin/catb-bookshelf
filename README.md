# CatB's Bookshelf

A personal digital library: a walnut bookcase in a secret garden, with covers face-out, tabs for **Currently reading**, **Read**, **Want to read** and **To gift or donate**, and a **Banned books** filter.

Live site (once GitHub Pages is on): https://catnolapumpkin.github.io/catb-bookshelf/

## What's in this repository

| Path | What it is |
| --- | --- |
| `index.html` | The whole library: page, styles, script and book data in one file |
| `data/banned-books.json` | The 13 banned books with ISBNs and the `isBanned` flag |
| `docs/covers.md` | How automatic covers work (Open Library Covers API) |
| `docs/banned-badge.md` | Spec for the banned-books badge |
| `docs/claude-prompts.md` | The prompts for building or updating the library with Claude |

## Banned books starter shelf

From the essay "I Love Banned Books" (Heartware by CatB, Oct 9, 2026). All 13 sit in **Want to read** with the banned badge on.

| # | Title | Author | ISBN |
| --- | --- | --- | --- |
| 1 | I Know Why the Caged Bird Sings | Maya Angelou | 9780345514400 |
| 2 | The Bluest Eye | Toni Morrison | 9780307278449 |
| 3 | Beloved | Toni Morrison | 9781400033416 |
| 4 | The Color Purple | Alice Walker | 9780156028356 |
| 5 | The Autobiography of Malcolm X | Malcolm X | 9780345350688 |
| 6 | The Kite Runner | Khaled Hosseini | 9781594631931 |
| 7 | To Kill a Mockingbird | Harper Lee | 9780060935467 |
| 8 | The Handmaid's Tale | Margaret Atwood | 9780385490818 |
| 9 | 1984 | George Orwell | 9780451524935 |
| 10 | The Diary of a Young Girl | Anne Frank | 9780553296983 |
| 11 | Of Mice and Men | John Steinbeck | 9780140177398 |
| 12 | The Adventures of Huckleberry Finn | Mark Twain | 9780486280615 |
| 13 | The Catcher in the Rye | J.D. Salinger | 9780316769488 |

ISBNs are standard paperback editions. Edit a book on the shelf to change one.

## Book record

Each book in `index.html` (inside `<script id="library-data">`) looks like this:

```json
{"id": "bb9", "title": "1984", "author": "George Orwell", "genre": "Fiction",
 "list": "Want to read", "format": "", "where": "", "finished": "", "rating": 0,
 "line": "", "cover": "", "isbn": "9780451524935", "isBanned": true}
```

`cover` holds an uploaded photo. When it's empty, the page loads the Open Library cover by `coverId` (falling back to `isbn`); when there's neither, it draws a designed cover.
