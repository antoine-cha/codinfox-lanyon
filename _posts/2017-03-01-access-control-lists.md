---
layout: post
title: access-control-lists.md
author: Antoine
tags: [linux]
---
## Access Control Lists (ACLs)

Example:
```Shell
$ ll /dev/dvb/adapter0/demux0

crw-rw----+ 1 root video 212, 0 févr. 27 09:54 /dev/dvb/adapter0/demux0      

```

The `+` here means that the file has advanced permissions called ACLs (access control list).

### Listing ACLs
To display them:
```Shell
$ getfacl /dev/dvb/adapter0/demux0

# file: dev/dvb/adapter0/demux0
# owner: root                  
# group: video                 
user::rw-                      
user:antoine:rw-               
group::rw-                     
mask::rw-                      
other::---                     
```
This explains that `antoine` could read the DVB adapter while not being in the group video.


### Modifying ACLs

To modify permissions:
```Shell
# For a user
getfacl -m u:<user>:<permissions> <file>
# For a group
getfacl -m g:<group>:<permissions> <file>
```
To remove permissions:
```Shell
# For a user
getfacl -x u:<user> <file>
# For a group
getfacl -x g:<group> <file>
```

Example:
```Shell
$ sudo setfacl -m u:tonio:r /dev/dvb/adapter0/demux0

$ getfacl /dev/dvb/adapter0/demux0

# file: demux0
# owner: root
# group: video
user::rw-
user:antoine:rw-
user:tonio:r--
group::rw-
mask::rw-
other::---

$ sudo setfacl -x u:tonio /dev/dvb/adapter0/demux0

$ getfacl /dev/dvb/adapter0/demux0

# file: dev/dvb/adapter0/demux0
# owner: root
# group: video
user::rw-
user:antoine:rw-
group::rw-
mask::rw-
other::---
```
