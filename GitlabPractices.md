# GitLab Practices
This document provides guidance on how to utilize GitLab as the District Defend code repository.

## Merge Requests
1. **Branch using the GitLab merge request** for a given issue you are assigned to work on. 
2. **Initiate the merge request when you start working on the issue** and create a feature branch.
3. **Avoid having too many branches at any point in time**, so as to avoid complex branch merge situations. For example:
    * If you are working on 5 issues and you create a feature branch for all 5 issues, then the parent (development) branch will change everytime the work in the feature branch is merged back in.
    * If the work for the issues touch the same file(s), you may be introducing scope creep. That is, the person merging the 5th feature branch will have to make sure the functionality implemented for all 5 issues still work. **_Try to avoid this situation._**
4. **Link closely related issues** if they are targeted for completion in the same sprint and the work must be completed in a single feature branch (i.e. work for one issue will impact the work for another). For example:
    * If you are assigned 3 issues on the same repository for a given sprint.
    * Create a single merge request from the first issue you are working on. This will create the feature branch.
    * Link the other 2 issues to the original issue.
    * Update your merge request description to note that it **_Closes #[issue id]_**. 
5. **Assign Approvers** for your merge request
6. **Resolve the WIP flag** when you are done working on the issue(s) for a merge request, and would like the approvers to review your work.
7. **Approvers should review changes, build and do a smoke test** before approving a merge request.
8. **Merge and remove the feature branch** when you are ready to resolve the issue(s) and close out the merge request.

## Merging Approaches
1. **No Branch History** - If you created a feature branch and the parent (development) branch changed before you worked on it, and you have not made any commits, you may:
    1. **Close the merge request and create a new one.** This should trigger GitLab to delete the current branch and create a new one based off of the current HEAD revision in the  development branch. If you are unable to create a new merge request, confirm that GitLab  in fact deleted your old branch. If not, you may have to manually delete the GitLab branch. 
    ![Image of Git History when recreating a feature branch](/images/no_branch_history_recreate.png)
    2. **Merge changes from development into your branch.** An example of how to do this is included in the [Cheatsheet section](#merge-development-branch-into-feature-branch).
    ![Image of Git History when merging development into feature branch with no feature branch history](/images/no_branch_history_merge.png)

2. **Branch History Exists** - If you have worked on your merge request branch and have committed changes, you will have to merge your changes from the development branch into your merge request branch. An example of how to do this is included in the [Cheatsheet section](#merge-development-branch-into-feature-branch).
![Image of Git History when merging development into feature branch and merging feature branch changes](/images/branch_history_merge.png)

## Cheatsheet

### Merge development branch into feature branch
The following git commands are a reference on how to merge work from development into your feature branch. 
1. _git stash_ (Stash your changes)
2. _git pull_ (to fetch origin and merge to your local branches)
3. _git checkout [branch name]_ (Confirm that you are in your branch)
4. _git merge --no-ff development_ (merge changes in the development branch into your branch)
5. _git stash pop_ (restore your changes)
6. Resolve merge conflicts and verify nothing "broke"

### Cheatsheet of Git Commands
| Command | Description |
| -------- | ----------- |
| _git branch -a_ | List all git branches |
| _git branch -d [branch name]_ | Delete a local branch |
| _git checkout [branch name]_ | Check out a branch. If you enter a branch name that doesn't exist, it will create a new branch |
| _git push origin --delete [branch name]_ | Delete a remote branch |
| _git remote prune origin_ | Clear references to remote branches that have been removed |
| _git fetch origin_ | Get latest from remote | 
| _git merge_ | Merge remote branch(s) into your local branch(s) |
| _git merge --no-ff [branch name]_ | Merge the HEAD revision of the branch (identified by branch name) into the branch you are currently working in. The _--no-ff_ flag will treat the merge commit as a new revision in the history. |
| _git pull_ | Get latest changes from remote and merge into your local. This command is essentially a _git fetch origin_ and _git merge_ combined. |
| _git stash_ | "Stash" your dirty/unstaged changes by temporarily storing them  |
| _git stash pop_ | "Pop" the first stashed changes to resume working |
| _git stash list_ | List all "stashed" changes |
| _git stash drop [id]_ | Drop the "stashed" items and get rid of all dirty/unstaged changes |
