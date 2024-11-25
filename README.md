# MeshSense Docker image

## Warnings

1) The actions in this repo will run every week, pulling the latest code from https://github.com/Affirmatech/MeshSense.
This repo has nothing to do with the original author, it just creates a containerized version of the MeshSense software.

2) I only build an `linux/amd64` image

## What is MeshSense
MeshSense is a simple, open-source application that monitors, maps and graphically displays all the vital stats of your area's Meshtastic network including connected nodes, signal reports, trace routes and more! 

Read more at https://github.com/Affirmatech/MeshSense

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

## Thanks
Thanks goes to `valentintintin` for his post how to build a docker image [here](https://github.com/Affirmatech/MeshSense/issues/8). I just optimized it a bit and making it available via this repo