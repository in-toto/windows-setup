# windows in-toto

In this repository you will find a Vagrant + ansible set of config files that
can help you provision a windows environment for in-toto development.

## Usage

With vagrant and ansible installed (you probably need python-pywinrm) using
your package manager, you can simply run:

```sh
$ vagrant up
```

This command should fetch a windows vm, start it and then run the ansible
playbook on it. The ansible playbook does basically the following:

1. Install python
2. Install git
3. Install tox
4. Cloning in-toto and running the tests using tox

After running vagrant up, you can log into the machine using:

```sh
$ vagrant ssh
```

This way you can inspect things manually, modify the in-toto source tree,
install packages using chocolatey, etc.

That's it!

## Other useful commands

### Hard-resetting everything

You can reset everything by running:

```sh
$ vagrant destroy && vagrant up
```

In case you want to start from scratch.


### Pointing to a different host

You can use the provided ansible playbook to provision on a different host by
modifying the inventory file and changing the default host to something else.

### Using a different windows VM

You can change the chosen box in the vagrantfile by editing the
`config.vm.box`. You can always search in [vagrant
cloud](https://app.vagrantup.com/boxes/search) to find alternative boxes.

### Debugging the box if winrm is failing

If you can't connect to the vm you can use a vrdp (such as `rdesktop-vrdp`)
tool to connect to the host and verify everything is working on the vm. if you
are using VirtualBox, The virtualbox GUI also allows you to attach to the
"monitor" of the running vm.
