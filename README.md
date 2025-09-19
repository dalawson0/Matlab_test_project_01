# Github Matlab Project Submission

Here we summarize the steps involved in making a Matlab project available on File Exchange via Github

## Prerequisites

1) Please sign up or log into your Github account.

2) Download the package manager [Homebrew](https://brew.sh/) if you don't already have it installed.

3) Download [git](https://git-scm.com/downloads) for your local computer.

## Set up

Once you have git locally and an remote Github account you are now able to start creating your project.

Create a new directory in the desired location on your local computer via

```bash
cd /path/to/desired/location
```

An example for macbook we would use the terminal whereas in Windows you would use the powershell.

Mac:

```bash
cd /Users/johndoe/Documents/
```
Windows:

```bash
CD C:\Users\JohnDoe\Documents\
```
Next, create a parent directory for the project with an appropriate name. This can be done with the function "mkdir"

```bash
mkdir Matlab_Project
```

Then you can add in anticipated child directories and/or populate the directory with project data.

```bash
mkdir ./tests ./examples ./images ./data
```

## Creating a local repository

Now you are ready to make your project directory a local repository using git create a "git".

To do this we navigate to be inside the parent directory of the project using the "cd" command in either powershell or terminal, then we run the following command in.

```bash
git init
```

Then do remote gihub stuff

Then back to terminal to set up SSH

then back to github (remote) 

then connect the two 

then confirm things by visiing the Gitbub remote repository page

then go to MATLAB file exchange page then back to Github and then you're like done.
