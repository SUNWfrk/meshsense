# MeshSense Docker image

## Warning

The actions in this repo will run every week, pulling the latest code from https://github.com/Affirmatech/MeshSense.
This repo has nothing to do with the original author, it just creates a containerized version of the MeshSense software.

I only build an `linux/amd64` image

## Installation
Create the directory where the app can save log and state files
```
mkdir /data/meshsense/data
```

Create the container
```
docker create \
  -v /data/meshsense/data:/root/.local/share/meshsense/
  -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket:ro \
  -p 5920:5920 \
  --restart unless-stopped \
  --name meshsense \
  ghcr.io/sunwfrk/meshsense:main
```

Start the container
```
docker start meshsense
```

## Use
Open [http://your_docker_host:5920](http://your_docker_host:5920)