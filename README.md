# Basic - Q/A
---

1. **What is a version control system? What is Git?**  
   - A version control system (VCS) tracks changes to files over time, enabling collaboration and version tracking.  
   - Git is a distributed VCS that manages source code, allowing multiple developers to work together efficiently.

2. **What are the advantages of using Git?**  
   - Distributed system: No central server dependency.  
   - Fast performance.  
   - Branching and merging for parallel development.  
   - Track changes with history.  
   - Collaboration through tools like GitHub.

3. **What is the difference between Git and GitHub?**  
   - Git: The software used for version control.  
   - GitHub: A web-based platform for hosting Git repositories, facilitating collaboration.

4. **Can you tell me the three storing areas of Git?**  
   - Working directory: Your local files.  
   - Staging area (Index): Files prepared for the next commit.  
   - Repository: The committed files stored in Git.

5. **What is index?**  
   - The index (staging area) is where you stage changes before committing them to the repository.

6. **How do you move files from staging to local repo to remote repo?**  
   - From working directory to staging: `git add <file>`  
   - From staging to local repo: `git commit -m "message"`  
   - From local to remote: `git push origin <branch>`

7. **What is a Git repository?**  
   - A Git repository stores all the project files, including their history, in a `.git` folder.

8. **How do you initialize a Git repository?**  
   - Run `git init` in the project's root directory.

9. **Name your 5 favorite Git commands:**  
   - `git init`: Initialize a repository.  
   - `git status`: Show changes.  
   - `git commit`: Save changes to the repository.  
   - `git pull`: Fetch and merge changes from remote.  
   - `git push`: Push changes to remote.

10. **What are some of the Git hosting repositories?**  
    - GitHub, GitLab, Bitbucket, AWS CodeCommit, Azure Repos.

11. **What command do you use to copy the repo from GitHub to local?**  
    - `git clone <repo-url>`

12. **What is Pull request?**  
    - A pull request (PR) is a request to merge changes from one branch (usually feature branch) into another (like main). It's used for code review and collaboration.

# Intermediate - Q/A
---

1. **How do you remove files from a Git repo?**  
   Use `git rm <file>` to remove files from the repo and staging area. If the file is already deleted locally, use `git rm --cached <file>` to untrack it without deleting it locally.

2. **What is the difference between Git Pull and Pull Request?**  
   - **Git Pull**: Merges changes from a remote repository into your local branch.  
   - **Pull Request**: A request to merge your branch into another branch (usually in collaborative workflows like GitHub).

3. **What is the difference between Git Pull and Git Fetch?**  
   - **Git Pull**: Fetches changes from the remote and merges them into your local branch.  
   - **Git Fetch**: Only downloads the changes, letting you review them before merging.

4. **What is a Merge Conflict? How do you resolve it?**  
   A merge conflict happens when Git cannot automatically reconcile changes in two branches. To resolve it:
   - Open the conflicted file(s) marked by Git.
   - Manually edit and keep the desired changes.
   - Add the resolved files and commit.

5. **How can you list all the files changed in a particular commit?**  
   Use `git show --name-only <commit-hash>`.

6. **What is the difference between fast forward merge and three-way merge?**  
   - **Fast Forward Merge**: Happens when the branch to be merged has no additional commits, and the pointer moves forward.  
   - **Three-Way Merge**: Used when branches have diverged; it considers the base branch, source branch, and target branch for merging.

7. **How can you tell if a branch has been merged or not?**  
   Use `git branch --merged` to see branches that have been merged. Use `git branch --no-merged` to see branches that have not been merged.

8. **I want to ignore certain files in my folder to be tracked by Git. How do I achieve this?**  
   Create a `.gitignore` file and list the files or patterns you want Git to ignore.

9. **What are some of the Git best practices?**  
   - Commit frequently with meaningful messages.  
   - Use branches for features or bug fixes.  
   - Pull and test before pushing.  
   - Avoid committing sensitive data.  
   - Use `.gitignore` for unnecessary files.

10. **What is the difference between `git remote add` and `git clone`?**  
    - **git remote add**: Adds a remote URL to an existing repository.  
    - **git clone**: Creates a copy of a repository (including remote details) on your local machine.

11. **How can you list all the files changed with each commit?**  
    Use `git log --stat` or `git log -p` for detailed changes.


# Github Advance Questions
---

