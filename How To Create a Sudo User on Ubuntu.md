## Steps to Create a New Sudo User

### Log in to your server as the root user.
```
ssh root@server_ip_address
```
### Use the adduser command to add a new user to your system.

Be sure to replace username with the user that you want to create.
```
adduser username
```
### Set and confirm the new user's password at the prompt. A strong password is highly recommended!

    Set password prompts:
		Enter new UNIX password:
		Retype new UNIX password:
		passwd: password updated successfully

### Follow the prompts to set the new user's information. It is fine to accept the defaults to leave all of this information blank.

User information prompts:
Changing the user information for username
Enter the new value, or press ENTER for the default
    Full Name []:
    Room Number []:
    Work Phone []:
    Home Phone []:
    Other []:
Is the information correct? [Y/n]

### Use the usermod command to add the user to the sudo group.
```
usermod -aG sudo username
```
By default, on Ubuntu, members of the sudo group have sudo privileges.

### Test sudo access on new user account

Use the su command to switch to the new user account.
```
su - username
```
As the new user, verify that you can use sudo by prepending "sudo" to the command that you want to run with superuser privileges.
```
sudo command_to_run
```
For example, you can list the contents of the /root directory, which is normally only accessible to the root user.
```
sudo ls -la /root
```
The first time you use sudo in a session, you will be prompted for the password of the user account. Enter the password to proceed.

Output:
[sudo] password for username:

If your user is in the proper group and you entered the password correctly, the command that you issued with sudo should run with root privileges.
