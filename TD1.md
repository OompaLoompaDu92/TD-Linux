#!/bin/bash

# Exercice 1
# Go to the root directory
cd /

# Display the content of the current (root) directory
ls

# Check your current location
pwd

# Try to create a directory named test
mkdir test

# Go to the general home directory (should contain folders named after each user)
cd /home

# Go to your home directory
cd ~

# Go back to the general home directory (located "just above")
cd /home

# Go again "just above", you should be back to the root directory
cd /

# Go directly to your home directory (named after you). It should be a very simple command, which take no name as parameter of the path
cd ~

# Try to create a directory named test
mkdir test

# Go into this new directory
cd test

# Check your current location
pwd

#Exercice 2

# Go to your home directory (should be named after you, you might be there by default)
cd ~

# Check your current location
pwd

# Create a folder linux_ex_1
mkdir linux_ex_1

# Go into this folder
cd linux_ex_1

# Create an empty text file named [first_name]_[last_name].txt (e.g. alexis_bogroff.txt)
touch [first_name]_[last_name].txt

# Create a folder notes
mkdir notes

# Move your text file into this folder
mv [first_name]_[last_name].txt notes/

# Rename the text file by appending the current year [first_name]_[last_name]_[current_year].txt
mv notes/[first_name]_[last_name].txt notes/[first_name]_[last_name]_$(date +"%Y").txt

# Make a copy of this folder, name it notes_2022
cp -r notes notes_2022

# Delete the first folder (notes) using the verbose option
rm -rv notes


#Exercice 3


# Create a script script_1.sh in the folder linux_ex_1
cd ~/linux_ex_1
touch script_1.sh

# In the script, write the commands that would output the following:
# Script running please wait ...
# Done.
echo "Script running please wait ..."
echo "Done."

# Quit editing and save the script

# Display the content of the script (using a command, not from an editor)
cat script_1.sh

# Run the script
bash script_1.sh

#Exercice 4


# Create a file credentials in the folder linux_ex_1
cd ~/linux_ex_1
echo "Fake personal information" > credentials

# Display the file content
cat credentials

# Display the current permissions
ls -l credentials

# Change the current permissions to : read only for all users
chmod a-w credentials

# Display the new permissions
ls -l credentials

# Modify and save the file
echo "Modified content" > credentials

# Display the file content
cat credentials

# Change the permissions back to read and write for all users
chmod a+rw credentials

# Display the new permissions
ls -l credentials

# Modify and save the file
echo "New modified content" > credentials

# Display the file content
cat credentials

# Add the execute permission to the owner
chmod u+x credentials

# Display the new permissions
ls -l credentials

# Remove the read permission to other users
chmod o-r credentials

# Display the new permissions
ls -l credentials

# Change the permissions to read, write and execute for all users
chmod a+rwx credentials

# Display the new permissions
ls -l credentials


#Exercice 4.2


# Go to the root folder
cd /

# Create a file in root user mode named .private_file
sudo nano .private_file

# (a) Write some information in the file
# (b) Display the file content
cat .private_file

# Display all the files in the folder including hidden files
ls -la /

# Modify the file in normal user mode
nano .private_file

# (a) Write some new information in the file
# (b) Display the file content
cat .private_file

# Modify the file in root user mode
sudo nano .private_file

# (a) Write some new information in the file
# (b) Display the file content
cat .private_file

# Change permissions to read, write and execute for all users
sudo chmod a+rwx .private_file

# (a) Modify the file content in normal user mode
nano .private_file

# (b) Display the file content
cat .private_file


#Exercice 4.3



# Change permissions of .private_file to read and write for all users, in normal user mode
chmod 666 /root/.private_file

# Set the new file owner as the current user
chown $USER:$USER /root/.private_file

# Change permissions of .private_file to read and write for all users, in normal user mode
chmod 666 /root/.private_file

#Exercice 4.4


# Update apt
sudo apt update

# Upgrade apt
sudo apt upgrade -y

# Install cmatrix
sudo apt install -y cmatrix

# Launch cmatrix
cmatrix

# Wait for user to quit cmatrix
read -p "Press enter to quit cmatrix"

# Install tmux
sudo apt install -y tmux

# Launch tmux
tmux new-session -s session0 -d

# Send command to session0
tmux send-keys -t session0 "echo 'Hello session 0'" Enter

# Launch cmatrix in session0
tmux send-keys -t session0 "cmatrix" Enter

# Detach from session0
tmux detach-client -s session0

# Create new session1
tmux new-session -s session1 -d

# Send command to session1
tmux send-keys -t session1 "echo 'Hello session 1'" Enter

# Detach from session1
tmux detach-client -s session1

# List all running sessions
tmux ls

# Attach to session0
tmux attach-session -t session0

# Detach from session0
tmux detach-client -s session0

# Attach to session1
tmux attach-session -t session1

# Detach from session1
tmux detach-client -s session1

# Kill all tmux sessions
tmux kill-server

# List all running sessions
tmux ls

#Exercice 4.5


# 1. Display the cmatrix help function
cmatrix -h

# 2. Launch cmatrix and make it display white characters
cmatrix -C white

# 3. Re-launch cmatrix and slow down the speed of characters actualization
cmatrix -s 10

# 4. Stop cmatrix
pkill cmatrix

# 5. Launch cmatrix with both slow speed and blue characters
cmatrix -s 10 -C blue

# 6. Display cmatrix manual
man cmatrix

# 7. Display the tmux help function
tmux -h

# 8. Display the tmux manual
man tmux
