# Example Readme
This repo demonstrates how to create an example python package using a pyproject.toml file. This is the modern way preferred by the Python Packaging Authority (PyPa) as the standard configuration file for building Python projects, as it is more declarative and future-proof. The transition to pyproject.toml is part of the PEP 518 standard

## Setup
To build a new project ensure that you have met the following requirements:
1. Place your project <my_project_name> in another folder named <my_project_name>_build so that your folder tree looks something like this: 

```
my_project_name_build
|__
   my_project_name
   |__
      src/
      |__
         file1.py
         file2.py
         __init__.py
         my_submodule/
         |__
            __init__.py
            file3.py
            file4.py
      test/
      |__
         __init__.py
         my_test1.py
         my_test2.py
      |
      __init__.py
   |
    pyproject.toml
    LICENSE.txt
    README.md
```
Note that every directory and subdirectory has an __init__.py file.  These files are required in order to make your repo a package. It is ok if these files are blank.

2. Ensure that your license file and README.md is not blank as these files are used by the toml file.  Tht said they are optional, but highly recommended!
3. Fill out the pyproject.toml with the appropriate values for your project.  See the example in this repo. Ensure that your project name has a unique name so that it does not collide with existing pypi libraries. To check you can go to the following website: https://pypi.org/
4. run the commands

```python
pip install build
python -m build
```
Only run the `pip install build` if you don't already have the package

To install the package locally run:
`pip install -e .` in the same directory as your .toml file.  This will locally install your repository as a python package in editor mode. This means that if you make changes to your code, that will also result in changes to the package.  If you don't want this behavior then simply run `pip install .`.

5. Finally in `my_project_name/__init__.py` create import statements to more easily access your functions.  For example 

```python3
# __init__.py
from src.file1 import (
   my_func1,
   my_func2
)
from src.my_submodule.file3 import (
   my_func3,
   my_func4
)
...
```
This makes it significantly easier for your end user because rather than writing code like this:

```python3
from my_project_name.src.my_submodule.file3 import my_func3

my_func3()
```

they can simply run:

```python3
from my_project_name import my_func3

my_func3()
```