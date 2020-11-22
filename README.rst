
****************************
Logic Bank Utility Functions
****************************

Utility Functions for Logic Bank, and others (no Logic Bank dependencies).

Addressing Python Path, for proper import operation
===================================================

This is from `stackoverflow <https://stackoverflow.com/questions/40304117/import-statement-works-on-pycharm-but-not-from-terminal/63487350?noredirect=1#comment113296551_63487350>`_.  Essentially, many of us have discovered the hard way is that:

* import statements often work in PyCharm

* but fail in VSCode, Command Line, etc

Setting ```PYTHONPATH``` is what makes imports work. I use the following VSCODE `.env` content so that it works for any project:


    PYTHONPATH=${PROJ_DIR}:${PYTHONPATH}


This is essentially what PyCharm does when you check **Add Content Roots to PYTHONPATH** in your run/debug configuration. It's a helpful setting, but it spoils you because your code fails outside PyCharm.

Or, if you run in terminal, first export:

    export PYTHONPATH=...



add_python_path
###############

You may find it easier to address this in your application, by calling the following:

.. code-block:: Python

    def add_python_path(project_dir: str, my_file: str) -> (str, str):
        """
        @param project_dir: enclosing path node (e.g., LogicBank
        @param my_file: callers __file__ variable
        @result (path_was_fixed, path)

For example, if you are several levels deep in a project were the root is ```MyProjectRoot```:

.. code-block:: Python

    import logic_bank_utils.util as logic_bank_utils

    (did_fix_path, sys_env_info) = \
        logic_bank_utils.add_python_path(project_dir="MyProjectRoot", my_file=__file__)
    print("\n" + did_fix_path + "\n\n" + sys_env_info + "\n\n")


Depends on:
-----------
- Python 3.8



Change Log
----------

0.3.0 - Initial Version

0.4.0 - Improved doc
