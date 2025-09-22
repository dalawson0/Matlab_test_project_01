# MATLAB File Exchange Integration with GitHub

Here we summarize the steps involved in making a Matlab project available on File Exchange via Github

### Table of Contents
1. [Prerequisites](#Prerequisites)
2. [Project Setup](#Project-Setup)
3. [Creating a Local Repository](#Create-Local-git-Repository)
4. [Setting up SSH key](#Set-up-SSH-key)
5. [Connecting git and GitHub Repositories](#Connecting-git-to-GitHub-repository)
6. [Utilizing Local and Remote Repos](#Using-both-the-local-and-remote-repositories)
7. [Connecting MATLAB to GitHub](#How-to-Link-a-GitHub-Repository-to-MATLAB-File-Exchange)
8. [Important Notes](#Important-Notes)

## Prerequisites

1) Please sign up or have your [GitHub account](https://github.com/).

2) Download the package manager [Homebrew](https://brew.sh/) if you don't already have it installed.

3) Download [git](https://git-scm.com/downloads) for your local computer.

4) Please sign up or have your [MathWorks account](https://login.mathworks.com/embedded-login/signin.html?cid=mktg&wid=gnav&uri=https%3A%2F%2Fwww.mathworks.com%2Fmatlabcentral%2Ffileexchange%2F).

## Project Setup

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

## Create Local git Repository

Now you are ready to make your project directory a local repository using git create a "git".

To do this we navigate to be inside the parent directory of the project using the "cd" command in either powershell or terminal, then we run the following command in.

```bash
git init
```

We then establish our first commit to the local repository to store the current state of the parent directory i.e. the 4 child directories we have created earlier.

Since we will store all the files/folders in our parent directory we will use the period operator '.' to indicate that all items in this current directory should be be 'staged' or stored in a intermediate location.

```bash 
git add .
```

Since we indeed want to store this files and save this as the initial state of our project we will use the "commit" command. In addition we will use the flag "-m" to attached a string containing a short description about the commit.

```bash
git commit -m "Initial Commit"
```

## Set up SSH key

before we move onto Github on our browsers let us create a SSH key that enables us to make authenticated and  protected API calls to GitHub's servers that store our remote repository that we will set up in the next section. 

So in termnial run the following command to create a new SSH key, thereby assuming you don't have a SSH key.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

where "your_email@example.com" should be the email you used to make your Github account. 

Next, add your key to the SSH agant by running each of the following lines separately.

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Awesome! Now its time to add your public key to GitHub by copying the content of the  ".pub" file:

```bash
cat ~/.ssh/id_ed25519.pub
```

Next, we have to go to **GitHub → Settings → SSH and GPG keys → New Keys** and paste in our public key via "CTRL+v" or "CMD+v"

Let's confirm that we set up the connection right but running the following line of code in our terminal:

```bash
ssh -T git@github.com
```

If "Hi YourUserName! You've succesffuly authenticated...", then you have successfully set up you SSH key and shared the proper one with your GitHub account. 

## Creating a remote GitHub repository

After all this work we are finally ready to create a remote repo! To do this navigate to [GitHub](https://github.com) and sign in if you aren't already.

On the left hand side you should see a green button titled "New". Click it!

**WARNING:** When you are providing metadata on your repository and specifying initial configurations be sure that "Add README", "Add .gitignore", and "Add license" are turned to "off" if and only if you have set up a README.md, lisence, and .gitignore file in your parent project directory already!
 
Since we have not set any of these up we can enable all of them for you repository!

After clicking the button **"Create repository"** we have successfully create a remote repo that we can now link to our local git repository. 

## Connecting git to GitHub repository

To connect the two repositories we first go to GitHub and underneath where it says **"Quick setup ..."** click on the SSH button and copy that text!

We then go to the terminal and run the following commands to push an existing repository to GitHub:

```bash
git remote add origin git@github.com:YourUser/YourRepo.git
```
```bash
branch -M main
```
```bash
git push -u origin main
```

Awesome sauce! Now to confirm that you have completed this process successfully, you should reload the GitHub page and should see the 4 folders we created populated!

## Using both the local and remote repositories

Now upon making changes to your local repo, and wish to make them available to your remote repo, you should:
1. Stage the change 
2. Commit the change to local repo
3. Push the local change to the remote repo via 

```bash
git push origin main
```

Alternatively, if you decide to make changes to the remote repo, and wish to have them locally, you should:
1. Pull the remote changes to the local repo in command line via

```bash
git pull origin main
```

## How to Link a GitHub Repository to MATLAB File Exchange

To be able to use you new GitHub repository with MATLAB file exchange we use the "MATLAB and Simulink Integration for GitHub" tool that has been added to GitHub.

1. Navigate [here](https://www.mathworks.com/matlabcentral/fileexchange/my-file-exchange/github-app-installation-guide) to learn how to connect GitHub to MATLAB and Simulink, or to jump right in click [here](https://github.com/apps/matlab-and-simulink-integration/installations/select_target?state=ZmlsZWV4Y2hhbmdl).
2. When prompted, choose **Select repositories** and add this repository. 
   (Recommended: don’t give access to “all repos” unless you want all of them visible.)
3. Go to your [MATLAB File Exchange account](https://www.mathworks.com/matlabcentral/fileexchange/) → Publish page to confirm that MATLAB File Exchange will display your repository and allow you
   to publish versions automatically from GitHub.

## Important Notes

- **Private repositories**:  
  If this repo is set to *Private*, File Exchange will show it grayed out and
  you will not be able to publish it.  
  To publish, you must change the GitHub repo visibility to **Public**:
  - Go to your repo on GitHub → **Settings → General → Danger Zone**  
    → Change visibility → **Make public**.

- **Versioning / Releases** (recommended):  
  Use [GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)  
  to tag stable versions of your code. File Exchange can mirror those releases,
  making it easier for others to download and use consistent snapshots.

## Quick Tips
- Keep your repository public if you intend to share it on File Exchange.

# For Help
email: da.lawson0@gmail.com
