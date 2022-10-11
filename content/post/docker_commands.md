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

