#!/bin/bash

curl -s https://opendomesday.org/api/1.0/county/DB/places/ | grep -o '"id":[0-9]*' | grep -o '[0-9]*'

#Exercice 1.3

#!/bin/bash

# Get list of place ids in Derbyshire
ids=$(curl -s https://opendomesday.org/api/1.0/county/DB/places/ | grep -o '"id":[0-9]*' | grep -o '[0-9]*')

# Loop through ids and extract manor details
for id in $ids
do
  # Get place details
  place=$(curl -s https://opendomesday.org/api/1.0/place/$id/)
  
  # Extract manor ids from place details
  manor_ids=$(echo $place | grep -o '"manor_id":[0-9]*' | grep -o '[0-9]*')
  
  # Loop through manor ids and extract manor details
  for manor_id in $manor_ids
  do
    manor=$(curl -s https://opendomesday.org/api/1.0/manor/$manor_id/)
    echo $manor
  done
done

#Exercice 1.4

#!/bin/bash

# Get list of place ids in Derbyshire
ids=$(curl -s https://opendomesday.org/api/1.0/county/DB/places/ | grep -o '"id":[0-9]*' | grep -o '[0-9]*')

# Loop through ids and extract manor details
for id in $ids
do
  # Get place details
  place=$(curl -s https://opendomesday.org/api/1.0/place/$id/)
  
  # Extract manor ids from place details
  manor_ids=$(echo $place | grep -o '"manor_id":[0-9]*' | grep -o '[0-9]*')
  
  # Loop through manor ids and extract geld paid and number of ploughs
  for manor_id in $manor_ids
  do
    manor=$(curl -s https://opendomesday.org/api/1.0/manor/$manor_id/)
    geld=$(echo $manor | grep -o '"geld":[0-9]*' | grep -o '[0-9]*')
    ploughs=$(echo $manor | grep -o '"ploughs":[0-9]*' | grep -o '[0-9]*')
    echo "$id,$manor_id,$geld,$ploughs
  done
done



  
