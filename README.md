#  **CS620 Git Quickstart**
##  **Create Project Git Repository**
1. **Determine** whether you are creating a **new repo** or using an **existing/provided repository**.
2. **Creating your own repository**  
   - I am going to use **GitHub**, and we recommend using GitHub (previous semester GitLab did not work well)  
   - Have **one team member** create a new repository (https://github.com/new).
---
## ⚙️ **Setting Up Repository Settings**
1. Make sure to **add all of your team members** by going to:  **Settings -> Collaborators** 
2. Please invite **all the course staff** to your repo as well: 

> Amber - amberrfield, Jerry - jerluo, Cathy - cqthyy, Leah - UWLeahUjda

3. **Recommended:** Protect your **main branch** and require pull requests: - **Settings -> Rules -> Ruleset**
   - Name the rule (e.g., "main" or whatever you like).
   - Click add target -> include default branch.
   - Check "Require a pull request before merging" under **branch rules**.

---
## 🏁 **Getting Started**

4. Once everyone is added to the repository, **clone** the repository to your machine with:
```bash
git clone <HTTPS URL>
```
   
5. Each group member should:
   - Create their own **branch**.
   - Print out "Hello World".
   - **Commit** these changes and push them to their branch.
6. **Create a pull request** and merge your feature into main
---
## 📚 **Git Useful Reference**

### ⚡️ **Workflow**
There are three key states maintained with Git:
- **Working tree** 🛠️ – Your local files.
- **Index** 📋 – Staging area for new commits.
   - Use `git add *` to add everything to staging.
- **Head** 📍 – Current commit you are working with (latest commit usually)

### 🌳 **Branching**
- Branches are used to develop features **isolated** from each other. 
- To avoid deleting your teammates code, we want to protect our **main branch** and only commit new changes to **feature branches**.

   **Create a new branch** named `feature_x` and switch to it using:  
```bash
git checkout -b feature_x
```
### 🔄 **Merge or Rebase**
- Remember to run `git pull` in main to update your local with changes made by your teammates.
- You can then **merge** a branch into your current branch. This is non-destructive and creates a new merge commit at your feature branch HEAD  
```bash
git merge <branch>
```
- If you are working on a branch **ALONE**, you can use rebase instead
```bash
git rebase <branch>
```
- This is destructive and moves your feature commits linearly after any changes in the rebased branch. This gives you a cleaner commit history but it is destructive
- See [here](https://www.atlassian.com/git/tutorials/merging-vs-rebasing) for more info
---
### Git Setup
#### Installing Git
- May need to install if you haven't already and are on windows. See [link](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for instructions
#### Git Config
- Set up your identity:
```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
#### GitHub SSH
If you are using a private repo, it is nice to use SSH to authenticate your GitHub account
- See the GitHub [docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) to setup your SSH key
---
### 🧹 Error: please commit your changes
We often need to do branch operations (merge, push, pull) that require a clean working tree. This means you either need to stash uncommitted work or get rid of it.

- Save local commits for later (remove from working tree)
```bash
git stash
# now do whatever with your clean state
git stash pop
# now we brought all those changes back
```

- If you messed up so bad you just want to delete everything and copy whatever is on origin
```bash
# get latest from remote origin
git fetch origin
git checkout main
git reset --hard origin/main
# delete untracked files/directories
git clean -d --force
# do this for each messed up branch
```
### Force push (careful!!!)
You can get overwrite remote commits
```bash
git push origin <branch> --force
```

### 🧹 **Someone broke something at some point**
- You can go and checkout a suspicious commit:  
```bash
git checkout <SHA>
```
- Check differences from current (HEAD) and prior commit
```bash
git show <SHA>
```
- And revert all changes in that commit (undo changes in a specific commit)
```bash
git revert <SHA>
```
- Or we can checkout only that broken file and commit it
```bash
git checkout <SHA> -- path/to/file
git commit -m "Wow, you don't need to copy-paste to undo!"
```
#### Git bisect
- We can also be fancy and use binary search to find the bad commit
```bash
git bisect start
git bisect bad
git bisect good <known good commit SHA>
```
- Git will auto checkout commits with binary search and ask if the issue persists:
	- Yes: ```git bisect bad```
	- No: ```git bisect good```
- Finally, it will tell you the latest good commit and you can leave git bisect with:
```bash
git bisect reset
```

--- 
For basic information, refer to this [Git Guide](https://rogerdudler.github.io/git-guide/)
And this [Oh Shit, Git!?!](https://ohshitgit.com/) for when you mess up
