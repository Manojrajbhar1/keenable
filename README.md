# LDAP

Requirement

1. Install and configure Ldap 389 DS in the containerised platform with persistence storage

2. Create organisation [keenable.in](http://keenable.in/)

3. Create OU [Dev,Support,POC, Document, Observability]

4. Create group Admin,Support

5. Create custom attribute

Environment Info

**Server Info:-**

Os version

NAME="Ubuntu"

VERSION="20.04.6 LTS (Focal Fossa)"

podman version 3.4.2

**Client Info:-**

NAME="Ubuntu"

VERSION="20.04.6 LTS (Focal Fossa)"

Ldap version:- 3

Apache Directory Studio version:- 2.0.0.v20210717-M17

**List of Tools:-**

1. Podman
2. Ldap
3. Apache Directory Studio

**LDAP**:- The Lightweight Directory Access Protocol is a communication protocol used to access directory servers and is used to store, update and retrieve data from a directory structure.

**Command for the setup or configuration**

1. Create Bash script for create Pod and container

cat  ldap.sh

Bash script :-

```bash
#!/bin/bash
#create pod with name ldap389
podman pod create --name ldap389 --publish 3389:3389 --publish 3636:3636
#create container
podman run -dt\
--pod ldap389 \
--name 389ds-ldap \
-v ~/389ds/data:/data \
-e DS_SUFFIX=dc=keenable, dc=in \
-e DS_DM_PASSWORD=<password> \
docker.io/389ds/dirsrv
```
