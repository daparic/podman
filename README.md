
```
podman run --name license-server --user root:root --network=host -v /opt/parasoft/license-server-data/:/usr/local/parasoft/license-server/data -v /run/user/1000/podman/podman.sock:/var/run/docker.sock -v parasoft-volume:/mnt/parasoft -d parasoft/lss:latest
```
