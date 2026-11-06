# An Ineractive Book for Elementary Programming in Python 
[GitHub page](https://simflowdatalab.github.io/elemPython/)

## Folder tree
* `book_/`: the book materials including text, figures, notebooks, etc.
  - `_toc.yml`: include `*.md` files and Jupyter notebooks in the book.
  - `_config.yml`: config file to build the book. It also contains general info about the book.
  - `_md/`: contains the `*.md` text files.
  - `_static`: static files in the book, e.g. figures in the `*.md` files.
  - `_notebooks`: contains Jupyter notebooks in `.ipynb` format. 
  - `_bibliography/references.bib`: bibliography (in Tex format).
  - `_build`: contains the built Jupyter book, see below. 
* `docs/`: Contains the `html` version of the compiled book which is published on the GitHub page. 

## GitHub branches, development, and update
* There are two branches on the GitHub `https://github.com/salrm8/numericalPythonBook`:
   - `main`: To keep track of the source files.
   - `ghpage`: Only for the compiled book in `html` format to show on the GitHub page.

Note that these two branches have their own specific `./gitignore`.
Also, different branches for development can be created, but they should be merged with `main` before local compilation. 

* All the files and folders except `docs/` should be on `main` branch. Therefore, when one does changes in the source files (text, notebooks, etc), the update should be pushed on the `main` branch. 

* First, build the book *locally* by Jupter book, see below (we need to be on the `main` branch when compiling).
Then the `html` version of the book (located in `book_/_build/html/` should be manually copied to `docs/` and then pushed to the `ghpage` branch. The following steps are followed:
  1. `git checkout ghpage`
  2. cd `docs/`
  3. run `cp -r ../book_/_build/html/* .`
  4. commit the changes made in `docs/`:
    - `cd ..` (to the root)
    - `git checkout ghpage`
    - `git add /docs`
    - `git commit -m 'blahblah'`
    - `git push`
As a result, the [GitHub page](https://simflowdatalab.github.io/elemPython/) is updated!


## Compile the book by `Jupyter book`
This is how to compile the book *locally*:

### Creating an Conda Environment

The conda environment is provided as `environment.yml`. This environment is used for all testing by Github Actions and can be setup by:

1. `conda env create -f environment.yml`
2. `conda activate elemPyBook_`

### Building a Jupyter Book

Run the following command in your terminal:

```bash
jb build book_
```

If you would like to work with a clean build, you can empty the build folder by running:

```bash
jb clean book_
```

If jupyter execution is cached, this command will not delete the cached folder. 

To remove the build folder (including `cached` executables), you can run:

```bash
jb clean --all book_/
```

