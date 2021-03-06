
## Generating documentation

Pydoc-markdown ended up being the easiest to modify, and unlike sphinx/napoleon,
wasn't a mixture of google docstrings plus RST, which ended up being pretty
ungainly to work with.  Instead, it's a mixture of google docstrings and markdown,
which works a bit better.  Also, though the API of pydoc-markdown is less
formalized, implementing changes is also less convoluted than for sphinx.

### PRE: Installation
You probably want to run the following because the auto-magic install doesn't work:
```
pip install git+https://github.com/quiltdata/pydoc-markdown.git@quilt
```

### From the `gendocs` dir:
Using the venv that t4 is installed with, execute build.py:
```
python build.py
```

If params are given, they are passed through to pydocmd.  Otherwise, 'build' is
assumed.

If the quilt version of pydocmd is not installed, build.py will ask to install it.

Configuration for pydocmd is stored in `pydocmd.yml`.  Original project can be 
found on github at https://github.com/NiklasRosenstein/pydoc-markdown

The Quilt version of pydocmd is modified to:
* include additional __special_methods__ and to easily to exclude them
* Fix issue reading classmethod/staticmethod signatures
* Use signatures as title, not under title in a code block
* Minor display improvements/preferences
* Handle google docstrings to render them as markdown
* Fix handling of codeblocks under sections
* Add handling for doctest-style code examples:

