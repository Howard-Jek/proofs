# Proof pages

Hosting for proof pages made with the builder in
[`work-stuff/proof-page`](https://github.com/Howard-Jek/work-stuff/tree/main/proof-page).
Served by GitHub Pages at **https://howard-jek.github.io/proofs/**.

| File | What it is |
|---|---|
| `index.html` | Tells buyers how to check a proof page |
| `404.html` | Shown for any code that doesn't exist: tells the buyer not to pay yet |
| `<CODE>.html` | One proof page per card, straight from the builder |
| `.nojekyll` | Serves files as-is, with no Jekyll build |

In the builder's Settings, put `howard-jek.github.io/proofs` as the hosting address.

## Publishing a proof

1. Download the page from the builder. It's named after its code, e.g. `KB5-X95.html`.
2. On GitHub, in this repo, go to **Add file → Upload files**, drop it in the root, and commit to `main`.
3. Within a minute or two it's live at `https://howard-jek.github.io/proofs/KB5-X95.html`. Open
   it once on your phone before sending the link to the seller.

Don't rename the file. The code in the link is the one buyers compare with the handwritten code.

## Taking a proof down

Delete the file and commit. The link then shows the 404 page.

**Deleting doesn't erase it from the repo's history.** The old commit, with the seller's photos,
can still be reached on GitHub. When a seller asks for their photos to be removed, rewrite the
history so nothing old survives:

```sh
git clone https://github.com/Howard-Jek/proofs.git && cd proofs
git rm <CODE>.html                      # if not already deleted
git checkout --orphan fresh
git commit -m "Proof pages"
git branch -D main && git branch -m main
git push --force origin main
```

This replaces the whole history with the current files. Every other proof keeps its URL.
