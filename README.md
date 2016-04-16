# Vagrant environment for Wordpress

This project provides a virtual environment for Wordpress development using
[Vagrant](https://www.vagrantup.com).

## What's in the box?

When you start Vagrant, this environment will provide the following tools
that can be useful when developing for Wordpress:

- Git
- cURL
- MySQL
  * Username: `root`
  * Password: empty
- SQLite
- nginx
- PHP
- PHP-FPM
- APC
- PEAR
- XDebug
- Memcached
- node
- gulp

Additionally, it will create a MySQL database called `wordpress`.

## Usage and requirements

### Ansible

[Ansible](http://ansible.com) is used to provision the virtual machine, so you
must have that installed. Follow the
[installation instructions](http://docs.ansible.com/intro_installation.html#installation).

### Usage

Installation is as easy as cloning a GitHub project:

```
$ cd your-symfony-project
$ git clone https://github.com/kleiram/vagrant-symfony.git
```

Vagrant will search the project code in the `../wordpress` directory.

After the project is added, you can start the environment like this:

```
$ vagrant up
```

Starting the VM might take some time, since it will download the entire box
and additional applications/library. When the VM is done setting up, point
your browser towards [http://192.168.33.10](http://192.168.33.10) and there you
have it.

#### Note

If you're using Windows, you have to modify the `Vagrantfile` a little bit to
make it all work (since Windows doesn't support NFS). Replace the following
lines in the Vagrantfile:

```ruby
config.vm.synced_folder ".",  "/vagrant", id: "vagrant-root", :nfs => true
config.vm.synced_folder "../wordpress", "/var/www", id: "application",  :nfs => true
```

with:

```ruby
config.vm.synced_folder ".",  "/vagrant", id: "vagrant-root"
config.vm.synced_folder "../wordpress", "/var/www", id: "application"
```

## License

```
Copyright © 2016, Nicolas Djambazian <nicolas@djambazian.fr>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

The Software is provided “as is”, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders X be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the Software.
Except as contained in this notice, the name of the Nicolas Djambazian shall not be used in advertising or otherwise to promote the sale, use or other dealings in this Software without prior written authorization from the Nicolas Djambazian.
```
