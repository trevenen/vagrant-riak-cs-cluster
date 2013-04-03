# Vagrant Riak CS Cluster

This is a Vagrant project powered by Chef to bring up a local Riak CS cluster.
Each node can run either `Ubuntu 12.04` or `CentOS 6.3` 32-bit with `1536MB`
of RAM by default. If you want to tune the OS or node/memory count, you'll
have to edit the `Vagrantfile` directly.

## Configuration

### Install Vagrant

Download and install Vagrant via the
[Vagrant installer](http://downloads.vagrantup.com/tags/v1.0.7).

**Note**: It is necessary, at present, to install Vagrant 1.0.7 due to a
compatibility issue.

### Clone repository

``` bash
$ git clone https://github.com/basho/vagrant-riak-cs-cluster.git
$ cd vagrant-riak-cs-cluster
```

### Launch cluster

``` bash
$ RIAK_CS_CREATE_ADMIN_USER=1 vagrant up
```

### Test cluster

``` bash
$ s3cmd -c ~/.s3cfgfasttrack --configure
```

There are 4 default settings you should change:

* **Access Key** - Replace with value next to `Riak CS Key` in the Chef
  provisioning output.
* **Secret Key** - Replace with value next to `Riak CS Secret` in the Chef
  provisioning output.
* **Proxy Server**: `localhost`
* **Proxy Port**: `8080`

``` bash
$ s3cmd -c ~/.s3cfgfasttrack mb s3://test-bucket
```

## Vagrant boxes

The Vagrant boxes used in this project were created by
[Veewee](https://github.com/jedi4ever/veewee/). To view the Veewee definitions,
please follow the links below:

* [opscode-centos-6.3](https://github.com/opscode/bento/tree/master/definitions/centos-6.3-i386)
* [opscode-ubuntu-12.04](https://github.com/opscode/bento/tree/master/definitions/ubuntu-12.04-i386)

## Erlang template helper

In order to set the appropriate Erlang data types for attributes, please use
the following methods provided by `erlang_template_helper`:

* `to_erl_string`
* `to_erl_binary`
* `to_erl_tuple`
* `to_erl_list`
