---
source: Rmd  
title: "Good Practices for Managing Projects in RStudio"  
teaching: FIXME
exercises: FIXME
questions:
- What are good research project management practices?
- What is an R Project file?
- How do you start a new or open an existing R Project?
- How do you use version control to keep track of your work?

objectives:
- Best pratices for working on research projects involving data
- The purpose of using .Rproj files
- Using version control in RStudio
- Starting or continuing an R project

keypoints:
- keypoint #1. Specific concept or syntax learned in this episode
- keypoint #2. Specific concept or syntax learned in this episode
---



## Managing Research Projects in R
Now that we’ve learned some of the basics of authoring in RStudio with 
R Markdown documents, let’s take a step back and talk about research project 
management as a whole. 

The ability to integrate code and narratives is a major advantage of the RStudio 
environment, especially considering the scientific process is naturally 
incremental, and many projects start life as random notes, some code, then a 
manuscript, and eventually everything ends up a bit mixed together. To 
complicate things further, we are often working with other collaborators, lab 
members, graduate students, faculty from the same or different institutions, 
which makes it that much more difficult to keep projects organized. When you 
throw data into the mix (sometimes huge amounts of it!), it’s integral to use 
best practices to maintain the integrity of your analysis and to be able to 
publish high quality and reproducible research. Using Rmarkdown is a powerful 
tool, but it can’t be fully utilized unless your project documents, scripts and 
other files are well-organized. So let’s take a look at RStudio’s features to 
manage projects and discuss some of the best practices when working with data 
and collaborators. 

## Research Project Stress Points
We often have organizational or logistical stress points in our research that 
may become breaking points, especially when it comes to working with 
collaborators, returning to a project after a hiatus, or dealing with data and 
scripts. Let’s discuss three of those common stress points:

- **File/folder disorganization**
  - you cannot find your files on your computer (or your cloud storage)
  - Multiple versions of files with names such as "finaldraft_4.txt"
  - Path issues when trying to run code 
  - Reviewers or colleagues cannot re-run your code/analyses
- **Storage and sharing issues**
  - Files are only saved to your computer and are vulnerable (or have already 
  succumbed to computer/hard drive failure
  - When working with collaborators, they (or you) don’t share the files needed
  - Files are shared via email attachments
  - Difficult to know if you have the latest version of documents
- **Losing track of project status**
  - You cannot remember where you are in a project after being away for an 
  extended period (or what you worked on the previous day...no judgement)
  - You aren’t sure what you should be working on next
  - You have various to-do notes spread across your office or home 
  (or never write them down in the first place)

> ## Discussion
> To what extent do these stress points affect your research projects? Are there
> additional issues that you’ve encountered that slow down or derail your work 
> due to issues with project management?
{: .challenge}

> ## Discussion: Antidotes
> What are some practices you implement to keep yourself on track with your 
> projects?
{: .challenge}

## Antidotes

A good project layout will ultimately make your life easier:
- It will help ensure the integrity of your data
- It makes it simpler to share your code with someone else (a lab-mate, 
collaborator, advisor etc.)
- It allows you to easily upload your code with your manuscript submission
- It makes it easier to pick the project back up after a break.
- It makes your research reproducible!

We’ll discuss three aspects of project management and then implement those 
practices for the remainder of this workshop in the RStudio environment.

1. File/ Folder Organization
2. Storage & Sharing
3. Using Version Control

Then, we’ll get started on our project!

## Project File/Folder Organization
### Important principles:  

Although there is no “best” way to lay out a project, there are some general 
principles to adhere to that will make project management easier:  

#### **Practice good file-naming practices**  
The three principles of file-naming are: 

1) Machine-readable
- friendly for searching (using regular expressions/globbing)
    - no spaces, punctions, accented characters, or case-senstitive file names
- friendly for computing
  - deliberate use of delimiters (i.e. for splitting file names)
  
2) Human-readable
- Name contains brief description of contents
- borrow from Clean URL practices
  - "slug" i.e. the part of a url that is human readable `data-analyses-fig1` 
  
3) Plays nice with default ordering  
adapted from https://datacarpentry.org/rr-organization1/01-file-naming/index.html 

#### **Practice good file-organization practices**  

