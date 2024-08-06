# Using Parasoft License Server in Podman

Here, the example utilizes the local user and group `dx`. Please replace `dx` with your corresponding local user and group identifier as needed.

## Setup folders
```
sudo mkdir /opt/parasoft
sudo chown dx:dx /opt/parasoft/
mkdir /opt/parasoft/license-server-data/
```

## Install `podman`
```
sudo apt install podman
```

## Create a persistent volume:
```
podman volume create parasoft-volume
```

## Additional system-related configuration:
```
systemctl --user enable podman.socket
systemctl --user start podman.socket
systemctl --user status podman.socket
```

## Create `parasoft/lss` as a podman container:
```
podman run --name license-server --user root:root --network=host -v /opt/parasoft/license-server-data/:/usr/local/parasoft/license-server/data -v /run/user/1000/podman/podman.sock:/var/run/docker.sock -v parasoft-volume:/mnt/parasoft -d docker.io/parasoft/lss:latest
```

[![Actual Session Replay](https://asciinema.org/a/udYP5Jh4ahd8U2WqeB5JUx9xM.svg)](https://asciinema.org/a/udYP5Jh4ahd8U2WqeB5JUx9xM)

## Additional References
- https://hub.docker.com/r/parasoft/lss
- https://linuxhandbook.com/autostart-podman-containers/
