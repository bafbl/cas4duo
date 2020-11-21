DUO-Only CAS
=======================

A CAS server/container that accepts any username/password and then initiates DUO validation. 
This essentially makes this a device-/duo-only login service.

# Versions

- CAS `6.3.x`
- JDK `11`

# Overview

To build the project, use:

```bash
docker build -t cas4duo .
```

To Launch the CAS Server

```bash
docker run -e ... --rm -p 8080:8080 cas4duo
```

Browse to [http://localhost:8080/cas](http://localhost:8080/cas). Usernames must match a Duo username, but the password is irrelevant. 

# Configuration

- The `etc` directory contains the configuration files and directories that need to be copied to `/etc/cas/config`.

