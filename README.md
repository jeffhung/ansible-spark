# Ansible Role: jeffhung.spark

Ansible playbook for installing Spark on CentOS/Debian Linux

Install this playbook:

	ansible-galaxy install jeffhung.spark


## Role Variables

### `spark_version`

Default: `1.6.2`

Set which Spark version to use.

Could be:

* `1.5.2`
* `1.6.1`
* `1.6.2`
* `2.0.0`

### `spark_bundle_hadoop`

Default: `hadoop2.6`

Set which bundled prebuilt Hadoop to use.

Could be:

* `hadoop2.7`: pre-built for Hadoop 2.7 or later
* `hadoop2.6`: pre-built for Hadoop 2.6
* `hadoop2.4`: pre-built for Hadoop 2.4
* `hadoop2.3`: pre-built for Hadoop 2.3
* `without-hadoop`: pre-built with user-provided Hadoop (no hadoop bundled)

### `spark_environment`

Default: `devel`

Which environment to deploy.

Could be:

* `devel`: provision devel-time environment for developing with Spark
* `build`: provision build-time environment for packaging Spark

### `spark_cache_dir`

Cache directory for holding downloaded/generated files.

The default is `/vagrant/files` so cache persist between boxes.


## License

BSD

