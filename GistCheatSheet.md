## Git Cheat Sheet
* To install git
	**$ sudo apt-get install git**
* Getting a git repo
	**$ git clone https://github.com/abc/abc..**
* Creating a repo
	*  **Make a project folder on GitHub and copy the link**
	*  **$ git init**
	*  **$ git remote add <project folder url>**
	*  **$ git add .**
* Checking a status
	**$ git status**
* Commiting the repo on stage
	**$ git commit -m "My Commit"**
* Pushing your local project folder on GitHub server 
	**$ git push original master**
* Logs of your previous commit (history)
	**$ git log**
* Removing a file from stage (tracked files)
	**$ git rm <file name or path>**
* To see the difference which one yet staged
	**$ git diff**
* To see the difference which are staged
	**$ git diff --staged**
* Creating a new branch
	**$ git branch <branch name>**
* Swithching between branches
	**$ git checkout <branch name>**

	Note: *  Default branch->**"Master"**
	      *  Branch is _**"movable pointer to the commits"**_

* To check on which branch we are currently working
	**$ git branch**
	(This will show all the branches and the active branch with a pointer **(*)**)
* To merge a branch with master
	**$ git merge <branch name>**
* Deleting a branch
	**$ git branch -d <branch name>**
* While merging _a branch with master_ it should have a direct ancestor. If not, git will doing three way merge.
	**c0 <- c1 <- c2 <- c4**
		     **^**
		     **|**
		     **c3 <- c5**					
	Here c2 is **common**,c4 is **master** and c5 is **branch1**. And hence c2 will be **common ancestor**.
* Using **c2**(common ancestor), **c4**(master pointer) & **c5**(branch1 pointer).
	*  **Then git creates a *new snapshot* having result of above three snaps**.
	 **c0 <- c1 <- c2 <- c4 <- c6**
		     **^	  **|**
		     **|	  **|**
		     **c3 <- c5 <--`**
	Here c6 is **master**.
* To see the last commits on each branch
	**$ git branch -v**
* To see which branches are already merged you are on:
	**$ git branch --merge**
* To see which branches are not merged yet:
	**$ git branch --no-merge**
* **$ git fetch origin**
	Updates your _local database_ looking upon the server origin (basically the changes that you don't have yet).
* Other than merging we can use **"rebase"**
	**$ git rebase . master**

	**c0 <- c1 <- c2 <- c3**				
		     **^**		  **rebase**	     **c0 <- c1 <- c2 <- c3 <- c4`**
		     **|**		**---------->**			       **^**	
		     **c4**						       **|_c4**
	**$ git chechout master**
	**$ git merge branch1**		 	    	     **c0 <- c1 <- c2 <- c3 <- c4`**
	Here c3 is master and c4 is branch1
* Here is the another example that you can get much clarity.
	**c1 <- c2 <- c5 <- c6**
		     **^**
		     **|**			  **$git rebase --onto master server client**	**c1 <- c2 <- c5 <- c6 <- c8` <- c9'**
		     **c3 <- c4 <- c10**	**------------------------------------------>**	       **^**	
		     **^**									       **|**	
		     **|**									       **c3 <- c4 <- c10**
		     **c8 <- c9**
	Here c6 is **master**, c10 is **server** and c9 is **client**.
* **$ git chechout master**
  **$ git merge client**
		**c1 <- c2 <- c5 <- c6 <- c8` <- c9'**
		       **^**
		       **|**
		       **c3 <- c4 <- c10**
		Now, c9` acts as **master and client** and c10 is **server**.
  **$ git rebase master server**
		**c1 <- c2 <- c5 <- c6 <- c8` <- c9' <- c3` <- c4` <- c10`**
  **$ git checkout master**
  **$ git merge server**
  **$ git branch -d client server**

###### Hope this could helps!!! :thumbsup: