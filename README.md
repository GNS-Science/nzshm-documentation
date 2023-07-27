# README

This project is documentation only. It uses poetry to install the necessary components for authoring these. 

A Github Action workflow will publish the output to a github pages site. 

## Documentation guides

 - [mkdocs user guide](https://www.mkdocs.org/user-guide/)
 - [mkdocs-material documentation](https://squidfunk.github.io/mkdocs-material/)
 - about [mermaid Diagrams](https://squidfunk.github.io/mkdocs-material/reference/diagrams/) with mkdocs-material.

## Content editing

```
git clone nshm-documentation
cd nshm-documentation
poetry run install
poetry run mkdocs serve
```

This will create a server running on http://locahost:8000 by default. Changes made in you editor should be immediately visible here.

Use regular git commits PRs etc to manage the review process with your co-authors.

### Editor setup

For VSCode recommend installing the extension `Markdown Preview Mermaid Support` which gives a close approximation of mkdocs formatting. 



