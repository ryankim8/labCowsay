# lab - pip install and PEP8

![](https://github.com/mikeizbicki/lab-cowsay/workflows/flake8/badge.svg)&nbsp;
![](https://github.com/mikeizbicki/lab-cowsay/workflows/command_line/badge.svg)&nbsp;

## Part 0: setup

For this lab you will need to make a copy of this repo on github.
Follow the standard procedures to create a new empty repo through the github interface,
clone this repo onto your computer,
and then push to your new empty repo.

Each part below will have you pushing to your new repo to fix parts of the github actions,
so you'll need to get this repo setup before continuing.

## Part 1: pip

This repo contains a script that shows a cow saying a message:
```
$ python3 cowsay/__main__.py 'mooooo moooo'
 ______________
| mooooo moooo |
 --------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
$ python3 cowsay/__main__.py 'hello world'
 _____________
| hello world |
 -------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```
It's a bit cumbersome to always have to type out `python3 cowsay/__main__.py` whenever we want the cow to say something.
So python gives is a tool called `pip` that allows us to *install* packages into an easier-to-use form.
If you run the command
```
$ pip3 install .
```
then this will give your terminal the `cowsay` command:
```
$ cowsay 'moo'
 _____
| moo |
 -----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```
And you can use this command from any folder
```
$ pwd
/home/user/proj/lab-cowsay
$ cd .. # always takes you to the "parent" folder; observe how pwd changes
$ pwd
/home/user/proj
$ cowsay moo
 _____
| moo |
 -----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
$ cd lab-cowsay
$ pwd
/home/user/proj/lab-cowsay
```
In your last lab, you installed the yt-dlp package from github by first cloning and then running the script manually.
It is far more common in the python world to install packages like yt-dlp via pip.
You can install the yt-dlp library with:
```
$ pip3 install yt-dlp
```
Notice that if we put a *package name* after the `pip3 install` command, we do not have to clone it;
pip will do all that work for us automatically.

Now you should be able to run `yt-dlp` whenever you want in your terminal to download fun videos
```
$ yt-dlp
```

> **Fun Aside:**
> Pip stands for "Pip installs packages".
> This is called a *recursive* acronym because the acronym contains itself.
> These recursive acronyms are quite popular in programming.

**Your Task:**

The `command_line` github actions is failing for this repo because the action tries to run the `cowsay` command without first installing it via pip.
Follow the instructions in the `.github/workflows/command_line.yaml` so that the action passes.

## Part 2: PEP8 and flake8

*Python Enhancement Proposals* (PEPs) are the system for adding new features to python.
The most famous PEP is [PEP8](https://peps.python.org/pep-0008/),
which defines best practices for formatting python code.
For example, in python, it is recommended to put spaces around operators.
This the following code
```
x=1+2
```
is considered "ugly" and should be rewritten as
```
x = 1 + 2
```
to conform to PEP8.

It is common for python programmers to run tools called *linters* that enforce PEP8 formatting.

> **NOTE:**
> The name *linter* comes from the idea that clothing with lint on it still serves its purpose, it's just ugly.
> Similarly, python code that is not formatted according to PEP8 still works, it's just ugly.

The most famous linter is called `flake8`.
You can install it with pip by running
```
$ pip3 install flake8
```
Then you can lint the cowsay code with the command
```
$ flake8 cowsay
cowsay/__main__.py:8:19: E201 whitespace after '('
cowsay/__main__.py:8:49: E202 whitespace before ')'
cowsay/__main__.py:9:1: W293 blank line contains whitespace
cowsay/__main__.py:12:23: E225 missing whitespace around operator
cowsay/__main__.py:13:1: W293 blank line contains whitespace
cowsay/__main__.py:14:23: E225 missing whitespace around operator
cowsay/__main__.py:24:1: W293 blank line contains whitespace
cowsay/__main__.py:25:23: E225 missing whitespace around operator
cowsay/__main__.py:26:1: W293 blank line contains whitespace
cowsay/__main__.py:33:1: W293 blank line contains whitespace
cowsay/__main__.py:42:1: W293 blank line contains whitespace
```
Each line of the output shows a violation of PEP8 formatting.

**Your Task:**

The flake8 github action runs this linter and fails if there are any violations of PEP8 style.
To make the test case pass, you will have to modify the file `cowsay/__main__.py` so that `flake8` does not return any linting errors.

## Submission

Create a new repo on github and push your fixed code to the new repo.
Ensure that all github actions badges are green.
Then submit your repo link to canvas.
