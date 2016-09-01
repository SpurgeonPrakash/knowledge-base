Cloud 9 IDE
===========

a web-based IDE

  * [Homepage](http://c9.io)
  * [Source](https://github.com/c9/core)


## Installation

### Oneliner

```
$ curl -sSL https://raw.githubusercontent.com/gbraad/oneliners/master/install_c9.sh | bash
```

### Ansible

```
$ curl -sSL https://github.com/gbraad/ansible-playbooks/raw/master/playbooks/install-c9sdk.yml -o install-c9sdk.yml`
$ ansible-playbook install-c9sdk.yml
```

### Docker

```
$ alias c9ide='docker run -it --rm -v `pwd`:/workspace gbraad/c9ide:c7'
$ cd ~/Projects/[something]
$ c9ide
```

Source: [GitLab](https://gitlab.com/gbraad/c9ide), [GitHub](https://github.com/gbraad/docker-c9ide), [Docker hub](https://hub.docker.com/r/gbraad/c9ide)


### Docker cloud

Create a new account, or re-use your Docker hub acount, at [Docker cloud](https://cloud.docker.com). Now open the [Node list](https://cloud.docker.com/node/cluster/list/) and Bring your own node. Setting up the first node is free of charge. It explaisn you how to deploy the docker cloud engine on a machine with a simple one-liner.

Now open the [Service list](https://cloud.docker.com/container/list/) and create a new service. Search Docker hub for `gbraad/c9ide`, and confirm with clicking Select. Below are the settings to can/need to be changed to allow you to start the C9 service on your own Docker cloud node.

#### General settings
Select the preferred flavor from the image selecter.

  * `c7` is based on CentOS 7
  * `f24` is based on Fedora 24
  * `u1604` is based on Ubuntu 16.04 (xenial)

If you want to know what is in these images, please see the source under the [Docker](#docker) header on this page.

_Note: Images with the `-devenv` suffix are based on my [devenv](htttp://github.com/gbraad/devenv) environment. Unless you know what you are doing, it is best to not use these._


#### Ports
```
Container port    Protocol   Published   Node port
8181              tcp        X           80
```

#### Environment variables
```
Name              Value
PASSWORD          pass
USERNAME          user
```

After clicking `Create & Deploy` you will be shown the endpoints Open the Service endpoint for `tcp/80` in your browser
(without the tcp:// prefix) and you will be shown a authentication prompt. User the parameters you set from the
Environment variables section and happy coding! Be aware that the first load of the page might take some time, as about 8.5M of data (JavaScript and CSS) need to be trasnferred.

_Note: Be sure to push your code out to a git repository or attach a volume to `/workspace`. Also, the container runs on port 80, which is unprotected (no TLS), which means that you should not work on super-secret code or use ultra-secure user/pass combination, as these will be littered all over the internet._