# Python for web development on Windows

Python for web development on Windows, using the Windows Subsystem for Linux (WSL). See more details, https://learn.microsoft.com/en-us/windows/python/web-frameworks.

## Create a new project

In your Ubuntu command line, navigate to where you want to put your project and create a directory for it: `mkdir MyPythonProject`.

## Install Python, pip and venv

Ubuntu LTS comes with Python 3.10 already installed, but it does not come with some of the modules that you may expect to get with other Python installations.

1. Confirm that Python3 is already installed by opening your Ubuntu terminal and entering:
`python3 --version`

2. Install **pip** by entering:
`sudo apt install python3-pip`

3. Install **venv** by entering:
`sudo apt install python3-venv`

Optional: You can also install **virtualenv** by entering:
`pip3 install virtualenv` or `pip install virtualenv`

## Create a virtual environment

Using virtual environments is a recommended best practice for Python development projects.

1. Open terminal and inside your *MyPythonProject* project folder, use the following command to create a virtual environment named **.venv**

```
python3 -m venv .venv                  // using venv
virtualenv .venv                       // using virtualenv
virtualenv -p <python-version> .venv   // using virtualenv and certain python version
```

2. Activate the virtual environment, enter:

```
source .venv/bin/activate
```

When you're finished with your virtual environment, enter the following command to deactivate it:

```
deactivate
```

Suggestion is to use the name **.venv** to follow the Python convention. Some tools (like pipenv) also default to this name if you install into your project directory.

## Working with VS Code

VS Code uses the Remote - WSL Extension (installed previously) to treat your Linux subsystem as a remote server. This allows you to use WSL as your integrated development environment.

**Recommendation**: Install the Microsoft Python extension. Find the Python (ms-python.python) by Microsoft extension and select the green Install button.

1. Open your project folder in VS Code from your Ubuntu terminal by entering:
`code .`

2. Close your Ubuntu terminal. Moving forward we will use the WSL terminal integrated into VS Code.

3. Open the WSL terminal in VS Code

4. Activate the virtual environment, enter:
`source .venv/bin/activate`

5. Install needed python packages using **pip**, enter e.g.
`pip install flask`

6. Create a needed files for your Python code

7. In the terminal, run the python app