Using the terminal.
^^^^^^^^^^^^^^^^^^

- First, if your user has sudo privileges, you must enable its NOPASSWD option. Otherwise, sudo will ask for a password even when you don't have one, and won't accept an empty password.
  To do so, open the sudoers configuration file with sudo visudo, and add the following line to the file, replacing david with your username:
  
  david ALL=(ALL) NOPASSWD:ALL
  
  Close the editor to apply the changes, and test the effect on sudo in a new terminal.
  
- Delete the password for your user by running this command:
  
  sudo passwd -d `whoami`
  
If you ever get prompted for a password, just type enter and it should work. I've tested this answer with LightDM, the lock screen, sudo, gksu and it works, but there's one more step to get it to work with pkexec (thanks muru).
