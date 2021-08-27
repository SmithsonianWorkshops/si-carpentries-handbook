# Creating a Workshop Website

## Creating a Repository from the Carpentries Template

1. Log into GitHub, and go to [https://github.com/carpentries/workshop-template#creating-a-repository](https://github.com/carpentries/workshop-template#creating-a-repository). Follow the steps under "Creating a Repository" so that your screen looks like this (with different Name). Fill in "Workshop website for {dates} {workshop type}" for the Description. Contact Mike Trizna if you do not have access to the "SmithsonianWorkshops" organization.
	![](images/creating_repo.png)
1. Test out the URL (of form *https://smithsonianworkshops.github.io/**[repo name]***), and add it to the Repo description.
	![](images/repo_website.png)

## Updating workshop-specific info

1. Fill in workshop details in `_config.yml` and `index.md`

1. Modify workshop-specific resources in `_includes/`

	1. `intro.html`: 
	1. `who.html`:
	1. `setup.html`:
	1. `syllabus.html`:
	1. `schedule.html`:

## Optional: Making an empty Main Branch

By default, when a user goes to the GitHub repository for the workshop, they will be confused by seeing confusing instructions about building a website. We can move all of these supporting files away from view, and have a fresh space to store workshop-related files such as Jupyter/R Notebooks, EtherPad exports, etc.

### Using GitHub GUI


### Using command line interface

1. If you have not already done so, clone the workshop repository to your computer and change directories into the workshop repo directory. (For illustration purposes, the fictional `2021-08-20-smithsonian` repository is used here. Replace this repo name with your workshop repo name.)

    ~~~
    git clone https://github.com/SmithsonianWorkshops/2021-08-20-smithsonian.git
    cd 2021-08-20-smithsonian
    ~~~

2. Check the existing branches. There should be only one branch, `gh-pages`, where the course website files are located.

	~~~
	git branch
	~~~
	
3. Create and switch to a new local branch, `main`. (The `--orphan` option allows for cleaner history tracking for the new branch.)

	~~~
	git checkout --orphan main
	~~~
	
4. Remove all existing files on this new branch. (Double check that you're in the workshop repo and on the `main` branch before you run this command!)

	~~~
	git branch
	git rm -rf .
	~~~
	
5. If you check the directory, you will see that it is now empty. If you switch back to the `gh-pages` branch, you should see all the course website files reappear.

	~~~
	git checkout gh-pages
	~~~
	
6. Switch back to `main`. Then add a `README.md` file using nano or the text editor of your choice. Stage and commit this README file.

	~~~
	git checkout main
	nano README.md
	git add README.md
	git commit -m "Create main branch and add README"
	~~~
	
	You can also add any additional files you would like to make available to students. (e.g. Jupyter Notebooks, R Notebooks, SQL files, etc.)
	
7. Push the new `main` branch to the workshop GitHub repository. Since `main` currently exists only as a local branch, you will need to specify a new remote origin.

	~~~
	git push -u origin main
	~~~

8. Go to the workshop repository on GitHub. Go to Settings > Pages and confirm that the Source for the course website is currently listed as `gh-pages`.

9. Go to Settings > Branches. Under Default branch, click the icon to **Switch to another branch**. Choose `main`, and click Update. You will see a warning message about unintended consequences of changing the default branch. Click the *I understand, update the default branch* button.

10. Confirm that the workshop repository is defaulting to the new `main` branch and that the course website is still showing up properly.

## Optional: Setting up a local jekyll environment
