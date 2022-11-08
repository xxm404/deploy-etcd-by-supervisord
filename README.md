# Deploy etcd by supervisord

## Test env
- etcd version: 3.4.22
- supervisord version: 4.2.2
- system
```
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.5 LTS
Release:	18.04
Codename:	bionic
```

## Config
1. etcd bin and environment
```
# conf/etcd.ini
command=/home/work/etcd/bin/etcd
...
environment=ETCD_NAME="config-center-1",ETCD_DATA_DIR="data.etcd",ETCD_INITIAL_ADVERTISE_PEER_URLS="http://host1:2380",ETCD_LISTEN_PEER_URLS="http://host1:2380",ETCD_ADVERTISE_CLIENT_URLS="http://host1:2379",ETCD_LISTEN_CLIENT_URLS="http://host1:2379,http://127.0.0.1:2379",ETCD_INITIAL_CLUSTER="config-center-1=http://host1:2380,config-center-2=http://host2:2380,config-center-3=http://host3:2380",ETCD_INITIAL_CLUSTER_STATE="new",ETCD_INITIAL_CLUSTER_TOKEN="9d9d1b11-6de6-4a09-9793-63fca202e185"
```

## Use
Use control script to manage etcd task.
```
control [start|stop|restart] [program]

    examples:
        control start 
        control start etcd 
```
