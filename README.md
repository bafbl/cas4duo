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

Configure CAS to use Duo: create local-duo.env
```bash
DUO_SECRET_KEY=
# not very important for CAS that doesn't protect actual applications,
# but can be regenerated with dd if=/dev/urandom count=100 | shasum -a 256
DUO_APPLICATION_KEY=ef1bdd7b252c8388a382d9663aa9f492bf876d1eca12e31f34e07fd3e1b0f9a4
DUO_INTEGRATION_KEY=
DUO_API_HOST=
```

To Launch the CAS Server
```bash
docker run --env-file <local-duo.env>  --rm -p 8080:8080 cas4duo
```

Browse to [http://localhost:8080/cas](http://localhost:8080/cas). Usernames must match a Duo username, but the password is irrelevant. 

# Configuration

- The `etc` directory contains the configuration files and directories are be copied to `/etc/cas/config` in the containers.
- The messages can be adjusted with src/main/resources/messages.properties