### 1. **What is Cherry-picking?**
   - Cherry-picking in Git allows you to apply specific commits from one branch into another branch without merging the entire branch.
   - Command:
     ```bash
     git cherry-pick <commit-hash>
     ```
   - Example: If a bug fix was committed in a feature branch and you want it in the main branch, cherry-picking can bring over that specific commit.

---

### 2. **What is Squash Merge?**
   - Squash merge combines all the commits in a branch into a single commit before merging it into the target branch.
   - Benefits: Keeps the commit history clean by avoiding clutter from small intermediate commits.
   - Example: 
     ```bash
     git merge --squash <branch>
     git commit -m "Merged branch with squash"
     ```

---

### 3. **What is the difference between Cherry-picking and Merge?**
   - **Cherry-picking** selects specific commits to apply to a branch, while **merge** integrates the entirety of one branch into another.
   - Cherry-picking does not establish a direct relationship between branches, but merging does.

---

### 4. **What is the difference between Rebase and Merge?**
   - **Rebase** rewrites the commit history by moving commits from one branch on top of another branch, making the history linear.
     ```bash
     git rebase <branch>
     ```
   - **Merge** combines two branches while retaining their individual histories.
     ```bash
     git merge <branch>
     ```
   - Use rebase for a cleaner history and merge for preserving the history of both branches.

---

### 5. **How do you restore a commit?**
   - Use `git revert` to create a new commit that undoes the changes made by a previous commit:
     ```bash
     git revert <commit-hash>
     ```
   - To restore a commit completely (hard reset):
     ```bash
     git reset --hard <commit-hash>
     ```
   - Be cautious when using `reset` as it alters the history.

---

### 6. **What is the difference between revert and reset?**
   - **Revert**: Undoes changes by creating a new commit, preserving the history.
   - **Reset**: Moves the branch pointer to a previous state, altering the history (can be destructive).
     - Soft reset:
       ```bash
       git reset --soft <commit>
       ```
       Keeps changes staged.
     - Hard reset:
       ```bash
       git reset --hard <commit>
       ```
       Removes all changes.

---

### 7. **What is the difference between fork and clone?**
   - **Fork**: Creates a copy of a repository in your GitHub account, allowing independent changes and contributions.
   - **Clone**: Copies a repository to your local machine for development.
     ```bash
     git clone <repository-url>
     ```

---

### 8. **What is the difference between git stash and git add?**
   - **Git stash** temporarily saves uncommitted changes without adding them to the staging area:
     ```bash
     git stash
     git stash pop
     ```
   - **Git add** stages changes, preparing them for a commit:
     ```bash
     git add <file>
     ```

---

### 9. **How do you keep your forked repo updated with upstream?**
   - Add the upstream repository:
     ```bash
     git remote add upstream <upstream-repo-url>
     ```
   - Fetch changes from upstream:
     ```bash
     git fetch upstream
     ```
   - Merge upstream changes:
     ```bash
     git merge upstream/main
     ```
   - Or rebase:
     ```bash
     git rebase upstream/main
     ```

---

### 10. **What are the purposes of GitHub issues?**
   - GitHub issues are used for:
     - Tracking bugs, enhancements, and tasks.
     - Collaborating with team members via comments and tags.
     - Assigning tasks using labels, milestones, and assignees.

---

### 11. **What is a Webhook? How is it different than API?**
   - A **Webhook** is an automated mechanism for notifying systems about events in real-time (e.g., a new commit in a repository).
     - Example: Triggering a Jenkins build on a GitHub push.
   - An **API** is a request-response mechanism where a client explicitly requests information or actions.
     - Key difference: Webhooks are event-driven; APIs are client-driven.

---

### 12. **How do DevOps tools get notified of repository changes?**
   - Using **webhooks** to trigger actions such as CI/CD pipelines.
   - Example: Configuring a webhook in GitHub to notify Jenkins on a code push.

---

### 13. **How can you integrate GitHub with a Jenkins job?**
   - Steps:
     1. Install the **GitHub plugin** in Jenkins.
     2. Add a GitHub repository URL in the Jenkins job configuration under "Source Code Management."
     3. Set up a **GitHub webhook** to notify Jenkins of changes.
     4. Add build steps in Jenkins to run scripts, tests, or deployments.

---

Let me know if you'd like detailed examples or further clarification on any of these!
