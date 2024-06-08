# Linting and Auto Formating
This doc explains how to lint and format python scripts (.py files). To reduce dependencies, we only use the [ruff](https://docs.astral.sh/ruff/) package for both linting and formating. To install, run `pip install ruff`.

## Set up rules
The [default ruff rules](https://docs.astral.sh/ruff/configuration/#__tabbed_1_2) is a good start, and further cutomization can be made via adding `ruff.toml` or `pyproject.toml` files in the root directory of project. Example of customized `ruff.toml` file:
```
extend-exclude = ["test"] # ignore the test folder for both linting and formating.
[lint]
extend-select = ["I", "D"] # add isort and pydocstyle rules during linting.
ignore = [
    "D100", "D101", "D102", "D103", # Missing docstring in public module, class, method, function
    "D400", "D415", # Docstring first line should end with a period.
]
```
## Lint and reformat
Navigate to the root directory of the project, and run the following steps. By default, ruff only processes scripts (.py) and leaves notebooks (.ipynb) unchanged.
1. lint and fix auto-fixable errors: `ruff check --fix`
2. manually correct the rest errors flagged but not fixed from above step.
3. rerun `run check --fix` to confirm no errors left.
4. format the code by running `ruff format`
