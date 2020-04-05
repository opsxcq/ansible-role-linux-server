# Linux server role

Role that install a generic setup for a Debian linux:

 - Docker
 - Monitoring with prometheus
 - Kernel parameters
 - Basic tools and packages
 - Import of ssh keys, gpg keys and known hosts
 
# Example playbook

This is an example playbook


```yml
- hosts: my-server
  vars:
    hostname: "server.strm.sh"
    ip: "192.168.0.16"
    static_hosts: "{{ lookup('file', 'hosts') }}"
    gpg: "{{ lookup('file', 'gpg.pub') }}"
    ssh:
      authorized_keys: "{{ lookup('file', 'authorized_keys') }}"
      known_hosts: "{{ lookup('file', 'known_hosts') }}"
  tasks:
  - debug:
        msg: "Your other tasks here"
  roles:
    - opsxcq.linux_server
```

# Requirements file

```yml
- src: git+https://github.com/opsxcq/ansible-role-linux-server.git
  name: "opsxcq.linux_server"
```

# Tmux configuration

Tmux is added to this setup, but with a difference that it uses `Ctrl+A`, so you
can keep a tmux session (using `Ctrl+B`) locally connected to a tmux remotely.
