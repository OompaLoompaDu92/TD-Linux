#!/bin/bash

#Exercice 1 

# Set variables for connection
server_address="serveur Matteo ADDRESS"
username="Matteo"
private_key_path="/path/to/your/private/key.pem"

# Change permissions on private key file
chmod 400 "$private_key_path"

# Connect to remote instance via SSH
ssh -i "$private_key_path" "$serveur_Matteo_ADDRESS"

# Rename private key file to a hidden file
mv "$private_key_path" "${private_key_path}.hidden"


#Exercice 2


touch test_to_remote_instance.txt
touch test_from_remote_instance.txt
exit
scp -i /path/to/private_key test_to_remote_instance.txt username@remote_instance_public_ip:~
scp -i /path/to/private_key username@remote_instance_public_ip:~/test_from_remote_instance.txt .
#!/bin/bash

# check if file path is provided
if [ $# -eq 0 ]; then
    echo "Please provide the path of the file to send"
    exit 1
fi

# send file to remote instance
scp -i /path/to/private_key "$1" username@remote_instance_public_ip:~

#!/bin/bash

# check if file path is provided
if [ $# -eq 0 ]; then
    echo "Please provide the path of the file to get"
    exit 1
fi

# get file from remote instance
scp -i /path/to/private_key username@remote_instance_public_ip:"$1" .

./scp_to_remote_instance.sh /path/to/local/file

./scp_from_remote_instance.sh ~/remote_file
