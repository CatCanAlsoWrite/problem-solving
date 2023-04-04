# programming, then initialize a repository 

1.Create the local project: 

- `mkdir xxx-file-name`→`cd xxx-file-name` →programming
  
2.Creating a new repository on git website: add name, set "public"

3.Open ==git bash== in VS code

4.Open local project:

- `cd xxx-file-name` 

5.Initialize empty git repository

- →`git init`

6.Add the file to the new local repository

- →`git add .`/`git add xxxx.txt` (to staging area)

- ==if wrongly added==: 

  - ==solution:== `git restore --staged xxxx.txt` (unstage)

7.Commit the files staged in your local repository by writing a commit message: 
	
- →`git commit -m *(message)* "xxxxx"`(message is written in an imperative sentence up to 50 characters long and defining "what was changed", and "why was the change made")

8.Rename branch: 

- →`git branch -m main`

9.***Copy your remote repository's URL from GitHub***

10.***Add the URL copied:***  

- →`git remote add origin https:xxxx`

11.Push the code in your local repository to GitHub: 

- →`git push -u(upstream for the first time after 'git remote add origin https:xxxx') origin(shorthand alias for the URL of remote repository used after git clone) xxxx(branch name)`

- ==if met error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Recv failure: Connection was reset"

- ==or error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Failed to connect to github.com port 443 after 21327 ms: Couldn't connect to server"
	
  - ==solution:== `git remote remove origin`→`git remote add origin https:xxxx`→`git push -u origin xxxx`

12.View files in your repository hosted on GitHub


## attention: React page repository is different

1.Create the local project: 
	
- `mkdir xxx-file-name`→`cd xxx-file-name` →programming

2.Creating a new repository on git website: add name, set "public"

3.Open ==git bash== in VS code

4.Open local project:

- `cd xxx-file-name` 

5.Initialize empty git repository

- →`git init`

6.Rename branch: 

- →`git branch -m main`

7.***Copy your remote repository's URL from GitHub:***

8.***Add the URL copied:***  

- →`git remote add origin https:xxxx`

9.Push the code in your local repository to GitHub: 

- →`git push -u(upstream for the first time after 'git remote add origin https:xxxx') origin(shorthand alias for the URL of remote repository used after git clone) xxxx(branch name)`

- ==if met error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Recv failure: Connection was reset"

- ==or error:== "fatal: unable to access 'https://github.com/xxx-github-username/xxx-repository-name.git/': Failed to connect to github.com port 443 after 21327 ms: Couldn't connect to server"
	
  - ==solution:== `git remote remove origin`→`git remote add origin https:xxxx`→`git push -u origin xxxx`

10.***Add the GitHub Pages dependency package:***

- →`npm install gh-pages --save-dev`

11.***Add the deploy scripts in the "package.json" file:***

- `"homepage": "http://xxx-github-username.github.io/xxx-repository-name"`

- `"scripts":{"predeploy" : "npm run build", "deploy" : "gh-pages -d build"}`

12.Add the file to the new local repository:

- →`git add .`/`git add xxxx.txt` (to staging area)

- ==if wrongly added==: 
	
  - ==solution:== `git restore --staged xxxx.txt` (unstage)

13.Commit the files staged in your local repository by writing a commit message: 

- →`git commit -m *(message)* "setup gh-pages"`

14.Push the code:

- →`git push

15.***Deploy React application:***

- →`npm run deploy`

16.View files in your repository hosted on GitHub

- To view our deployed React application, navigate to the **Settings** tab and click on the **Pages** menu. You should see a link to the deployed React application.


# clone a repository, then do more programming

1.Open ==git bash== in VS code

2.Clone the git repository

- →`git clone *(first download the repository)* https:xxxx *(paste https/ssh URL from github.com)* `→`cd xx` *(repository name)* →`ls -la`*(and drag in the former coded but haven't updated files)* 

3.Add the file to the new local repository

- →`git add .`/`git add xxxx.txt` (to staging area)
	
  - undo git add: `git restore --staged xxxx.txt` (unstage)

-  branch: 
		
    - check: `git status` *(branch up-to-date)*/`git branch` *(all branches)*
	
    - create and switch to the new branch: `git checkout -b *(branch)* xxxx *(branch name)*`/`git branch xxxx *(branch name)*`
	
    - switch to an existed branch: `git checkout xxxx *(branch name)*`
	
   - rename branch: `git branch -m *(move)* newname *(when in the local branch)*`/`git branch -m oldname newname *(when in local but not the branch)*`
	
    - delete branch: `git branch -d xxxx *(branch name)*`(delete locally), `git push --delete xxxx *(branch name)*`/`git push origin: xxxx *(branch name)*`(delete remotely)
	
   - synchronize branch list: `git fetch -p *(prune)*`

4.Commit the files staged in your local repository by writing a commit message: 

- →`git commit -m *(message)* "xxxxx"`(message is written in an imperative sentence up to 50 characters long and defining "what was changed", and "why was the change made")

5.Push the code in your local repository to GitHub: 

- →`git push origin(shorthand alias for the URL of remote repository used after git clone) xxxx(branch name)`


---

ref:

- https://www.datacamp.com/tutorial/git-push-pull

- https://blog.logrocket.com/deploying-react-apps-github-pages/#pushing-the-react-app-to-the-github-repository
