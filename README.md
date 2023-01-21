# Broadcast-Storm-Detection-using-Ansible

This Ansible program is designed to detect broadcast storms in a network. A broadcast storm occurs when a network device repeatedly sends broadcast packets, causing a flood of traffic that can bring down the entire network.

The program uses the `netstat` command to gather information about network interfaces and their traffic statistics. The output is then parsed using `awk` to extract the interface name and the number of broadcast packets. The result is filtered to remove interfaces with no broadcast traffic.

The parsed data is then passed to a query using `json_query` filter, which filters out interfaces with broadcast traffic below a threshold (1000 in this case). The interfaces with high broadcast traffic are stored in a variable `high_broadcast_interfaces`.

The final task in the playbook will check if there is any interface with high broadcast traffic in the `high_broadcast_interfaces` variable and if yes, it will alert with a message.

To run the program, you need to have Ansible installed on your system.
You can run the playbook by using the command `ansible-playbook -i <hosts-file> <playbook-file.yml>`

## Note: This is a basic example and can be modified to suit specific requirements. Also, it might not work as is as it is not tested.

## Prerequisites
- Ansible should be installed on the machine from which you are running the playbook
- You should have the ssh access to the hosts on which you want to run this playbook
- You should have a hosts file ready with the inventory of the hosts on which you want to run this playbook.

## Configuration
- You can modify the threshold value to suit your requirements.
- You can also modify the shell command to use other tools like tcpdump or snmp to gather network statistics.
- You can also modify the playbook to take the threshold value as a variable and pass it at runtime.

## Output 
- If there is any interface with high broadcast traffic, the playbook will output the message "High broadcast traffic detected on interface <interface-name>"
- If there is no high broadcast traffic, the playbook will not output anything.

# Warning
- Running this playbook on a production environment without testing it in a lab environment is not recommended.
- This is just an example and it might not work as is.
- Make sure you understand the impact of this playbook before running it.
