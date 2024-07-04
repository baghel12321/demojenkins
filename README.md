#!/bin/bash

# Check if script is run as root
if [ "$(id -u)" -ne 0 ]; then
    echo "Please run this script as root or with sudo."
    exit 1
fi

# Loop to create 10 users
for i in {1..10}; do
    username="user$i"
    useradd -m -d /home/$username -s /bin/bash $username
    
    # Set a default password for the user (change 'password123' to a more secure one or ask for input)
    echo "$username:password123" | chpasswd
    
    echo "Created user: $username"
done

echo "All users created successfully."

