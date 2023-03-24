#!/bin/bash

#Exercice 1

# 1. Create an empty working directory called “td4”.
mkdir td4

# 2. Initialize a Git repository in it.
cd td4
git init

# 3. Install the Linux python3-pip package using your Linux package manager.
# For Debian-based systems, run:
sudo apt-get update && sudo apt-get install python3-pip

# 4. Install the VirtualEnv Python package using pip3.
pip3 install virtualenv

# 5. Create a Python virtual environment called “.env”.
virtualenv .env

# 6. Activate your virtual environment.
source .env/bin/activate

# 7. List the Python packages installed in your virtual environment.
pip list

# 8. Does Git want you to commit something ?
# Do you think it is a good thing ?
# hint : You can find templates at https://github.com/github/gitignore
git status

# 9. Create a .gitignore file to tell Git which files should be untracked.
echo ".env/" > .gitignore

# 10. Does Git want you to commit something ?
# Do you think it is a good thing this time ?
git status

# 11. Do your first commit and check that Git is happy now.
git add .
git commit -m "Initial commit"
git status

#manque de temps pour la suite 
