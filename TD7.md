#Exercice 1

git clone https://github.com/OompaLoompaDu92/TD-Linux.git

cd TD-Linux
cat README.md
sudo apt-get install git

#Exercice 2

git branch <your-branch-name>
git branch john-doe
echo "Hello, this is John Doe." > john-doe.txt
git add john-doe.txt
git commit -m "Add john-doe.txt"
git push -u origin <your-branch-name>
git push -u origin john-doe

#Exercice 3

git checkout master
git merge <your-branch-name>
git commit -m "Merge <your-branch-name> into master"
git push origin master

#Exercice 4


git checkout <your-branch-name>
nano README.md
git commit -am "Your commit message"
git pull origin master
git merge <your-branch-name>
git push origin master

#Exercice 5

cd TD-Linux
git checkout your_branch_name
git pull origin master
nano README.md
git add README.md
git commit -m "Added team members' names to README.md"
git push origin your_branch_name

#Exercice 6

git branch -d your-branch-name
git push origin --delete your-branch-name
git branch

#Exercice 7

git checkout master
git pull origin master
git checkout -b your_branch_name
echo "" > README.md
echo "Git interactive rebase" > README.md
sed -i '6d' README.md
echo "Written by [Your Name]" >> README.md

git add README.md
git commit -m "Clear the whole file, removing all text."
git add README.md
git commit -m "Add a title line 'Git interactive rebase'."
git add README.md
git commit -m "Copy the first paragraph from https://git-scm.com/book/en/v2/GitTools-Rewriting-History."
git add README.md
git commit -m "Add the second paragraph from the same page."
git add README.md
git commit -m "Add the first and second paragraphs from the 'Changing Multiple Commit Messages' section in the same page."
git add README.md
git commit -m "Remove the second paragraph from your file."
git add README.md
git commit -m "Add the missing title 'Changing Multiple Commit Messages' on a line just before the two paragraphs you copied (before 'To modify a commit that is farther back in your history...')."
git add README.md



