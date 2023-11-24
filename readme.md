# Run Locally

1. install python 
2. install mkdocs: `pip install mkdocs`
3. install theme: `pip install mkdocs-material`
3. install plugins:
    *  `pip install mkdocs-callouts`
4. run serve.bat

# Deploy to github pages

github Actions should take care of it (.github/workflows/ci.yml). new plugins need to be installed

alternative run `mkdocs gh-deploy`. If authentication fails it probably has created a a local commit with could not be pushed => push manually


Plugins:
- https://pypi.org/project/mkdocs-callouts/

# MkDocs

For full documentation visit [mkdocs.org](https://mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## How to

> Some statement

> [!TIP] 
> asdasdasd asdasdasdasd asd ds asd asd ads ads ads das asd adsd asd asad sdas a asd das das 
> asd
---

> [!note]-
> asdasdasd asdasdasdasd asd ds asd asd ads ads ads das asd adsd asd asad sdas a asd das das 
> asd

some <mark>marked</mark> text

- [x] Write the press release
- [ ] Update the website

