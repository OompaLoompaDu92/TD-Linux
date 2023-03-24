#!/bin/bash

#Exercice 1

# Put system up to date
sudo apt-get update && sudo apt-get upgrade -y

# Display system information
echo "Linux version:"
uname -a
echo "Current processes and memory usage associated:"
ps aux --sort=-%mem | awk '{printf("%-20s %-10s %-10s %-10s %-20s\n", $USER, $PID, $CPU, $MEM, $COMMAND)}'
echo "Number of processors:"
nproc
echo "L1, L2, and L3 cache size:"
lscpu | grep cache
echo "Disk space:"
df -h
echo "Mounted devices:"
mount | column -t
echo "Connected USB devices:"
lsusb
echo "Hostname:"
hostname

#Exercice 2

#!/bin/bash

# 1. Create a variable x and assign it the short text piri pimpin
x="piri pimpin"

# 2. Display the value of this variable
echo "The value of x is: $x"

# 3. Add to this value the following text piri pimpon
x+=" piri pimpim piri pimpon"

# 4. Create a folder named my_programs, then enter into that folder
mkdir my_programs
cd my_programs

# 5. Create a script named pilou that displays pilou pilou
echo "echo 'pilou pilou'" > pilou

# 6. Run this script
./pilou

# 7. Make this script executable
chmod +x pilou

# 8. Run the script by writting its name only
pilou

# 9. Display the content of the variable PATH
echo "The content of the PATH variable is: $PATH"

# 10. Add the path of your current location to the global variable PATH
PATH="$PATH:$(pwd)"

# 11. When you are sure of the result, export it
export PATH

# 12. Go to your home directory
cd ~

# 13. Run your script by writting its name only
my_programs/pilou

# 14. Change the value of the PATH in the .profile file in order to make it permanent
echo "export PATH=\"$PATH\"" >> .profile

# 15. Create a new shell and run your script using its name only
# (run this command manually)

#Exercice 3

nano say_hello.sh

echo $(date +"%Y-%m-%d %H:%M:%S") Hello >> hellos.txt

chmod +x say_hello.sh

crontab -e

* * * * * /path/to/say_hello.sh

#Exercice 4

#!/bin/bash

# 1. Create a folder named hash_checksum. Go into this folder
mkdir hash_checksum
cd hash_checksum

# 2. Inside this folder, create two files named .sensible_addresses and .sensible_passwords
touch .sensible_addresses
touch .sensible_passwords

# 3. Display the list of files of the folder
ls

# 4. Still inside the folder hash_checksum, create a script named gentle_script.sh. This script should display the following text "Have a good day"
echo "echo Have a good day" > gentle_script.sh

# 5. Run the script
bash gentle_script.sh

# 6. Compute the sha256sum of gentle_script. Store it into a file named log_sha
sha256sum gentle_script.sh > log_sha

# 7. Now corrupt the file by adding a line of code that deletes any file starting with : ".sensible"
echo "rm -f .sensible*" >> gentle_script.sh

# 8. Compute again the sha256sum of gentle_script. Store it into the log_sha file
sha256sum gentle_script.sh >> log_sha

# 9. Run the script
bash gentle_script.sh

# 10. Display again the list of files of the folder
ls

# 11. Display the log_sha content : are the hashes any different ?
cat log_sha

#Exercice 5

#!/bin/bash

# Step 1: Install QPDF
sudo apt-get install qpdf

# Step 2: Create the directory and go into it
mkdir compress
cd compress

# Step 3: Create the first file
echo "Hello" > hello

# Step 4: Compute the deflate compression (level 1) of the first file and store the compressed file size
zlib-flate -1 < hello | wc -c > log_compress

# Step 5: Create the second file
yes "Hello" | head -n 1000 > hello_multiple

# Step 6: Compute the deflate compression (level 1) of the second file and store the compressed file size
zlib-flate -1 < hello_multiple | wc -c >> log_compress

# Step 7: Create the third file
for i in {1..100}; do echo "Hello $i"; done > hello_multiple_i

# Step 8: Compute the deflate compression (level 1) of the third file and store the compressed file size
zlib-flate -1 < hello_multiple_i | wc -c >> log_compress

# Step 9: Display the content of log_compress
cat log_compress

# Step 10: Compute the compression ratio of each file and display it as a simple fraction
echo "Compression ratios:"
echo "hello: $(echo "$(cat hello | wc -c)/$(cat log_compress | head -n 1)" | bc -l | cut -c 1-5):1"
echo "hello_multiple: $(echo "$(cat hello_multiple | wc -c)/$(cat log_compress | head -n 2 | tail -n 1)" | bc -l | cut -c 1-5):1"
echo "hello_multiple_i: $(echo "$(cat hello_multiple_i | wc -c)/$(cat log_compress | tail -n 1)" | bc -l | cut -c 1-5):1"

# Step 11: Analyse the results
# ...

#Exercice 6

#!/bin/bash

# Create users
sudo useradd -m -p $(openssl passwd -1 passwd-client_1) client_1
sudo useradd -m -p $(openssl passwd -1 passwd-contributor_1) contributor_1
sudo useradd -m -p $(openssl passwd -1 passwd-contributor_2) contributor_2

# Create groups
sudo groupadd clients
sudo groupadd contributors

# Add users to their respective group
sudo usermod -a -G clients client_1
sudo usermod -a -G contributors contributor_1
sudo usermod -a -G contributors contributor_2

# Check the users and groups have been successfully created
getent passwd client_1
getent passwd contributor_1
getent passwd contributor_2
getent group clients
getent group contributors

# Create folder lika_project and give it appropriate permissions
sudo mkdir /likaproject
sudo chown :clients /likaproject
sudo chmod 750 /likaproject
sudo setfacl -m g:contributors:rw /likaproject

# Check folder permissions
ls -l / | grep likaproject

# Change user and become as a client, then try deleting the folder
su client_1
rm -rf /likaproject

# Change user and become as a contributor, then try deleting the folder
su contributor_1
rm -rf /likaproject

# Check who is the current user
whoami

