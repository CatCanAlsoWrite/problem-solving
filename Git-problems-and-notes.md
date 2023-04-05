# programming, then initialize a repository 
1.Create the local project: 

- `mkdir xxx-folder-name`→`cd xxx-folder-name` →programming

2.Creating a new repository on git website: add name, set "public"

3.Open ==git bash== in VS code

4.Open local project:

- `cd xxx-folder-name` 

5.Initialize empty git repository

- →`git init`

6.Add the file to the new local repository

- →`git add .`/`git add xxx-file-name.txt` (to staging area)

- ==if wrongly added==: 
	
	- ==solution:== `git restore --staged xxx-file-name.txt` (unstage)

7.Commit the files staged in your local repository by writing a commit message: 

- →`git commit -m *(message)* "xxx-message"`(message is written in an imperative sentence up to 50 characters long and defining "what was changed", and "why was the change made")

8.Rename branch: 

- →`git branch -m main*(default local branch name)*`

9.***Copy your remote repository's URL from GitHub***

10.***Add the URL copied:***  

- →`git remote add origin https:xxx-repository-url`

11.***Push the code in your local repository to GitHub:*** 

- →`git push -u *(upstream)* origin*(default remote name)* main*(default remote branch name)*`/`git push --set-upstream origin main`

- ==if met error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Recv failure: Connection was reset"

- ==or error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Failed to connect to github.com port 443 after 21327 ms: Couldn't connect to server"

	- ==solution:== `git remote remove origin`→`git remote add origin https:xxx-repository-url`→`git push -u origin main`

12.View files in your repository hosted on GitHub

## attention: React page repository is different
1.Create the local project: 

- `mkdir xxx-file-name`→`cd xxx-folder-name` →programming

2.Creating a new repository on git website: add name, set "public"

3.Open ==git bash== in VS code

4.Open local project:

- `cd xxx-folder-name` 

5.Initialize empty git repository

- →`git init`

6.Rename branch: 

- →`git branch -m main*(default local branch name)*`

7.***Copy your remote repository's URL from GitHub:***

8.***Add the URL copied:***  

- →`git remote add origin https:xxx-repository-url`

9..***Add the GitHub Pages dependency package:***

- →`npm install gh-pages --save-dev`

10.***Add the deploy scripts in the "package.json" file:***

- `"homepage": "http://xxx-github-username.github.io/xxx-repository-name"`

- `"scripts":{"predeploy" : "npm run build", "deploy" : "gh-pages -d build"}`

11.Add the file to the new local repository:

- →`git add .`/`git add xxx-file-name.txt` (to staging area)

- ==if wrongly added==: 
	
	- ==solution:== `git restore --staged xxx-file-name.txt` (unstage)

12.Commit the files staged in your local repository by writing a commit message: 

- →`git commit -m *(message)* "xxx-message"`

13.***Push the code in your local repository to GitHub:*** 

- →`git push -u *(upstream)* origin*(default remote name)* main*(default remote branch name)*`/`git push --set-upstream origin main`

- ==if met error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Recv failure: Connection was reset"

- ==or error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Failed to connect to github.com port 443 after 21327 ms: Couldn't connect to server"
	
	- ==solution:== `git remote remove origin`→`git remote add origin https:xxx-repository-url`→`git push -u origin main`

~~14.***Deploy React application:***~~

- ~~→`npm run deploy`~~

15.View files in your repository hosted on GitHub

- To view our deployed React application, navigate to the **Settings** tab and click on the **Pages** menu. You should see a link to the deployed React application.

# clone a repository, then do more programming
1.Open ==git bash== in VS code

2.***Clone the git repository:***

- `git clone https:xxx-repository-url`

- →`cd xxx-folder-name`→`ls -la`*(and drag in the former coded but haven't updated files)* 

3.Add the file to the new local repository

- →`git add .`/`git add xxx-file-name.txt` (to staging area)
	
	- undo git add: `git restore --staged xxx-file-name.txt` (unstage)

-  branch: 
	
	- check: `git status` *(branch up-to-date)*/`git branch` *(all branches)*
	
	- create and switch to the new branch: `git checkout -b *(branch)* xxx-local-branch-newname`/`git branch xxx-local-branch-newname`
	
	- switch to an existed branch: `git checkout xxx-local-branch-anothorname`
	
	- rename branch: `git branch -m *(move)* xxx-local-branch-newname*(rename this local branch)*`/`git branch -m xxx-local-branch-oldname xxx-local-branch-newname *(when in local but not the branch)*`
	
	- delete branch: `git branch -d xxx-local-branch-deletename`(delete locally), `git push --delete xxx-local-branch-deletename`/`git push origin: xxx-remote-branch-deletename`(delete remotely)

	- synchronize branch list: `git fetch -p *(prune)*`

4.Commit the files staged in your local repository by writing a commit message: 

- →`git commit -m *(message)* "xxx-message"`(message is written in an imperative sentence up to 50 characters long and defining "what was changed", and "why was the change made")

5.Push the code in your local repository to GitHub: 

- →`git push origin*(default remote name)* main*(default remote branch name)*`/`git push`

---
ref:
- https://www.datacamp.com/tutorial/git-push-pull
- https://blog.logrocket.com/deploying-react-apps-github-pages/#pushing-the-react-app-to-the-github-repository
