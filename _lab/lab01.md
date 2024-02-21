---
layout: lab
num: lab01
ready: true
desc: "Objective Cars"
assigned: 2024-01-17 9:00:00.00-8
due: 2024-01-24 23:59:00.00-8
---

# Collaboration policy

This lab may be done solo 

# Step by Step Instructions

## Step 1: Getting Ready

Create a repo for this lab in our class organization and clone it to your local machine.

## Step 2: Get the starter code

The starter code is in this repo:

* <https://github.com/{{site.class_org.name}}/STARTER-{{page.num}}>

To get the starter code follow these steps

## Step 2a: Create an emplty lab01 repo on GitHub (no README)

Log into CSIL. Create a directory for all your cs24 code
`mkdir cs24` then change into that directory `cd cs24`

Create an **empty** repo in our {{site.class_org.name}} GitHub org under the name `lab01-YOUR-GITHUB-ID`. Remember not to include a README when you create the repo on GitHub.

Following the steps outlined in a previous lab, please use the SSH address to clone this repo by typing the following on the terminal in CSIL, i.e.

```
git clone git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git
```

After that, you should have a directory under `cs24` called `lab01-YOUR-GITHUB-ID`.   Use the `cd` command to move into this directory:

```
cd lab01-YOUR-GITHUB-ID
```

You may want to practice moving between this directory and the parent directory a few times, and using the `ls` and `pwd` commands to understand what is happening:

```
cd ..
pwd
ls
cd lab01-YOUR-GITHUB-ID
pwd
ls
```

Then, as a reminder, while in your `~/cs24/lab01-YOUR-GITHUB-ID` directory (remember that `~` stands for your home directory), use `ls -a` to see that while the directory 
may appear empty, there is a hidden folder called `.git` that marks this folder as a git repository (or repo for short):

```
$ ls -a
.  ..  .git
$
```

## Step 2b: Create the `main` branch in your repo

Every git repo can have multiple *branches* of code; this is useful on  projects where there are multiple programmers collaborating on a solution.  Multiple branches allow for
different versions of the code to live side-by-side in a repository, and then be merged together at a later stage.

* Courses that involve group work (such as CMPSC 148 and/or CMPSC 156) may cover the use of git with multiple branches.
* However, in this course, to keep things simple, **we'll typically stick to just one branch** 

This single branch is sometimes called the *default branch*.
* Prior to October 1, 2020, the usual name for that branch was `master`.
* Starting October 1, 2020, GitHub started calling the default branch `main`

Not all `git` software is updated with this convention however.  Accordingly, when we clone a new repo, to align our local repo with GitHub,
our first step is to set the current branch to `main`, with this command (please type this now in your `~/cs24/lab01-YOUR-GITHUB-ID` directory:)

```
git checkout -b main
```

The `git checkout` command is the one that is used to switch from one branch to another, and the `-b` command says that we are creating a new
branch in our local repo.

For the time being, and probably throughout CS16, this is likely everything you need to know about branches (at least for the purposes of this course.)

Now we are ready to pull in some starter code.

## Step 2c: Add a remote for starter code.

While in your `~/cs24/lab01-YOUR-GITHUB-ID` directory, type this command:

```
git remote -v
```

The `-v` here stands for `verbose`, and it means that the command will give lots of helpful information. The output should look like this:

```
$ git remote -v
origin	git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git (fetch)
origin	git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git (push)
$ 
```

Explanation:
* The word *remote* refers here to a Git repo that lives on some other computer; in this case, a GitHub.com server. 
* The output above shows that you have one *remote* called `origin` and it shows the URL associated with that name `origin`.  
* By convention, the name `origin` is used for the GitHub repo from which you cloned the current repo, i.e. the one that came after `git clone` in a previous step.

What we are doing to do next is add a second remote, called `starter`.  From this remote, you'll be able to pull in some starter code; your lab solution will involve
working with some of that starter code.

The starter code lives in this repo, which you can visit in a web browser to look at the starter code:
* <https://github.com/{{site.class_org.name}}/STARTER-lab01>

To add a remote for this repo, we'll use the ssh url, like this:

```
git remote add starter git@github.com:{{site.class_org.name}}/STARTER-lab01.git
```

