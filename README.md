# Ansible Role: jeffhung.spark

Ansible playbook for installing Spark on CentOS/Debian Linux


## Installing

Install this playbook:

	ansible-galaxy install jeffhung.spark

## Testing with Vagrant

After [installing](#installing) this playbook, you could create a working
folder with the following `Vagrantfile` and `site.yml` in folder root, to run
vagrant box locally:

`Vagrantfile`:

```
Vagrant.configure("2") do |config|
  config.vm.box = "centos/6"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024 # Spark need much larger memory
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
  end
	# spark console service port:
  config.vm.network :forwarded_port, host: 8080, guest: 8080
end
```

`site.yml`:

```
- hosts: default
  roles:
		- jeffhung.spark
```

Try to invoke `spark-shell`:

```
$ vagrant ssh
Last login: Mon Mar  6 06:17:02 2017 from 10.0.2.2
[vagrant@cattools-lab ~]$ spark-shell --version
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 1.6.2
      /_/

Type --help for more information.
[vagrant@cattools-lab ~]$
```


## Role Variables

### `spark_version`

Default: `1.6.2`

Set which Spark version to use.

Could be:

* `1.5.2`
* `1.6.1`
* `1.6.2`
* `2.0.0`
* `2.1.0`

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

