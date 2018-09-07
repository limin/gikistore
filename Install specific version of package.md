# Check the available versions of packages
```
$ apt-cache madison nodejs
    nodejs | 10.8.0-1nodesource1 | https://deb.nodesource.com/node_10.x bionic/main amd64 Packages
    nodejs | 8.10.0~dfsg-2 | http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

$ apt-cache policy nodejs
nodejs:
  Installed: (none)
  Candidate: 10.8.0-1nodesource1
  Version table:
     10.8.0-1nodesource1 500
        500 https://deb.nodesource.com/node_10.x bionic/main amd64 Packages
     8.10.0~dfsg-2 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

# Simulate the installation
```
$ sudo apt-get install -s nodejs=8.10.0~dfsg-2
```

# Install a specific version of a package
```
$ sudo apt-get install nodejs=8.10.0~dfsg-2 -V
```

# List the installed packages with the versions
```
$ dpkg -l | grep nodejs
ii  nodejs                                     8.10.0~dfsg-2                               amd64        evented I/O for V8 javascript
ii  nodejs-doc                                 8.10.0~dfsg-2                               all          API documentation for Node.js, the javascript platform
```