[Good Enough Practices for Scientific Computing](http://swcarpentry.github.io/good-enough-practices-in-scientific-computing/) gives the following recommendations for project organization:  
1. Put each project in its own directory, which is named after the project.
2. Put text documents associated with the project in the doc directory.
3. Put raw data and metadata in the data directory, and files generated during cleanup and analysis in a results directory.
4. Put source for the project’s scripts and programs in the src directory, and programs brought in from elsewhere or compiled locally in the bin directory.
5. Name all files to reflect their content or function.
6. Additionally, we'd recommend to include README, LICENSE, and CITATION files! 

#### **Use relative paths**  
This goes hand-in-hand with keeping your project within one “root” directory. If you use complete paths to say, read in your data to RStudio and then share your code with a collaborator, they won’t be able to run it because the complete path you used is unique to your system and they will receive an error that the file is not found. That is why one should always use relative paths to link to other files in the project. I.e. “where is my data file in relation to the script I’m reading the data into?” The practice of using relative paths is made easier by having a logical directory set up and keeping all project files within one root project folder. 

FIXME add brief review of relative paths vs complete paths

#### **Treat data as read only**  
This is probably the most important goal of setting up a project. Data is typically time consuming and/or expensive to collect. Working with them interactively (e.g., in Excel or R) where they can be modified means you are never sure of where the data came from, or how it has been modified since collection. It is therefore a good idea to treat your data as “read-only”. However, in many cases your data will be “dirty”: it will need significant preprocessing to get into a format R (or any other programming language) will find useful. Storing these scripts in a separate folder, and creating a second “read-only” data folder to hold the “cleaned” data sets can prevent confusion between the two sets. You should have separate folders for each: raw data, code, and output data/analyses. You wouldn’t mix your clean laundry with your dirty laundry, right?  

#### **Treat generated output as disposable**
Anything generated by your scripts should be treated as disposable: it should all be able to be regenerated from your scripts.
There are lots of different ways to manage this output. Having an output folder with different sub-directories for each separate analysis makes it easier later. Since many analyses are exploratory and don’t end up being used in the final project, and some of the analyses get shared between projects.  

#### **Include a README file**  
FIXME With project details such as?  

We also recommend adding a citation and license file. A citation file which simply contains citation text to make it clear to those who reference your work how you want it to be cited, and a license file for code reuse - see license types on Github. See the project files for an example. 

For our project we’re working in today, we used the following setup for folders and files:

- **code:** contains the scripts that generate the plots and analysis (found in `output/plots`)  
    - **/functions:** contains custom functions written for the data pre-processing  
- **data:** this folder contains the raw and cleaned data files  
    - **/foodchoice_data:** contains the individual data files from food choice trials  
- **output:**
	- **/data:** contains the output data file after applying custom pre-processing function  
	- **/plots:** contains pdfs of the plots generated from the plot scripts in the code folder  
- **report:** All files needed for the publication of the research project  
	- **/source:** .Rmd file for the paper and additional files needed for rendering the paper  
      - **/fig:** contains the images created specifically (not through the analysis scripts) for the paper  
	- **/output:** contains the final html output of the Rmd paper  
- **R-repro-pub.Rproj:** R project file that lives in the root directory.  
- **README.md:** A detailed project description with all collaborators listed.
- **CITATION.md:** Directions to cite the project.
- **LICENSE.md:** Instructions on how the project or any components can be reused.  

Again, there are no hard and fast rules here, but remember, it is important at least to keep your raw data files separate and to make sure they don’t get overridden after you use a script to clean your data. It’s also very helpful to keep the different files generated by your analysis organized in a folder.

*what’s this .Rproj file? We’ll explain in a bit.


### Storage and Sharing

#### Backup your work

Having a solid backup plan in case of emergencies (say your hard drive on your computer fails) is essential. The general guideline for back ups is to adhere to the [3-2-1 principal](https://www.uschamber.com/co/run/technology/3-2-1-backup-rule ) which dictates that you should have 3 copies, on 2 different media, with 1 copy offsite. Your decision on backups will be based on your own personal tolerance but we recommend at minimum to avoid only having a copy of your project on your personal, work computer or a lab computer at all costs. At the very least, you should backup your project into cloud storage (either provided by your university or paid for yourself). Common cloud storage platforms include Google drive, Box, OneDrive, Dropbox, etc. Backing up a project on a local device to cloud storage allows you to meet two of the 3-2-1 criteria (2 different media and 1 offsite). If you're working with at least one collaborator and they also keep an up-to-date copy of the project on their computer, you're set!

#### Version Control hosting services 

If your research project involves code, the best way to make sure you have your work backed up AND keep track of your code and data is to use a version control hosting service such as GitHub - though we'd recommend using version control for any large projects. 

The main three version control hosting services are GitHub, GitLab, and BitBucket, to see a comparison of the available options, see: https://www.linkedin.com/pulse/demystifying-git-vs-github-atlassian-bitbucket-gitlab-pawan-verma?trk=read_related_article-card_title. 

We will proceed using GitHub because it is the most used version control platform to date. 

### Using Version Control

Ok, now let’s talk about implementing version control in your project through RStudio! But first… let's quickly clarify the difference between Git and GitHub. We already said that GitHub is the version control hosting platform. Git is the version control system and does not **have** to be used with GitHub. You can use Git and then host your code on Bitbucket for example, or save to your Google drive. In fact, you can use Git on your local system only and never save it to a cloud storage platform. However, version control hosting platforms such as GitHub enhance the benefits of version control and offer incredible collaboration features. The difference between the two can be a bit confusing because they are so often used together, but the more you use them the more it will make sense. Soon enough you'll be wondering how you even completed a code project without version control.

#### So how does version control work?
first, you have to have a directory or folder that becomes your git "repository". That is, the directory (folder) that contains all your project files you want to track with version control. (you can start to see, that good file organization becomes *necessary* rather than option at this point). Within that folder there is a git file that tracks the versions of each of your saves which makes it possible for you to return or consult an older version if necessary (you won't be able to see this file it's a [hidden file](https://en.wikipedia.org/wiki/Hidden_file_and_hidden_directory)). Along with the file that tracks those changes, Git is compromised of syntax which allows you to save, change, and interact with different versions of your project files. Simple at it's most basic, but there are many many more complex options for you to dig into Git (if you so choose - we'll keep it simple to start).  

There are actually many ways to use Git, you could use it on GitHub only (though that suffers from lack of options and is a bit clunky), there is a Desktop interface, many serious programmers use it on command line. HOWEVER, RStudio has Git controls built in so we'll use it there - all in one place!

Before we use Git in RStudio project, we must have an .RProj file so let's talk about R Projects.

Who has used R Projects before?


#### Working in R Projects

One of the most powerful and useful aspects of RStudio is its project management functionality. We’ll be using an R project today to complement our R Markdown document and bundle all the files needed for our paper into one self-contained, reproducible bundle. An `.Rproj` file makes it keep your R scripts, data and other files altogether - just navigate through your file system to get to your project directory and double click on the .Rproj file. The added benefit is that the .RProj file will automatically open RStudio and start your R session in the same directory as the `.Rproj` file and remember exactly where you left off. .RProj files are powerful ways to stay organized on their own, but they also unlock the additional benefit of being able to use Git within RStudio. 

> ## Tip: R Project in “root” folder
> `.Rproj` files must be in the root directory of your project folder/directory. What is the root directory again (look back at the relative paths intro)?  
{: .callout}


### Using R projects and version control in RStudio
There are several options for working with R projects in RStudio
FIXME add add screen shot. 

To start an R project, you would navigate to `File > new project` rather than just `File > new file`. 
1. Starting a new project (with version control)
![Add image starting new R project project type screen]()

To get the added benefit of a Git version controlled project follow:
![Add image create new project version control checked]()

2. If you've already started an R project WITHOUT version control, you have the option to add version control retrospectively. You can also add existing R files to a project and version control if you've done neither. We won't go over that here, but to see an example please see episode from x lesson here: FIXME add link

3. Continue a version-controlled project
The final option is to continue a version controlled project. This is the option we will do.
![Add image new project version control option]()
![Add image import project from Git]()

But first, we need to navigate to GitHub and make a copy of the project for this workshop -> FIXME add instructions. 


Woo hoo! We have the project we are collaborating on for this workshop open in a new RStudio session!

Let’s take a second to pause and look at our materials in the folders to acquaint ourselves with them.
Now, how to use version control. 

### Using version control

The simple workflow for version control is:   
Pull > add > commit > push

But what do those words even mean?


Pull: definition  
add: definition
Commit: definition  
Push: definition  

- You should pull each time you start working on your project after a hiatus, or before each edit if you know a team member is working at the same time. 
- Commit frequently, each commit should be a distinct set of edits which you can summarize in 50 characters or less. Don’t add a bunch of unrelated edits to the same commit, it makes it harder to look back through your “snapshots” and find the right one if you need to. 
- At the end of your work session (or more frequently if you are working at the same time as team members), “push” your commits to the remote repository - this is the only way your local changes get added to your team’s remote repository.

This pull, add, commit, push routine will become second nature. Pulling at the beginning and pushing at the end of your work session becomes a sort of ritual that marks the beginning and end of your work session. 

Show how to commit

> ## Tip: add files that don’t need to be tracked to the .gitignore
> Such as data files, outputs, references (you want to save those, but you 
> aren’t actively making changes to them so we don’t need to “track” them through 
> version control. Mostly scripts and rmd files need tracking
{: .callout}

> ## Challenge: (optional) Add the following files to the .gitignore 
>
{: .challenge}

### Your first edit

Demonstrate an edit

> ## Challenge: Find the FIXMEs and add the Markdown formatting indicated. 
>
{: .challenge}

Make a commit when you’re done with a message that is descriptive of the edits made. 
