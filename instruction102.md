# Collaborative Git Workflows

* Go back to the feature branch: `git checkout feature/project-name/description`
* Confirm that the remote branch is up to date with the branch in the origin by running `git status`
* If the branch is behind, then fetch the latest changes from the main branches in origin and merge them into your local branch

```bash 
git checkout feature/project-name/description

git fetch origin 

git merge origin/main
```
## __11. Moving Work Around (git cherry-pick)__
**Member 2** is required to simulate a common mistake: committing work to the **wrong branch.**

To list all the local branches, use:
```bash
git branch
```

To list all the branches in the origin (remote branches), use:
```bash
git branch -r
```

To show which branch you are currently on, use:
```bash 
git status
```
1. __The Simulated Mistake:__ Commit an update in the wrong branch.

2. __Get the ID:__ Find the **Commit ID (SHA value)** of the misplaced commit in the wrong feature branch.
    * Note that you need to be in the branch that contains the misplaced commit first: `git checkout feature/lab-number/description-of-wrong-branch`  
    * Then view the commit IDs (SHA values) using `git log --oneline`.

3. __Switch and Copy:__
    * Confirm that the commit is not in the correct branch by switching to it and checking the log: 
    ```bash 
    git checkout feature/lab-number/description-of-wrong-branch`   

    git log --oneline
    ```

    * Perform the cherry-picking to copy the commit from the wrong branch to the correct branch:
    ```bash 
    git cherry-pick <Commit-ID-from-Step-2>
    ```
    *Note: Git applies those changes to your current branch and creates a **new commit ID**, while the original commit remains in the old branch.*

4. __Clean up:__
    * Switch back to the branch that had the misplaced commit and use `git reset --hard HEAD~1` (see the next Section) to remove the duplicate commit from the wrong location.





























