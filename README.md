# Prometheus_Exporter_Docker

## Configure Docker Host on Linux
1. Modify `daemon.json` file.
- file should be located in one of the paths below
```
/etc/docker/daemon.json
/var/snap/docker/2915/config/daemon.json
```
To see the path to the config file check the service status.
- add following entry to the config file
```JSON
    {
        "metrics-addr" : "0.0.0.1:9323",
    }
```
- restart docker service.


```SH
    systemctl restart snap.docker.dockerd.service
```
If service was not found run command below to list all services:
```SH
    sudo systemctl list-units --type=service
```

- metrics should be available at `<ip_address>:9323/metrics`c