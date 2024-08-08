# Prometheus_Exporter_Docker

[cAdvisor](https://github.com/google/cadvisor) is a running daemon that collects, 
aggregates, processes, and exports information about running containers. 
Specifically, for each container it keeps resource isolation parameters, 
historical resource usage, histograms of complete historical resource usage and network statistics. 
This data is exported by container and machine-wide

## How to run cAdvisor

```SH
    git clone https://github.com/HornaHomeLab/Prometheus_Exporter_Docker.git \
    && cd ./Prometheus_Exporter_Docker \
    && docker compose up -d --force-recreate
```

## Configure default Docker metrics on Linux Host
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