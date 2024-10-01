
# 🎓 **CS620 Git Quickstart**

## 🚀 **Create Project Git Repository**
1. **Determine** whether you are creating a **new repo** or using an **existing/provided repository**.
   
2. **Creating your own repository**  
   - I am going to use **GitHub**, but you can use **GitLab** if you prefer.  
   - Have **one team member** create a new repository (https://github.com/new).

## ⚙️ **Setting Up Repository Settings**
1. Make sure to **add all of your team members** by going to:  
   **Settings -> Collaborators** 
   
2. **Recommended:** Protect your **main branch** and require pull requests:   - **Settings -> Rules -> Ruleset**
   - Name the rule (e.g., "main" or whatever you like).
   - Click add target ➡️ include default branch.
   - Check "Require a pull request before merging" under **branch rules**.

---

## 🏁 **Getting Started**

1. Once everyone is added to the repository, **clone** the repository to your machine with:
   ```bash
   git clone <HTTPS URL>
   ```
   
2. Each group member should:
   - Create their own **branch**.
   - Print out "Hello World".
   - **Commit** these changes and push them to your branch.
   
3. **Create a pull request** and merge your feature into **main**! 🎉

---

## 📚 **Git Useful Reference**

### ⚡️ **Workflow**
There are three key states maintained with Git:
- **Working directory** 🛠️ – Your local files.
- **Index** 📋 – Staging area for new commits.
   - Use `git add *` to add everything to staging.
- **Head** 📍 – Your latest commits.

### 🌳 **Branching**
- Branches are used to develop features **isolated** from each other. 
- To avoid **merge hell**, we want to protect our **main branch** and only commit new changes to **feature branches**.
- However, you can discuss with your team how to organize this.

   **Create a new branch** named `feature_x` and switch to it using:  
   ```bash
   git checkout -b feature_x
   ```

---

### 🔄 **Update & Merge**
- Remember to run `git pull` to update your local repository with changes made by your teammates.
- You can then **merge** a branch into your current branch with:  
   ```bash
   git merge <branch>
   ```

### 🧹 **Replace Local Changes**
- Replace changes in your local with the last content of **HEAD**:  
   ```bash
   git checkout -- <filename>
   ```

- If you want to **get rid of all your local changes AND commits**:
   ```bash
   git fetch origin
   git reset --hard origin/main
   ```

--- 
**For more information, refer to this [Git Guide](https://rogerdudler.github.io/git-guide/).**
