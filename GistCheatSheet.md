## Git Cheat Sheet
* To install git<br/>
	**$ sudo apt-get install git**
* Getting a git repo<br/>
	**$ git clone https://github.com/abc/abc..**
* Creating a repo
	*  **Make a project folder on GitHub and copy the link**
	*  **$ git init**
	*  **$ git remote add <project folder url>**
	*  **$ git add .**
* Checking a status<br/>
	**$ git status**
* Commiting the repo on stage<br/>
	**$ git commit -m "My Commit"**
* Pushing your local project folder on GitHub server <br/>
	**$ git push original master**
* Logs of your previous commit (history)<br/>
	**$ git log**
* Removing a file from stage (tracked files)<br/>
	**$ git rm <file name or path>**
* To see the difference which one yet staged<br/>
	**$ git diff**
* To see the difference which are staged<br/>
	**$ git diff --staged**
* Creating a new branch<br/>
	**$ git branch <branch name>**
* Swithching between branches<br/>
	**$ git checkout <branch name>**<br/>

	 *  Default branch->**"Master"**<br/>
         *  Branch is _**"movable pointer to the commits"**_ <br/>

* To check on which branch we are currently working<br/>
	**$ git branch**<br/>
	(This will show all the branches and the active branch with a pointer **(*)**)
* To merge a branch with master<br/>
	**$ git merge <branch name>**
* Deleting a branch<br/>
	**$ git branch -d <branch name>**
* While merging _a branch with master_ it should have a direct ancestor. If not, git will doing three way merge.<br/>
<pre>
 c0 <- c1 <- c2 <- c4
              ^
              |
              c3 <- c5</pre>		
	      
	Here c2 is common,c4 is master and c5 is branch1. And hence c2 will be common ancestor.
* Using **c2**(common ancestor), **c4**(master pointer) & **c5**(branch1 pointer).<br/>
	 **Then git creates a *new snapshot* having result of above three snaps**.<br/>
	 <pre>
	 c0 <- c1 <- c2 <- c4 <- c6
		     ^	         |
		     |	         |
		     c3 <- c5 <--`</pre>
		     	     
	Here c6 is **master**.
* To see the last commits on each branch<br/>
	**$ git branch -v**
* To see which branches are already merged you are on:<br/>
	**$ git branch --merge**
* To see which branches are not merged yet:<br/>
	**$ git branch --no-merge**
* **$ git fetch origin**<br/>
	Updates your _local database_ looking upon the server origin (basically the changes that you don't have yet).
* Other than merging we can use **"rebase"**<br/>
	**$ git rebase . master**<br/>
<pre>
	c0 <- c1 <- c2 <- c3				
		     ^		  rebase	     c0 <- c1 <- c2 <- c3 <- c4`
		     |		---------->			       	
		     c4						       
	$ git chechout master
	$ git merge branch1		 	     c0 <- c1 <- c2 <- c3 <- c4`</pre>
	
	Here c3 is master and c4 is branch1
* Here is the another example that you can get much clarity.<br/>
<pre>
	c1 <- c2 <- c5 <- c6
		     ^
		     |			  $git rebase --onto master server client	c1 <- c2 <- c5 <- c6 <- c8` <- c9`
		     c3 <- c4 <- c10	------------------------------------------>	       ^
		     ^									       |
		     |									       c3 <- c4 <- c10
		     c8 <- c9</pre>
		     
	Here c6 is master, c10 is server and c9 is client.
* **$ git chechout master**
* **$ git merge client**<br/>
	<pre>
		c1 <- c2 <- c5 <- c6 <- c8` <- c9`
		       ^
		       |
		       c3 <- c4 <- c10
		       </pre>
		Now, c9` acts as master and client and c10 is server.
		
* **$ git rebase master server**<br/>
	<pre>
		 c1 <- c2 <- c5 <- c6 <- c8` <-c9` <-c3` <- c4` <- c10` 
		 </pre>
* **$ git checkout master**
* **$ git merge server**
* **$ git branch -d client server**

###### Hope this will be helpful!!! :thumbsup:
