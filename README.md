# calvinkim85.github.io: the public website for the games' store pages (published 2026-11-12)

A plain static GitHub Pages **user site**. It exists for one reason the project sites (like `dusk-site`,
`lumentor-site`) can't cover: AdMob reads `app-ads.txt` only from the **root of the developer website's domain**
("Upload your app-ads.txt file to the root directory of your developer website"; a website address with a path
is crawled at its domain's root: AdMob Help, "Set up an app-ads.txt file for your app", answer 9363762, read
2026-11-12). A project site lives at `calvinkim85.github.io/<repo>/`, so its root is this repo.

## What is here

| Address | File | Comes from |
|---|---|---|
| `https://calvinkim85.github.io/app-ads.txt` | `app-ads.txt` | Inflate to Fill's AdMob publisher line |
| `https://calvinkim85.github.io/inflate-to-fill/privacy.html` | `inflate-to-fill/privacy.html` | Inflate to Fill's privacy policy (both stores, and Settings in the apps) |
| `https://calvinkim85.github.io/inflate-to-fill/privacy-ko.html` | `inflate-to-fill/privacy-ko.html` | The same in Korean |
| `https://calvinkim85.github.io/inflate-to-fill/support.html` | `inflate-to-fill/support.html` | Support page; also the "developer website" on both store pages |
| `https://calvinkim85.github.io/robots.txt` | `robots.txt` | Lets every search engine read the whole site (the pages are meant to be found; nothing here is private) |

Project sites keep working beside it: `calvinkim85.github.io/dusk-site/` and `/lumentor-site/` are served from
their own repos. Don't add folders here with those names.

## How to update

The pages are written in the game's repo, never edited here:

```
cd ~/Desktop/Code/inflate-to-fill
npm run release-ids                                         # fills the pages into dist/site/ from release-ids.json
npm run stage-site -- ~/Desktop/Code/calvinkim85.github.io  # copies only the pages with nothing left to fill
```

`stage-site` copies a page only when no placeholder is left in it, and it never commits or pushes.

## How to test

Open each file in a browser. `grep -rn '\[' --include=*.html .` should find no square-bracket placeholder.
After pushing: open each address above, and in AdMob, Apps › app-ads.txt, check that AdMob found the file (it can
take up to 24 hours).

## Where it is hosted

Not yet. Creating the public GitHub repo and pushing is the owner's step (`docs/publish-day.md` in
inflate-to-fill, step 9):

```
cd ~/Desktop/Code/calvinkim85.github.io
git add -A && git commit -m "Inflate to Fill pages and app-ads.txt"
gh repo create calvinkim85/calvinkim85.github.io --public --source . --push
```

GitHub serves a repo named `<user>.github.io` from its `main` branch at `https://<user>.github.io/` without
further settings; check under the repo's Settings › Pages that it shows the address.
