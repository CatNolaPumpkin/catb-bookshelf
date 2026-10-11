# Automatic covers

The library uses the **Open Library Covers API**. No API key, no sign-in.

```
https://covers.openlibrary.org/b/isbn/{ISBN}-{SIZE}.jpg?default=false
```

- `SIZE`: `S` (thumbnail), `M` (shelf and detail card), `L` (large).
- `ISBN`: 10 or 13 digits, no hyphens.
- `?default=false` returns a 404 when no cover exists, so the page keeps its designed cover instead of showing a blank image.

## How the page uses it

1. A book with an uploaded photo (`cover`) always shows that photo.
2. Otherwise, if it has an `isbn`, the page draws the designed cover and lays the Open Library image on top, fading it in only once it loads.
3. If the image fails (missing cover, network blocked), it is removed and the designed cover stays.

## Limits

- **Rate limit:** 100 requests per IP per 5 minutes. The browser caches covers, so each one is fetched once.
- **Where it works:** on GitHub Pages or any normal web host. The Claude-hosted copy of the page can't load images from other sites, so covers there stay designed.

## Alternative: Google Books API

`https://www.googleapis.com/books/v1/volumes?q=isbn:{ISBN}&key={KEY}` returns `items[0].volumeInfo.imageLinks.thumbnail` plus description, categories and page count. Needs a free API key. Use it when Open Library has no cover for an ISBN.
