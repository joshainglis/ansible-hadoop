Cluster deployment and Management
=================================

# Preface
The playbooks in this example are designed to deploy a Hadoop cluster on a CentOS 6 or RHEL 6 environment using Ansible. The playbooks can:

 1.  Deploy a fully functional Hadoop cluster with HA and automatic failover. With Zookepper, Spark and Elasticsearch.
 2. Deploy additional nodes to scale the cluster.


### Requirements
 * Ansible 1.6+
 * CentOS 6.5

### Configuration

edit the files:
 * `hosts` : to determine where to install services
 * `group_vars/all`: to change/add  more configuration parameters (ex: hdfs path, spark port etcetc)

Also, due to a restriction with Github files size, you will have to copy jdk and spark archive to:
 * oracle JDK 7: `roles/common/files/dependencies/jdk-7u67-linux-x64.rpm`
 * spark Pkg: `roles/spark_configuration/files/spark-1.1.0-bin-cdh4.tgz`


# Deploy a new cluster

To run with Ansible:

```sh
./deploy
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
./deploy zookeeper
```

### Services url

 * **HDFS**: master:50070 - *active*
 * **HDFS**: master2:50070 - *standby*
 * **Spark Master**: master:4242
 * **Spark Master2**: master2:4242
 * **Elasticsearch**: eshost:9200

# Restart service or cluster

restart all services run 
```sh
./restart
```

If you want to just restart some service run:
Simply run 
```sh
./restart serviceName
```

List of service that can be restarted
 * zookeepers
 * journalnodes
 * elasticsearch
 * namenodes
 * datanodes
 * sparkmasters
 * sparckworkers

#### License
Licensed under the [Apache License, Version 2.0](https://github.com/NFLabs/cluster-deployment/blob/master/LICENSE).
