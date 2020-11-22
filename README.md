Utility Functions for Logic Bank.

## add_python_path
This is from [stackoverflow](https://stackoverflow.com/questions/40304117/import-statement-works-on-pycharm-but-not-from-terminal/63487350?noredirect=1#comment113296551_63487350).  Essentially, many of us have discovered the hard way is that:

* import statements often work in PyCharm

* but fail in VSCode, Command Line, etc

Setting ```PYTHONPATH``` is what makes imports work. I use the following VSCODE ```.env``` content so that it works for any project:
```
PYTHONPATH=${PROJ_DIR}:${PYTHONPATH}
```

This is essentially what PyCharm does when you check ```Add Content Roots to PYTHONPATH``` in your run/debug configuration. It's a helpful setting, but it spoils you because your code fails outside PyCharm.

Or, if you run in terminal, first export:

```
export PYTHONPATH=...
```


#### add_python_path
To address this, you can call the following:

```python
def add_python_path(project_dir: str, my_file: str) -> (str, str):
    """
    @param project_dir: enclosing path node (e.g., LogicBank
    @param my_file: callers __file__ variable
    @result (path_was_fixed, path)

    """

```
