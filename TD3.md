#!/bin/bash

#Exercice1 

# Display the list of files and folders at the root using ls -l
ls -l / 

# In a pipeline (using |), append a grep instruction to only display informations of bin
ls -l / | grep "bin"

# Append an awk instruction to only display the size of bin
ls -l / | grep "bin" | awk '{print $5}'

# Now rather extract the month, day and year of creation of the folder bin
ls -ld /bin | awk '{print $6,$7,$8}'

# Now rearrange the instruction to get the following output format : 2020-Oct-26 (from original data : Oct 26 2020)
ls -ld /bin | awk '{print $6"-"substr($1,1,3)"-"$2}' 

#Exercice 2

# Run the following command : curl https ://en.wikipedia.org/wiki/List_of_cyberattacks > cyberattacks.txt
curl https://en.wikipedia.org/wiki/List_of_cyberattacks > cyberattacks.txt

# Use grep to extract all the lines that contain the keyword "meta"
grep "meta" cyberattacks.txt

# Now only extract "meta" and the first following word. You might use grep options to enable the use of regex (Regular Expressions)
grep -o "meta [^ ]*" cyberattacks.txt

# Only extract the follwing word (but not the keyword "meta")
grep -oP "(?<=meta )[^\s]*" cyberattacks.txt

#Q5 faite pour voir les résultats

# Extract the tab title
grep -oP "<title>\K.*(?= - Wikipedia</title>)" cyberattacks.txt

# Make a list of cyber attacks based on section titles
grep -oP "<span class=\"mw-headline\".*>\K.*(?=</span>)" cyberattacks.txt
