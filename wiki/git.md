# Git

As important as any codebase itself, is how the codebase develops over time. _What_ features were added, _who_ added them, _why_ they were added etc. We refer to this process of managing the development of a body of code or project, *version control*. The most popular and widely used version control system is [Git](https://git-scm.com), a snapshot based system. We'll use Git throughout this course, together with GitHub, a hosting service for Git repositories. You will be expected to have a familiarity of the basic Git commands, interaction with Github and actions such as pull requests at the onset of the course.

## Installation

Installing Git is relatively straightforward and can be done with installers. If you run into any issues, or prefer to install Git using a different method as outlined here, see Atlassian's website, [here](https://www.atlassian.com/git/tutorials/install-git)

### MacOS

We're going to use [Homebrew](https://brew.sh) a super helpful package manager to install Git. To check if you already have a version of Homebrew installed, type the following into your terminal

```bash
which brew
```

If you see a version of homebrew installed, you can skip the next step. If you do not however see a version of brew installed, paste the following line of code into your terminal

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Once you hit enter, you'll be notified of what the script will install. Once the process is complete, if you check the version of brew installed, using the line of code from earlier, you should now see the latest version of Homebrew. If you have any issues, refer to the Homebrew [website](https://brew.sh).

Now that Homebrew is installed, to install git we're simply going to run

```bash
brew install git
```

Once executed, you will be able to see the version of git installed, using

```bash
git --version
```

Lastly, you're going to want to change your git username and git email address. This will be the name and contact details that get assigned to every change to make to a code base. To change these, simply run the following code, and use your name and email

```bash
git config --global user.name "Tim Apple"
git config --global user.email "Tim@apple.com"
```

This sets your username globally for every repository on your PC. If you however want a specific username for a specific repo, simply navigate to the directory associated with the repository in your terminal and type

```bash
git config user.name "Tim Cook"
```

### Linux

Git can be installed easily using APT (Advanced Package Tool). From your shell, type

```bash
sudo apt-get update
sudo apt-get install git
```

Once executed, you will be able to see the version of git installed, using

```bash
git --version
```

Lastly, you're going to want to change your git username and git email address. This will be the name and contact details that get assigned to every change to make to a code base. To change these, simply run the following code, and use your name and email

```bash
git config --global user.name "Tim Apple"
git config --global user.email "Tim@apple.com"
```

This sets your username globally for every repository on your PC. If you however want a specific username for a specific repo, simply navigate to the directory associated with the repository in your shell and type

```bash
git config user.name "Tim Cook"
```

### Windows

There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to https://git-scm.com/download/win and the download will start automatically. Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to https://gitforwindows.org/.

#### Git BASH

Git for Windows provides a BASH emulation used to run Git from the command line. *NIX users should feel right at home, as the BASH emulation behaves just like the "git" command in LINUX and UNIX environments.

## Resources

- [Git-It](http://jlord.us/git-it/index.html): A free online tutorial that walks you through all all of the git commands by example

- [Codeacademy](https://www.codecademy.com/learn/learn-git) (paid): in-browser interactive lessons.

- The [official Git docs](https://git-scm.com/doc): one of the best sources for introductory and advanced information, tutorials and external links.

- [Visual explanation of git commands](http://marklodato.github.io/visual-git-guide/index-en.html)

- [Git school visualization](http://git-school.github.io/visualizing-git/): allows you to type git commands in a web browser based terminal and see a visualisation of how the commands affect the structure of the repo.

- [Github Guides](https://guides.github.com)
