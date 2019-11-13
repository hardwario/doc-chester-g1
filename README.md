# Repository: doc-chester

This repository contains source data for the CHESTER online datasheet. It uses **Sphinx** as a documentation generator altogether with **reStructuredText** as a lightweight markup language.

The documentation is hosted at [**Read The Docs**](https://readthedocs.org/) and is automatically built on commit to the repository.

Once built, the site hosted at: **https://chester.hardwario.com/**.


## Local Setup

You can build your local version of the documentation. All you need is Python 3.

Follow these steps:

1. Clone the repository:

       git clone https://github.com/hardwario/doc-chester.git

1. Go to the repository:

       cd doc-chester

1. Create Python 3 virtual environment:

       python3 -m venv venv

1. Activate the virtual environment:

       source venv/bin/activate

   > Don't forget to perform this step anytime you re-open the shell.

1. Install all the PyPI dependencies:

       python3 -m pip install -r requirements.txt

1. Build the documentation:

       make html

1. Opend the documentation:

       open build/html/index.html
