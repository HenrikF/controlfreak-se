# controlfreak.se

The page at controlfreak.se (and www.controlfreak.se), served by GitHub Pages.

ControlFreak, the course-setting app, has moved to
[course.controlfreak.se](https://course.controlfreak.se). It used to run here, and
everything a user made is stored in the browser for this address. This page moves it:

1. It reads what ControlFreak stored here: the keys starting with `kartvisaren.` or
   `controlfreak.` in localStorage, and the map cache in IndexedDB (`kartvisaren.maps`).
2. It hands them to `https://course.controlfreak.se/flytt` in a hidden iframe. The two
   addresses are the same site, so the frame may write the new address's storage.
   `/flytt` (in ControlFreak, `src/lib/domain-move.ts`) accepts data only from
   controlfreak.se and www.controlfreak.se, adds what is missing and never overwrites.
3. It sends the visitor to the same path, query and hash at the new address, so old
   links keep working, with `flyttat=<n>` so the app can say how many projects came along.

Nothing is deleted here. A visitor with nothing stored is sent on at once. If the move
fails, the visitor can try again or go anyway; the data stays here either way.

`404.html` is the same file as `index.html`, so every old path gets the page too.

Later this can become the start page for the family of apps under controlfreak.se.

## DNS

- `controlfreak.se`: A records to GitHub Pages (185.199.108.153, 185.199.109.153,
  185.199.110.153, 185.199.111.153).
- `www.controlfreak.se`: CNAME to `henrikf.github.io`.

## License

MIT, see [LICENSE](LICENSE).
