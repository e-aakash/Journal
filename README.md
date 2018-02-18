# Journal

A documentation of all the assets of WnCC and how to set them up. It can useful even if you're not related to WnCC. 

## Install Python and Sphinx
Install Python, the version I am using while writing this documentation is 2.7.10. You can use Python3 as well, there won't be any issues. 
[Sphinx](http://www.sphinx-doc.org/en/stable/) is a tool that makes it easy to create intelligent and beautiful documentation. To install it via pip 

`pip install sphinx sphinx-autobuild`

The theme used here is `sphinx_rtd_theme` install it by running 

`pip install sphinx_rtd_theme`

The best way to install all these requirements would be to create a virtual environment and simply do a 

`pip -r install requirements.txt`

## Build

Running the server for live-editing: `sphinx-autobuild source build/html` then open http://127.0.0.1:8000/ in your browser.

Build the page: `sphinx-build -b html source build`

## Content

You write all your content in the `source` directory in `.rst` files which stands for ReStructuredText. As far as directory structure is concerened it currently look like this

```
.
├── _static
├── _templates
├── conf.py
├── index.rst
├── portals
│   ├── django.rst
│   ├── portals.rst
│   ├── server.rst
│   └── templates.rst
├── website
│   ├── hook.rst
│   ├── jekyll.rst
│   ├── server.rst
│   └── website.rst
└── wiki
    ├── backup.rst
    ├── setup.rst
    └── wiki.rst
```

Every folder contains a `.rst` file with the same name which acts like a landing page. Each of that file follows this template

```
Wiki
====

.. toctree::
   :maxdepth: 4
   :caption: Contents:

   setup
   backup
```

The `===` signifies that the text written over it is a title, only by writing `===` does `Sphinx` generate a link to it. Note that in this toctree only the `.rst` files in the same directory are mentioned. Go ahead and do this for the rest. Great level of nesting is possible just be sure to change the `maxdepth` accordingly.