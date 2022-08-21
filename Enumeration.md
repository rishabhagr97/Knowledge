The purpose behind post-exploitation enumeration is to gather as much information about the system and its network. The exploited system might be a company desktop/laptop or a server. We aim to collect the information that would allow us to pivot to other systems on the network or to loot the current system.

# Linux Enumeration
## System Information
On a Linux system, we can get more information about the Linux distribution and release version by searching for files or links that end with `-release` in `/etc/`. Running `ls /etc/*-release` helps us find such files. Then we can read available files to find exact distribution.
## Important Files
Various files on a system can provide plenty of useful information. In particular, consider the following `/etc/passwd`, `/etc/group`, and `/etc/shadow`. Any user can read the files passwd and group. However, the shadow password file requires root privileges as it contains the hashed passwords. If you manage to break the hashes, you will know the user’s original password.

Similarly, various directories can reveal information about users and might contain sensitive files; one is the mail directories found at `/var/mail/`.

## Users Info
Files such as `/etc/passwd` reveal the usernames; however, various commands can provide more information and insights about other users on the system and their whereabouts.

You can show who is logged in using `who`.

To take things to the next level, you can use `w`, which shows who is logged in and what they are doing.

To print the real and effective user and group IDS, you can issue the command `id` (for ID).

Do you want to know who has been using the system recently? `last` displays a listing of the last logged-in users; moreover, we can see who logged out and how much they stayed connected.

