# labdeploy

This ansible playbook deploys Arista veoslab instances in a KVM hypervisor host, veoslab interface links are setup with openflow rules in Open Virtual Switch.

Playbook tasks are:

* Copy VM instances disks (qcow2 files, one for each VM)
* Create VMs in KVM hypervisor (definition based in a XML template)
* Setup EOS config for each VM based in a jinja2 template (including configurable systemid, management ip, usernames or whatever you want to include)
* Start VMs instances
* Setup links using openflow rules (with this LLDP, lag, and other L2 protocolos work fine)

In the event that you only want to setup the links (for instance because VMs are already setup from previous session) you can call ansible-playbook with --tags links

The directory structure in your ansible control host is:

```
$ tree
.
├── ansible.cfg
├── create.yml
├── files
│   └── disks
│       └── VEOSLAB4253M.qcow2
├── inventory
├── templates
│   ├── startup-config
│   └── VEOSLAB.xml
└── vars
    └── topo.yml

4 directories, 7 files
```

You can download veoslab qcow2 images from Arista support site.
