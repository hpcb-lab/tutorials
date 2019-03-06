Git and GitHub for Bioinformatics
--------------------------------------
Eric T Dawson

## Background
Git is a powerful to for version control that was developed by Linus Torvalds,
who also developed Linux. We're going to talk about how we can use git to
make our analyses more reproducible, but first we need a little background.

So what is "version control?" Version control is a system of organizing our
code, analysis, and data that tracks how it changes through time. Imagine
you're typing an essay for a class. You might write a few hundred words and 
save it under a file named "My\_essay.version2.doc." You might write a few hundred more
words then go back and edit what you'd written initially, saving your progress
to a file called "My\_essay.version2.doc." Now imagine you continue this process,
writing, editing, and saving; you might even save concurrent versions with different
wording of the same sentence with names like "My\_essay.version2.1.doc." At the end of
this process, you'll have a set of files which hold not just your final product but the
history, changes, and alternative paths you took along the way. If you used the "Track Changes"
feature in Microsoft Word, you'll have a change-for-change history. You might decide in the end
to pull from several of your previous and alternate versions to generate the essay you submit.

The rather-lengthy essay analogy above is a type of version control. For code, there are many
programs for version control, but Git has become the dominant one due to its relative ease of use.
For the historically curious, you might look into subversion or mercury, though a discussion of them
is outside the scope of this tutorial.

## Why use Git
In short, Git allows us to maintain a clean directory of code that still maintains our history and changes.
This makes our analyses more reproducible and saves us time if we need to go back to older code for some
reason. Combined with GitHub, we can easily share and archive our code so that others can use it and we
can have a permanent copy we can access from all of our computers.

## Setup and Installation
As part of the standard Unix toolchain, Git is often install by default. If not, it's usually easy to find
in the standard repositories:  

```
# on debian/Ubuntu/Linux Mint
sudo apt-get update && sudo apt-get install git

# on Mac OS X:
sudo port install git

# or, if you don't have sudo on Mac and do package management with Brew:
brew install git

```


## Step 1: Creating a Git repository
The first step in a Git version control workflow is to create a repository, a directory in which
our version-controlled files will exist. First, we'll need to make a directory that will
contain our code:  
```

mkdir my_git_project

```

This is just a normal Linux directory, which you might remember from basic Unix tutorials. Now we'll
make it a Git repository by "initializing" a repo in that directory:
```

cd my_git_project
git init

```

This will print a message to the terminal that says something like `Initialized empty Git repository in /Users/dawsonet/my_git_project/.git/`.
We've just made our first git repository. You won't see anything in the repo, but Git has created a small hidden directory. We can see it
with `ls -a`:
```
ls -a

```
There's now a hidden directory called .git that will hold the files Git uses to track our changes.

## Step 2: Making changes
Let's make a few files to show how we add and remove files from Git. First, let's make a file that we want to add to version control:  
```
echo "This is a file to add" > add_me.txt
```

We can tell Git to track this file using the `add` command, like so:
```
git add add_me.txt
```

Our file is now tracked with Git! Before we 
