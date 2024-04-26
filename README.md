# Today I Learned

> Note taking during work or learn something new.

## How to use

This project is built using [Docsify](https://docsify.js.org/), please follow their [quick start](https://docsify.js.org/#/quickstart).

- Local: `$HOME/Downloads/TIL/_docs`
- Online: <https://thinhphan.github.io/til/> -> `wip` version, still have bugs

## Goals

- First pilot experiment with `Docsify`
- Load documents (Markdown files) in specific folders like `Obsidian Vault`, `Dropbox` and other project docs **dynamically** by configure in Settings.
- `_sidebar` should watch changes in the specific directory and update automatically.
- Should support `properties - YAML front mater` from `Obsidian` to publish the articles/docs by detect flag named `publish = true`

## Benefits

- No hosting required. Use GitHub Pages to publish this website.

## Drawback

- Sidebar & navbar should manually identical together

## TODO

- [ ] Option 1: How to load notes from `Obsidian Vault` without add them to the repo -> free my time.
- [ ] Option 2: `sync` notes periodically from `Vault` to `repos` -> it will give version control for publish notes.

## Notes

- [Docusaurus](https://docusaurus.io/blog/releases/3.2) supported Algolia DocSearch for searching in documents (full-text search) and it's free for technical documents.
