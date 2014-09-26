Cluster deployment
=================

### Requirements
 * Ansible 1.6+
 * CentOS 6.5

This ansible playbook will deploy a hadoop CDH4 cluster in HA mode.
It will also deploy Elasticsearch and spark

### Installation

edit the files:
 * `hosts` : to determine where to install services
 * `group_vars/all`: to change/add  more configuration parameters (ex: hdfs path, spark port etcetc)

Also, due to a restriction with Github files size, you will have to copy jdk and spark archive to:
 * oracle JDK 7: `roles/common/files/dependencies/jdk-7u67-linux-x64.rpm`
 * spark Pkg: `roles/spark_configuration/files/spark-1.1.0-bin-cdh4.tgz`

To run with Ansible:

```sh
./deploy.sh
```

To e.g. just install ZooKeeper, add the `zookeeper` tag as argument.
available tags: 
 * elasticsearch
 * hadoop
 * ntp
 * zookeeper
 * slaves
 * spark
 * ...

```sh
./deploy.sh zookeeper
```
