# Ansible Haddop
**Need Help?:** [Issues Tracking](https://github.com/NFLabs/ansible-hadoop/issues) | [acorbacho@nflabs.com](mailto:acorbacho@nflabs.com) <br/>
**Contributing:** [Contribution Guide](https://github.com/NFLabs/ansible-hadoop/blob/master/CONTRIBUTING.md)<br/>
**License:** [Apache 2.0](https://github.com/NFLabs/ansible-hadoop/blob/master/LICENSE)


Ansible Haddop is a playbook that help you to deploy a new Hadoop and Spark cluster.


The playbooks are designed to deploy a Hadoop cluster on a CentOS 6 or RHEL 6 environment using Ansible. The playbooks can:

 1.  Deploy a fully functional Hadoop cluster with HA and automatic failover. With Zookepper and Apache Spark.
 2. Deploy additional nodes to scale the cluster.


## Requirements
 * Ansible 1.6+
 * CentOS 6.5+ or RedHat servers

## Configuration

edit the files:
 * `hosts` : to determine where to install services
 * `group_vars/all`: to change/add  more configuration parameters (ex: hdfs path, spark port etcetc)

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


#### Version
 * Hadoop (HDFS, Zookeeper, journal) : CDH4.7
 * Elasticsearch : 1.3.4
 * Spark : 1.1.0
 * Java : 1.7 from oracle
 * Nginx : 1.6.2

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

If you want just restart some services run:

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

