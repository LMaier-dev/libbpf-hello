# Hello World with Bumblebee

## Prerequisites
- Install docker

## Install Bumblebee 
source: https://bumblebee.io/EN

```console 
curl -sL https://run.solo.io/bee/install | sh
```

Set the Environment Variable

```console
export PATH=$HOME/.bumblebee/bin:$PATH
```
To make this persist after reboot add it to .bashrc:
```console
sudo nano ~/.bashrc
```

Required permissions to push code into kernel:

```console
sudo setcap cap_sys_resource,cap_sys_admin,cap_bpf+eip $(which bee)
```

Fix docker permission denied:
```console
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

### Build:

```console
bee build hello-world.c hello-world:v1
```
#### Run local image:
```console
bee run hello-world:v1
```

### Push:
```console
bee tag hello-world:v1 <local-ip>:5000/hello-world:v1
bee push --plain-http <local-ip>:5000/hello-world:v1
```

### Pull/Run:
```console
bee pull --plain-http <local-ip>:5000/hello-world:v1
bee run <local-ip>:5000/hello-world:v1
```
replace `<local-ip>` with your privately hosted docker registry