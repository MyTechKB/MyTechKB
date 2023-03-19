---
title: "Docker Commands"
date: 2022-01-19T22:22:53-06:00
draft: false
category: Commands
tags:
- Docker
---

## Start and stop all containers

{{< highlight bash >}}
# Stop all containers
docker stop $(docker ps -a -q)
# Start all containers
docker start $(docker ps -a -q)
{{< / highlight >}}


## Remote docker access

You can configure Docker to accept remote connections. This can be done using the docker.service systemd unit file for Linux distributions using systemd. Or you can use the daemon.json file, if your distribution doesn’t use systemd. Configuring Docker to listen for connections using both the systemd unit file and the daemon.json file causes a conflict that prevents Docker from starting.

--Configuring remote access with systemd unit file
-Use the command sudo systemctl edit docker.service to open an override file for docker.service in a text editor.
-Add or modify the following lines, substituting your own values.

[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://127.0.0.1:2375

-Save the file.
-Reload the systemctl configuration.
  sudo systemctl daemon-reload
-Restart Docker.
  sudo systemctl restart docker.service
-Verify that the change has gone through.
  sudo ss -lntp | grep dockerd

To disable:
sudo mv /etc/systemd/system/docker.service.d/override.conf /etc/systemd/system/docker.service.d/override.old
sudo systemctl daemon-reload
sudo systemctl restart docker.service


## Create a Docker Swarm

{{< highlight bash >}}
docker swarm init
# Will give you join command which includes token and ip_address:port
docker swarm join --token [token] [ip_address]:[port]
# To get a join command for a worker
docker swarm join-token worker
# To get a join command for a manager
docker swarm join-token manager
# Check swarm with
docker node ls
{{< / highlight >}}

