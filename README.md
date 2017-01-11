
# Imporve your git skills the cool way

# BASICS

### To make changes:

	git add path/to/file1 path/to/file2
	git commit -m "templates: Changed the XX template to do XX"

### To push that to the central server (which makes it available for deployment):

	git push

### To revert a file to its state in the repository:

	git checkout path/to/file_that_has_changed

### To get the latest code changes:

	git pull --rebase


# REMOTE BRANCHES: YOUR OWN

We use remote tracking branches for branching.

### To create a tracking branch called "ajax_fallback":

	git checkout -b ajax_fallback
	git push -u origin ajax_fallback

### To push changes in this branch:

	git push

	If you get an error, pull the latest files, then try again:

		git pull
		git push

	If, after that, you still get an error for "git push", pull on master, then
	go back to the branch and try again:

		git checkout master
		git pull --rebase

		# Try again.
		git checkout ajax_fallback
		git push

	If, after that, you still get an error and the error message contains
	"[rejected]", then find the branch name next to "[rejected]" and update it.
	Then go back to the branch and try again.

		git checkout branch_that_was_rejected
		git pull

		# Try again.
		git checkout ajax_fallback
		git push

### To pull changes that other people have made to this branch (do not use rebase!):

	git pull

### To pull changes that have been made to master (do not use rebase!):

	git merge master
	git push

	If you get an error for "git push", do a straight "git pull" WITHOUT "--rebase".

		git pull

### To see the full diff of what's changed in this branch:

	git checkout master
	git diff master ajax_fallback

When you're ready to merge the branch back into master:

	# Double check the full diff of what changed.
	git checkout master
	git diff master ajax_fallback

	# Merge it (keep in mind you're still in master).
	git merge ajax_fallback
	git push

	# Delete the local and remote branches.
	git branch -d ajax_fallback
	git push origin :ajax_fallback

### To delete a branch without merging it back into master:

	git checkout master
	git branch -D ajax_fallback
	git push origin :ajax_fallback


# REMOTE BRANCHES: OTHER PEOPLE'S


### To check out the branch somebody else has created:

	git checkout --track origin/ajax_fallback

### To push changes in this branch:

	git push

### To pull changes that other people have made to this branch (do not use rebase!):

	git pull

### To pull changes that have been made to master (do not use rebase!):

	git merge master
	git push

### To see the full diff of what's changed in this branch:

	git checkout master
	git diff master ajax_fallback


# LOCAL BRANCHES

Generally all of our branches are remote, but if you want to create a local one,
a few things are different -- namely to use "git rebase master" when you pull
changes from master.

### To create the branch:

	git checkout -b ajax_fallback

### To pull changes that have been made to master:

	git rebase master


# VIEWING INFO


### To view which branch you're on:

	git status

### To view all branches, including remotes:

	git branch -a

### To view all branches, with information about whether they're tracking/remotes:

	git remote show origin


# USEFUL LINKS


[GitHub Git cheat sheet](http://help.github.com/git-cheat-sheets/)

[Why do we use --rebase when pulling on master?](http://gitready.com/advanced/2009/02/11/pull-with-rebase.html)

[Remotes](http://progit.org/book/ch3-5.html)
