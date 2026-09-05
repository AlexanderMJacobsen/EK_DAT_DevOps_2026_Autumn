# Upgrade the application

Upgrade the server code from Python 2.0 to Python 3.x.x. Get a feel for the server. 

**Type**: Group work


**Motivation**: The goal is for everyone to study the code base and get familiar with the functionalities.


# The application

In case you missed it, the application can be found here:

https://github.com/who-knows-inc/whoknows_variations

The main branch is the same as what we copied from the server. 

---

## Install the Dependencies

The dependencies have been defined in `requirements.txt`. 

> [!CAUTION]
> The dependencies are pinned to very old version. Remove the versions in order to be able to run them.

You wouldn't want to install the dependencies globally. 

If you run other Python projects they would conflict with the legacy dependencies of `whoknows`. 

Python solves this with virtual environments. To create one (all platforms):


> [!TIP]
> Python has stopped including the a tool you will install after setting up your virtual enviroment. You need Python `3.12.0` or less. On Windows you can install old version of Python through the **Windows Store**.
> 
> For **Linux/Unix** MacOS(homebrew) you can use https://github.com/pyenv/pyenv to directly manage your installed version of Python.
> 
> Note for **Windows users**: pyenv does have a fork that allows you to run it as well, however this is not officially supported by the team behind pyenv.


```bash
$ python -m venv .venv
```

And to activate it (*nix users):

```bash
$ source ./.venv/bin/activate
```

Windows users:

```powershell
$ .\.venv\Scripts\activate
```

Then install the dependencies defined in `requirements.txt`:

```bash
$ pip install -r requirements.txt
```

You might need to define pip3 if you can't run pip.

---

## Converting from Python 2 -> 3.  

There are multiple ways to achieve this. One is to install and use the `2to3` tool.

#### Installation

Install the tool 2to3 (Windows/Linux):

```bash
$ pip install 2to3
```

Or on MacOS:

```bash
$ pipx install 2to3
```


#### Usage

Check installation and find some useful flags here.

```bash
$ 2to3 --help
```

You can run it on the server file like this:

```bash
$ 2to3 app.py
```

<!-- #### Check the result

In cause you use 2to3 to auto-fix it then save it to a different file and compare these two before you push the changes. 

For *nix systems, use the `diff` command to compare the files: 

```bash
$ diff app.py app.py3
```

For Windows use the FC (File Compare) command:

```powershell
$ FC app.py app.py3
``` -->

---

## Fix the shell script: `run_forever.sh`

In the `src` directory you can find `run_forever.sh` script. Use `shellcheck` to fix potential problems. 

#### Installation

MacOS:

```bash
$ brew install shellcheck
```

Windows:

```bash
$ scoop install shellcheck
```

#### Usage

Assuming that you are in the `src` directory:

```bash
$ shellcheck run_forever.sh
```
