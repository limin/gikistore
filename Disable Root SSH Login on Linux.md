One of the biggest security holes you could open on your server is to allow directly logging in as root through ssh, because any cracker can attempt to brute force your root password and potentially get access to your system if they can figure out your password.

It’s much better to have a separate account that you regularly use and simply sudo to root when necessary. Before we begin, you should make sure that you have a regular user account and that you can su or sudo to root from it.

To fix this problem, we’ll need to edit the sshd_config file, which is the main configuration file for the sshd service. The location will sometimes be different, but it’s usually in /etc/ssh/. Open the file up while logged on as root.
```
    vi /etc/ssh/sshd_config
```
Find this section in the file, containing the line with “PermitRootLogin” in it.
```
    #LoginGraceTime 2m
    #PermitRootLogin no
    #StrictModes yes
    #MaxAuthTries 6
```
Make the line look like this to disable logging in through ssh as root.
```
    PermitRootLogin no
```
Now you’ll need to restart the sshd service:
```
    /etc/init.d/sshd restart
```
Now nobody can brute force your root login, at least.