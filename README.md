# ansible-role-thinlinc-server-prereq
Prepare servers to be able to install ThinLinc using https://github.com/cendio/ansible-role-thinlinc-server.

Installed Thinlinc 4.14.0 on virtual machines:
 - openSUSE Tumbleweed (20220202)
 - Rocky Linux 8.5 (Green Obsidian, https://rockylinux.org/)
 - Linux Mint 20.3 (Una) 

Installed Thinlinc 4.14.0 on containers:
 - debian-11 (bullseye)
 - opensuse-15.3-default
 - ubuntu-18.04-standard (bionic)
 - ubuntu-20.04-standard (focal)
 - debian-10-standard (buster)
 - almalinux-8.5 (Arctic Sphynx, https://almalinux.org/)
 - centos-8-stream

Not yet tested virtual machines:
 - SUSE Linux Enterprise Server 15 ( Requires extra repos, see tasks/pre_suse.yml )
 
Playbook Variables:
```yaml
  install_xfce: false  # Change to true if you want to install Xfce
```

Example playbook:

```yaml
  ---
  - hosts: all
    gather_facts: false
  
    roles:
      - { role: ansible-role-thinlinc-server-prereq, install_xfce: true }
      - { role: ansible-role-thinlinc-server, thinlinc_accept_eula: "yes", thinlinc_server_bundle: "/local/artifactory/tl-4.14.0-server.zip" }
```
