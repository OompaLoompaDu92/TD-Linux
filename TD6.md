#!/bin/bash
Exercice 1 2

mkdir test-repo
cd test-repo
git init
ls -a
git status
echo "# Test repository" > readme.md
git status
git add readme.md
git status
git commit -m "Add readme file"
git status
git log

#Exercice 3

touch main.py functions.py
git status
git add main.py
git status
git commit -m "Add main.py"
git status
git add functions.py
git commit -m "Add functions.py"
git status
git log

#Exercice 4

touch requirements.txt .gitignore .private
git status
git add .
git status
git commit -m "Add requirements.txt, .gitignore and .private files"
git status
git log --pretty=oneline

#Exercice 5

# Emulate a temporary empty file by creating a file named "temp.ipynb"
touch temp.ipynb

# Check the current git status
git status

# Add an instruction to .gitignore to prevent git from tracking this temp file
echo "temp.ipynb" >> .gitignore

# Check the current git status
git status

# Create other temporary files named "temp.aux" and "temp.log"
touch temp.aux temp.log

# Check the current git status
git status

# Change your instruction in .gitignore to prevent git from tracking any file which name starts with "temp"
echo "temp*" >> .gitignore

# Check the current git status
git status

# Now let’s consider your personal notes will be added to the ".private" folder. Use the "exclude" git file to prevent git from tracking this ".private" folder
echo ".private" >> .git/info/exclude

#Exercice 6

# Add an online description of your repository in the "readme.md" file
echo "# Test repository\nThis is a test repository for learning Git." > readme.md

# Stage your "readme.md" file
git add readme.md

# Display the changes in your root directory since the last commit (not just the current status)
git diff HEAD

# Commit your change
git commit -m "Add online description in readme.md"

# Display the changes since the last commit
git diff HEAD^ HEAD

# Display again the changes in your root directory since the last commit
git diff HEAD

# Change some words in the description of the "readme.md"
echo "# Test repository\nThis is a test repository for learning Git and GitHub." > readme.md

# Display the changes since the last commit
git diff HEAD

#Exercice 7

# 1. Suppress all your files.
rm -rf *

# 2. Use Git to restore your files.
git checkout .

# 3. Backup your Git repository elsewhere (pretending a copy exists on another colleague’s computer or on a remote server).
# Assuming backup is done manually

# 4. Suppress your root directory, create a new empty one and use your backup to restore everything.
cd ..
rm -rf root_directory
mkdir root_directory
cd root_directory
# restore backup from colleague or remote server

# 5. Unstage your first file
git reset HEAD <first_file>

# 6. Commit your two file changes directly, without staging them.
git commit -am "Commit message for two file changes"

# 7. Check your commit log history. Do you see your new commit ?
git log

# 8. Without affecting your Git repository, set your root directory state as of the snapshot of your first commit.
git checkout <first_commit_hash>

# 9. Check your commit log history. You do not see all commits, do you ? How can you see all of them ?
# You can see all commits by running the command: git log --all

# 10. Return to the snapshot of your your last commit.
git checkout <last_commit_hash>

# 11. Undo your second commit by adding a new commit that reverts it.
git revert <second_commit_hash>

# 12. Check the content of your root directory. Have your previous changes disappeard ?
# No, the changes should still be present as the revert commit only creates a new commit that undoes the changes made in the second commit.

# 13. Check your commit log history. Do you see your revert commit ?
git log

# 14. Remove the last 2 commits from the history.
git reset HEAD~2

# 15. Check the content of your root directory. Have your previous changes disappeard ?
# Yes, the changes made in the last 2 commits should have disappeared.

# 16. Check your commit log history. Have you lost the last 2 commits ?
# No, the last 2 commits are still present in the repository's reflog, which is a log of all changes to the repository's references (i.e. branches and tags). However, they are no longer accessible through branch or tag references.
