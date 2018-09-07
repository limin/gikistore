#### Create a new file: /etc/apt/sources.list.d/nodesource.list

You'll need to create this file with sudo, but when you create the file, put this inside it:
```sh
deb https://deb.nodesource.com/node_6.x xenial main
deb-src https://deb.nodesource.com/node_6.x xenial main
```

Then, save the file. (replace node_6.x with node_7.x or node_8.x, etc. for newer Node versions)

#### Download the GPG Signing Key from Nodesource for the repository. Otherwise, you may get NO_PUBKEY errors with apt-get update:
```sh
    curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -
```

#### Manually run sudo apt-get update.

This refreshes the data from the nodesource repo so apt knows a newer version exists.

If you get a NO_PUBKEY GPG error, then go back to Step 2

#### Check apt-cache policy nodejs output.
```sh
apt-cache policy nodejs
```
This is not done by the script, but you want to make sure you see an entry that says something like this in the output:

```
Version table:
  6.2.1-1nodesource1~xenial1 500
     500 https://deb.nodesource.com/node_6.x xenial/main amd64 Packages
  4.2.6~dfsg-1ubuntu4 500
     500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

If you do not see entries like this, and only see 4.2.6, start over. Otherwise, proceed.

#### Install the nodejs binary. Now that you have confirmed 6.x is available on your system, you can install it: 
```sh
sudo apt-get install nodejs
```

#### Check nodejs version, should now show v6.2.1 or similar on output (as long as it starts with v6. you're on version 6 then).
```sh
nodejs --version 
```


[reference](https://askubuntu.com/questions/786272/why-does-installing-node-6-x-on-ubuntu-16-04-actually-install-node-4-2-6)