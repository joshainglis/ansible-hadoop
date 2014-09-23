Cluster deployment
=================

### Requirements
 * Ansible 1.6
 * centOS 6.5

This ansible playbook will deploy a hadoop CDH4 cluster in HA mode plus elasticseach.

### Installation

edit the file `hosts` and `group_vars/all`

To run Ansible:

```sh
./deploy.sh
```

To e.g. just install ZooKeeper, add the `zookeeper` tag as argument.
available tags: 
 * configuration
 * elasticsearch
 * hadoop
 * hbase
 * hive
 * ntp
 * zookeeper
...

```sh
./site.sh zookeeper
```
