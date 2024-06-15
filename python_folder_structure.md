# Python Folder Structure
In this document, we demonstrate one folder structure that supports using the python library in three different ways:
* download the repo, then import the library in jupyter notebooks
* download the repo, then run the library in command line
* install the library via pip

## Folder Structure
```
my_project/
  pyproject.toml
  requirements.txt
  my_library/
    __init__.py
    module_1.py
    module_2.py
    ...
```

## Usage
### Download repo and import in notebooks
In this usage, we will
1. download the `my_project` folder to a local directory
2. install required libraries w.r.t. `requirements.txt`
3. import the `my_library` in notebooks as follows:
```
import sys
sys.path.append('{parent_folder_of_my_library}')

from my_library import module_1
```
### Download repo and run in cmd
In this usage, we will
1. download the `my_project` folder to a local directory
2. install required libraries w.r.t. `requirements.txt`
3. navigate to the `my_project` folder
4. run the library in cmd:
```
> python3 -m my_library.module_1 --optional_arguments
```
### Install via pip
In this usage, we will 
1. install the library via `pip install` (assuming the library is already uploaded to pip or we get the wheel file)
2. then use the library in notebooks/scripts via `from my_library import module_1`