To see if it worked, you can type the `git remote -v` command again. Output should look like this (with YOUR-GITHUB-ID replaced by your github id. 

```
$ git remote -v
origin	git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git (fetch)
origin	git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git (push)
starter	git@github.com:{{site.class_org.name}}/STARTER-lab01.git (fetch)
starter	git@github.com:{{site.class_org.name}}/STARTER-lab01.git (push)
$ 
```

Note that if the URLs are wrong for either the `origin` or the `starter` remotes, you can fix that by doing this command to remove a remote:
* `git remote remove origin` to remove the remote `origin`
* `git remote remove starter` to remove the remote `starter`

Then you can add the remote back with the correct URL, e.g.:
* `git remote add origin git@github.com:{{site.class_org.name}}/lab01-YOUR-GITHUB-ID.git`
* `git remote add starter git@github.com:{{site.class_org.name}}/STARTER-lab01.git`

This can be used, for example, if you accidently cloned the repo using the `https` url instead of the one that starts with `git@github.com` (which is the SSH based URL).

Assuming your remote for `starter` is now set up correctly, the next step is to pull in the starter code.

## Step 2d: Pull in Starter Code

To pull in the starter code, use:

```
git pull starter main
```

Then use an `ls` command, and you should see new files in your directory.  That should look something like this:

```
$ ls
$ git pull starter main
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 10 (delta 2), reused 7 (delta 2), pack-reused 0
Unpacking objects: 100% (10/10), 2.45 KiB | 47.00 KiB/s, done.
From github.com:{{site.github_url}}/STARTER-lab03
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> starter/main
$ls
car.cpp  car.hpp  doors.hpp  perf.cpp  perf.hpp
```

## Step 2e: Push the initial code to the main branch of the origin remote

To push the code to the main branch of your original remote (origin) type the command

```
$ git push origin main
```
This will sync up the commit history and files from your local repo with the main branch of the origin remote (which exists on github.com)

You should see the following message:
```
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (10/10), 3.90 KiB | 1.95 MiB/s, done.
Total 10 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To github.com:ucsb-cs16-f22/llab03-YOUR-GITHUB-ID.git
 * [new branch]      main -> main
[dimirza@csilvm-11 lab03_test]$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

With these files in place, you are ready to start coding. 

If you don't see those files, go back through the instructions and make sure you didn't miss a step. From here on after you complete each part of the assignment you should add, commit and push your changes to origin main. For instructions on how to do this, scroll down and read the section on "Commit your code to GitHub". If you still have trouble, ask your TA/ULAs for assistance.

## Step 2: Understand the Code and finish car.cpp 

In this lab you will create a comprehensive `Car` class with
* descriptive member variables, 
* constructor, 
* copy constructor, 
* destructor, 
* overloaded assignment operators, and
* commonly used methods that manipulate member variables

The definition of the `Car` class will be provided to you in the header file `car.hpp`. The member variables listed below are all private:
```
char*  manufacturer;
char*  model;
uint32_t  zeroToSixtyNs;
float  headonDragCoeff;
uint16_t  horsepower;
DoorKind  backseatDoors;
uint8_t  seatCount;
```

The functionalities of these variables can easily be inferred from their names. The `manufacturer` and `model` are of the type `string`, e.g. `manufacturer = "Audi\0"` and `model = "R8\0"`, which shall be dynamically managed. `zeroToSixtyNs` is the time taken to accelerate from 0 to 60 mph. There are also `headonDragCoeff`, `horsepower`, and `seatCount`. The `backseatDoors` is an enumeration whose declaration is in `doors.hpp`. It can take one of the four values: 
1. `None = 0`, 
2. `Hinge = 1`, 
3. `GullWing = 2`, 
4. `Sliding = 3`

The descriptions of the functionalities of the public methods are listed below:

* `Car()`
	* Default constructor. Initialize the pointer type variables with `NULL` and the numerical variables with `0`. `DoorKind` variable is also initialized with `None`.
* `Car(char const* const manufacturerName, char const* const modelName, PerformanceStats perf, uint8_t numSeats, DoorKind backseatDoorDesign)`
	* Constructor. Initialize the member variables with specific values.
* `Car(Car const& o)`
	* Copy constructor. Initialize the member variables with the values in `o`.
* `~Car()`
	* Destructor. Recycle the memory of variables.
* `Car& operator=(Car const& o)`
	* Overloaded assignment operator `=`. Set the values of the variables in the current object to be those in `o`.
* `char const* getManufacturer() const`
	* Get the string of `manufacturer`.
* `char const* getModel() const`
	* Get the string of `model`.
* `PerformanceStats getStats() const`
	* `PerformanceStats` is a structure given to you in the head file `perf.hpp`. It summarizes the three parameters `horsepower`, `zeroToSixtyNs`, and `headonDragCoeff` together. This method gets their values and returns as the structure.
* `uint8_t getSeatCount() const`
	* Get the number of seats in `seatCount`.
* `DoorKind getBackseatDoors() const`
	* Get the type of the doors in `backseatDoors`.
* `void manufacturerChange(char const* const newManufacturer)`
	* Change the name (string) in `manufacturer` to the new in `newManufacturer`. Since the name is of the type string in the memory, please care about the memory management and avoid the memory leak.
* `void modelNameChange(char const* const newModelName)`
	* Change the name (also string) in `model` to the new in `newModelName`.
* `void reevaluateStats(PerformanceStats newStats)`
	* Update the values of `zeroToSixtyNs`, `headonDragCoeff` and `horsepower` by using the new parameters in `newStats`.
* `void recountSeats(uint8_t newSeatCount)`
	* Set the value of `seatCount` to be `newSeatCount`.
* `void reexamineDoors(DoorKind newDoorKind)`
	* Set the kind of the doors in `backseatDoors` to be `newDoorKind`.


## Step 3: Test Your Code and Upload to Gradescope

The Autograder will use some test cases to check if your implementations are correct. In order to verify them, you’ll need to write your own test code, which can be a ‘main’ function to print out the results, before the submission. Then, write a Makefile to link all dependencies to make and run your test. 
The lab assignment “{{page.num}}” should appear in your Gradescope dashboard in CS 24. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. For this lab, you will only need to upload your modified file (i.e. `car.cpp`). 
If you already submitted something on Gradescope, it will take you to their “Autograder Results” page. There is a “Resubmit” button on the bottom right that will allow you to update the files for your submission.
For this lab, if everything is correct, you’ll see a successful submission passing all of the Autograder tests.

**Remember to check if you can see the files uploaded correctly in Gradescope.**

