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