# Building Package
This doc tracks the basic setups for using [pyproject.toml](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/) to package a python library. Please check the previous page for more details. This doc only lists a few choices.

## Define pyproject.toml
### Build backend
This part is specified in `[build-system]`.
* choose to use `hatchling` as build backend since it has [better default behaviors](https://hatch.pypa.io/1.8/why/#build-backend).

### Project setups
This part is specified in `[project]`.
* __Package version__ is set dynamically: `dynamic = ["...", "version"]`. Please refer to [this guide](https://hatch.pypa.io/1.8/version/#configuration) on how to set version dynamically. This ensures [single-sourcing the package version](https://packaging.python.org/en/latest/guides/single-sourcing-package-version/#single-sourcing-the-version).
* __Package dependencies__ is set dynamically based on `requirements.txt`. Please refer to [this guide](https://github.com/repo-helper/hatch-requirements-txt?tab=readme-ov-file#usage) on how to set dependencies dynamically. Please see [dependencies.md](./dependencies.md) on how to extract dependent libraries.
* __Package descriptions__. The `description` field should contains a one-line description and will be used as headline on PyPI project page. The `readme` field is pointed to the readme file: `readme = "README.md"`.
* __Package license__. It points to the license file of the repo: `license = {file = "LICENSE"}`

### Tool setups
* [Ruff](https://docs.astral.sh/ruff/) is chosen as the linting and formating tool. Its rules can be specified either in `pyproject.toml` or `ruff.toml`. We choose to use `ruff.toml` so that linting and formating can be configured during development phase, which is before and independent of packaging. For details about this step, please check out [lint_format.md](./lint_format.md).
* Specify which files will be shipped in each build. Follow [this example](https://hatch.pypa.io/1.9/config/build/#patterns).

## Test build locally
### Generate distribution files
1. Create a new python virtual environment for packaging (no need to install any dependencies).
2. Install hatch: `pip install hatch`.
3. Navigate to the root directory of the project. It should contains `pyproject.toml`.
4. Run `hatch build`. It will generate distribution files (e.g. the `.whl` file) in the `dist` directory of your project root directory.
### Test distribution files
1. Create a new python virtual environment for testing.
2. Install package from the newly built distribution file: `pip install {your_distribution_file}.whl`.
3. Test your package.

## Publish build
Follow steps here: https://packaging.python.org/en/latest/tutorials/packaging-projects/#uploading-the-distribution-archives
