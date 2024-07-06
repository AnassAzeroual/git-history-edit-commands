# git-history-edit-commands

# Git Commands Documentation

## Remove Backup

The following command is used to remove the backup of your Git repository created by the `git filter-branch` command.

\`\`\`bash
rm -rf .git/refs/original/
\`\`\`

## Change Commit Dates

The following command changes the author and committer dates of all commits in all branches and tags to "07/06/2024 16:14:00".

\`\`\`bash
git filter-branch -f --env-filter '
export GIT_COMMITTER_DATE="07/06/2024 16:14:00"
export GIT_AUTHOR_DATE="07/06/2024 16:14:00"
' --tag-name-filter cat -- --all
\`\`\`

## Force Push

The following command force pushes all branches to the remote repository named `origin`.

\`\`\`bash
git push origin --force --all
\`\`\`

## Create a New Branch

The following commands are used to create a new branch with a new initial commit, delete the old branch, and force push the new branch to the remote repository.

\`\`\`bash
git checkout --orphan newBranch
git add -A
git commit -m "Initial commit"
git branch -D main
git branch -m main
git push -f origin main
\`\`\`

Replace `main` with the name of your default branch if it's not `main`.

## Edit a Specific Commit

The following commands are used to modify the author and committer dates of a specific commit identified by its hash.

\`\`\`bash
git rebase -i 3aac782a16123ccc95fd7547911e806ee434ffd9
GIT_COMMITTER_DATE="07/06/2024 13:14:00" GIT_AUTHOR_DATE="07/06/2024 13:14:00" git commit --amend --no-edit --date "07/06/2024 13:14:00"
\`\`\`
