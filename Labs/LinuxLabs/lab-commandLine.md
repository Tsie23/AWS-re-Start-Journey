# Linux Lab: Command Line

## Objective
- Run commands to gain knowledge of current system and current session
- Search and run previous bash commands

## Steps Taken
**Task 1**
Launched terminal using SSH to connect to an Amazon Linux EC2 instance
![alt text](<images/linuxCLI/Screenshot 2025-12-08 075716.png>)

**Task 2 - Run familiar commands**
1. From termial, entered *whoa* and press Tab(the auto complete feature displays the full *whoami* command)
![alt text](<images/linuxCLI/Screenshot 2025-12-08 075950.png>)

2. Press ENTER to display current user name
![alt text](<images/linuxCLI/Screenshot 2025-12-08 075950.png>)

3. Enter *hostname -s* and press ENTER to display a shortend version of computer's host name
![alt text](<images/linuxCLI/Screenshot 2025-12-08 075950.png>)

4. Enter *uptime -p* and press ENTER to display the uptime of the system in an easily readable format
![alt text](<images/linuxCLI/Screenshot 2025-12-08 075950.png>)

5. From terminal, enter *who -H -a* and press ENTER to display information about the users who are logged in and some additional information
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080015.png>)

6. Enter *TZ=America/New_York date* and press ENTER, then enter *TZ=America/Los_Angeles date*. These commands identify the date and time of alterante locations in the world
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080134.png>)

7. Enter *cal -j* in the terminal to see the Julian dates for the current month
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080212.png>)

8. Enter *cal -s* or *cal -m* commands to display alternate views of calendars. (The cal -s shows output of September from Sunday to Saturday, and the cal -m command gives the output from Monday through Sunday) 
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080339.png>)

9. Enter *id ec2-user* in the terminal and press ENTER, to see your unique ID and group information about specific user
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080441.png>)

**Task 3 - Improve workflow through history and search**
In this task, you attempt to ease your overall workload by reusing commands through search techniques, manual visualization of the bash history log, and reuse of the last command.
10. Enter *history* and press enter, check the output for the commands used in task 2. This command brings up the current bash history
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080533.png>)

11. Press CTRL+R to bring up a reverse history search. In the reverse history search feature of the terminal, enter *TZ* and press TAB. This command will bring up an old use of the date command that you can edit, using the arrow buttons to edit the command inline.
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080748.png>)

12. Enter *date* into the terminal and press ENTER, then enter !! and press ENTER. This step gives you the ability to rerun the most recent command.
![alt text](<images/linuxCLI/Screenshot 2025-12-08 080826.png>)

## Challenges
This lab did not present a lot of challenges, the only thing that gave me some trouble was getting the putty to connect and responsive during the lab. This was due to unstable internet connetion on my end. I remedied this by switching to mobile-hotspot.

## Takeaways
The Linux Bash terminal is an incredible and powerful environment for efficient workflow. Mastering core Linux commands and terminal shortcuts is an excellent way to being effective in cloud and systems administration.
