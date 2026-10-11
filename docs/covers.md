# Automatic covers

The library uses the **Open Library Covers API**. No API key, no sign-in.

```
https://covers.openlibrary.org/b/isbn/{ISBN}-{SIZE}.jpg?default=false
```

- `SIZE`: `S` (thumbnail), `M` (shelf and detail card), `L` (large).
- `ISBN`: 10 or 13 digits, no hyphens.
- `?default=false` returns a 404 when no cover exists, so the page keeps its designed cover instead of showing a blank image.

## Cover IDs (preferred)

The ISBN lookup can be slow or fail, so each book also stores Open Library's `coverId`, loaded directly:

```
https://covers.openlibrary.org/b/id/{coverId}-M.jpg
```

Find a cover ID at `https://openlibrary.org/isbn/{ISBN}.json` (the `covers` array).

## How the page uses it

1. A book with an uploaded photo (`cover`) always shows that photo.
2. Otherwise, if it has a `coverId` (or failing that an `isbn`), the page draws the designed cover and lays the Open Library image on top, fading it in only once it loads.
3. If the image fails (missing cover, network blocked), it is removed and the designed cover stays.

## Books with no cover ID

Order of sources: uploaded photo, then `coverId`, then a remembered lookup result, then the ISBN cover. Lookups: books with an ISBN ask Google Books by ISBN; books without one search Open Library by title and author, then Google Books.

## Books with no ISBN

For a book with no photo, `coverId` or `isbn`, the visitor's browser searches Open Library once:

```
https://openlibrary.org/search.json?title={title}&author={author}&fields=cover_i&limit=3
```

The first result with a cover supplies the cover ID. Each answer is remembered in that browser (misses are retried after 14 days), and lookups run one at a time to stay well under the rate limit. If a book shows the wrong cover, add its ISBN or `coverId` to the book record and that takes priority.

## Limits

- **Rate limit:** 100 requests per IP per 5 minutes. The browser caches covers, so each one is fetched once.
- **Where it works:** on GitHub Pages or any normal web host. The Claude-hosted copy of the page can't load images from other sites, so covers there stay designed.

## Alternative: Google Books API

`https://www.googleapis.com/books/v1/volumes?q=isbn:{ISBN}&key={KEY}` returns `items[0].volumeInfo.imageLinks.thumbnail` plus description, categories and page count. Needs a free API key. Use it when Open Library has no cover for an ISBN.
