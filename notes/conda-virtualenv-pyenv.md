## Conda
Conda provides package, dependency and environment management.

[Conda](https://docs.conda.io/en/latest/index.html) replaces `virtualenv`. Can be used with languages other than Python.


`virtualenv` / `venv` = isolated virtual environments for Python libs
`pyenv` = isolate Python versions


## `venv` vs `virtualenv`
Python 3 ships with `venv`, which serves the same purpose for `virtualenv`. `virtualenv` supports both Python 2 and 3 though. If you don't use Python 2 (and you should not, unless it's legacy), using `venv` is preferred over `virtualenv`

## others
- `pyvenv` is deprecated in Python 3.6+, replaced by `venv`
- `virtualenvwrapper` set of extensions for `virtualenv` to make managing virtual environments easier.
- `pipenv` combines virtual environments with package management. aims to combine `Pipfile`, `pip` and `virtualenv` into one command on the command-line.

## Links
- https://stackoverflow.com/a/41573588