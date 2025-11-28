# Linux Lab: Command Line

## Objective
Run commands to gain knowledge of current system and current session
Search and run previous bash commands

## Steps Taken
**Task 1**
Launched terminal using SSH to connect to an Amazon Linux EC2 instance

**Task 2 - Run familiar commands**
1. From termial, entered *whoa* and press Tab(the auto complete feature displays the full *whoami* command)
2. Press ENTER to display current user name
3. Enter *hostname -s* and press ENTER to display a shortend version of computer's host name
4. Enter *uptime -p* and press ENTER to display the uptime of the system in an easily readable format
5. From terminal, enter *who -H -a* and press ENTER to display information about the users who are logged in and some additional information
6. Enter *TZ=America/New_York date* and press ENTER, then enter *TZ=America/Los_Angeles date*. These commands identify the date and time of alterante locations in the world
7. Enter *cal -j* in the terminal to see the Julian dates for the current month
8. Enter *cal -s* or *cal -m* commands to display alternate views of calendars. (The cal -s shows output of September from Sunday to Saturday, and the cal -m command gives the output from Monday through Sunday)
9. Enter *id ec2-user* in the terminal and press ENTER, to see your unique ID and group information about specific user

**Task 3 - Improve workflow through history and search**
In this task, you attempt to ease your overall workload by reusing commands through search techniques, manual visualization of the bash history log, and reuse of the last command.
10. Enter *history* and press enter, check the output for the commands used in task 2. This command brings up the current bash history
11. Press CTRL+R to bring up a reverse history search. In the reverse history search feature of the terminal, enter *TZ* and press TAB. This command will bring up an old use of the date command that you can edit, using the arrow buttons to edit the command inline.
12. Enter *date* into the terminal and press ENTER, then enter !! and press ENTER. This step gives you the ability to rerun the most recent command.

Lab Complete

## Challenges
- Struggled with the touch command, getting the right code to get the desired script output
- Solved by consulting AI for assistance with the touch command and automation

## Screenshot
![Challenge Instructions](images/Inst.png "Ictions")
After launching the Linux terminal with SSH, you log into terminal as EC2-User, and proceed to running commands.

![Bash GNU Nano Window](images/dow.png "TScript")
Run the command to open the GNU Nano window to add the touch script in Bash and save it, to automate the directory output when running the command in terminal.

![Terminal Output](images/put.png "TScript Output")

## Takeaways
Linux is
