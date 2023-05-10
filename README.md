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

Required permissions to push code into kernel:

```console
sudo setcap cap_sys_resource,cap_sys_admin,cap_bpf+eip $(which bee)
```

### Build:

```console
bee build hello.c hello:v1
```


### Push:
```console
bee tag hello:v1 192.168.0.2:5000/hello:v1
bee push --plain-http 192.168.0.2:5000/hello:v1
```

### Pull/Run:
```console
bee pull --plain-http 192.168.0.2:5000/hello:v1
bee run 192.168.0.2:5000/hello:v1
```
