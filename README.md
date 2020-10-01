# RPM builder for latest HAProxy 2.2 (CentOS 7) with default syslog

:white_check_mark: [Latest 2.2.4 2020/09/30](https://github.com/philyuchkoff/HAProxy-2-RPM-builder/releases/tag/2.2.4)

Perform the following steps on a build box as a regular user:

## Install Prerequisites:

    sudo yum groupinstall 'Development Tools'

## Checkout this repository
    cd /opt
    sudo git clone https://github.com/philyuchkoff/HAProxy-2-RPM-builder.git
    cd ./HAProxy-2-RPM-builder
    sudo git checkout master

## Build:

### Without Lua:

    sudo make
    
### With Lua:

    sudo make USE_LUA=1

### With Prometheus module:

    sudo make USE_PROMETHEUS=1

### Without sudo for YUM:

    sudo make NO_SUDO=1

Resulting RPM will be stored in 

    /opt/HAProxy-2-RPM-builder/rpmbuild/RPMS/x86_64/

## Build using Docker:

    sudo make run-docker

Resulting RPM will be stored in 

    ./RPMS/


### Install RPM:

    sudo yum -y install /opt/HAProxy-2-RPM-builder/rpmbuild/RPMS/x86_64/haproxy-2.2.3-1.el7.x86_64.rpm
    

## Check after install:

    haproxy -v

Must be like this:

    HA-Proxy version 2.2.3
    

## :exclamation: If some not working:

Check SELINUX:

    sestatus

If SELINUX is enabled  - switch off this: open /etc/selinux/config and change to SELINUX в disabled

## Stats page

After install you can access a stats page **without** authenticating via the URL: `http://<YourHAProxyServer>:9000/haproxy_stats`
