# Snort
Network Monitoring 
Step 1: Setup and Installation
sudo apt update
sudo apt install -y snort 
Step 2: Create a Custom NIDS Rule
sudo nano /etc/snort/rules/local.rules 
Add a Brute-Force Rule: Add the following rule to the bottom of the file. This rule alerts if it sees
more than 5 connection attempts to the SSH port (22) from the same source IP within 60 seconds.
Step 3: Test the Rule
1. Start Snort: Run Snort in console mode to watch for alerts in real-time. Replace enp0s3 with
your network interface.
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3
2. Install an SSH Server: To attack something, you need an SSH server running on your Snort
VM. sudo apt install -y openssh-server
3. Perform the Attack: From another machine on the same network (your host machine or
another VM), use a tool like Hydra to simulate a brute-force attack. You'll need a dummy
password list. # Create a small password list
echo "password123\nadmin\nroot\n123456\nqwerty" > pass.txt
Verify the Alert: Watch the console where Snort is running. After a few seconds of the Hydra
attack, you will see the alert message "SSH Brute-Force Attempt Detected" appear multiple
times.
