# purpledrop-manual

This repository contains content for the PurpleDrop Manual. 

It uses sphinx to render the markdown and/or RST formatted documents into HTML.

## Formatting

Most of the documentation in this project is written with markdown, instead of
the sphinx default of RST. It uses [MyST](https://myst-parser.readthedocs.io/en/latest/)
to parse the markdown, which allows all of the more complex RST rules -- e.g. figures with captions -- to be used in markdown.

## Local viewing

To build the HTML output, you can run `make html` in the project directory. You
can then open `_build/html/index.html` in your browser to preview.

Alternatively, you can use [sphinx-autobuild](https://pypi.org/project/sphinx-autobuild/)
to automatically re-build changes and reload your browser as you edit files: 

`sphinx-autobuild . _build/html`



