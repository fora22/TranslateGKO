# **PYTHON: VIRTUAL ENVIRONMENT**

C-based project needs to include header files and libraries individually when compiling the script. Python, on the other hand, requires installation of modules under the interpreter directory.

However, when working with multiple Python projects, having all the packages installed in a single interpreter is inconvenient and inefficient. This is why separating Python environment is essential which can be done using virtual environment.

## `venv` Package

The Python3 has virtual environment package `venv` included by default. The package support creating lightweight virtual environments with their own site directory, optionally isolated from system site directory.

Each virtual environment has its own Python binary (which matches the version of the binary that was used to create this environment) and can have its own independent set of installed Python packages in its site directory.

### Creating Environment

Creating a virtual environment under the name `.venv` on desired project directory is done as follows:

```
python -m venv D:\Workspace\Python\project\.venv
```

### Activate Environment

Here, the term "activating" means activating virtual environment on the command prompt or terminal. While this is unnecessary when running the script under virtual environment, activation is required when installing packages using pip on console.

* Windows:

    ```
    D:\Workspace\Python\project\.venv\Scripts\activate.bat
    ```

* Unix (e.g. Linux and macOS):

    ```
    source ~/Workspace/Python/project/.venv/bin/activate
    ```

### Deactivate Environment

To exit from virtual environment activated console, user need to "deactivate" virtual environment.

```
deactivate
```

This is same as enter the command `PATH=D:\Workspace\Python\.venv\Scripts\deactivate.bat`. Because of this, relocating the virtual environment directory will cause `deactivate` command unable to recognize the path.
