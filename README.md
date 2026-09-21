# The Science of Online Entrepreneurship — flipbook

Live at **https://book.bobbyboomer.com**, embedded on bobbyboomer.com.

Two files, no build step. `index.html` renders `book.pdf` with PDF.js and turns the pages with
StPageFlip, both from a CDN.

## Updating the book

Replace `book.pdf`, commit, push. Live within a couple of minutes; readers may need a hard refresh.

**If the new PDF does not have a blank first page, set `FIRST_PAGE` back to `1`** near the top of the
script in `index.html`. The 2026-09-21 export had a blank page 1 with the cover art on page 2, so the
viewer skips it. The Download button always serves the whole file.

## Reusing this for another PDF

Copy both files into a new folder, drop in the new PDF as `book.pdf`, and adjust `FIRST_PAGE`. Nothing
else needs touching.

## Two things that will bite you

- **The PDF must be served from this same origin.** Browsers block a cross-site PDF fetch, which is why
  the file is committed here rather than linked from the CDN it already lives on.
- **`RENDER_SCALE`** near the top of the script controls page sharpness. It is `2`. Raising it sharpens
  the pages and slows the first load, because every page renders in the browser before the book appears.
