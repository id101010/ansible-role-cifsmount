ansible-role-cifs
=================

Mount any cifs network share and create a persistent config.

Requirements
------------

An available cifs network share.

Role Variables
--------------

```yaml
# share configs, this can be a list of shares
cifs_connections:
  - name: movies
    user: testuser
    pass: changeme
    mountpoint: '/movies'
    domain: mymediaserver.com
    share: 'O:\\some\weird\windows\share'
  - name: pictures
    user: testuser
    pass: changeme
    mountpoint: '/pictures'
    domain: mymediaserver.com
    share: 'O:\\some\weird\windows\share'

# local
cifs_credsfile_path: '/root'
cifs_credsfile_mode: '0600'
cifs_credsfile_owner: root
cifs_mount_root_path: '/mnt'
cifs_dir_mode: '0777'
cifs_file_mode: '0777'
cifs_persist_config: false
```

Dependencies
------------

None.

Example Playbook
----------------

An example playbook which installs all necessary packages and configures
all the shares defined in the list `cifs_connections`.


```yaml
---

- name: cifs test play
  hosts: all
  vars:
    cifs_persist_config: false
    cifs_connections:
      - name: movies
        user: testuser
        pass: changeme
        mountpoint: '/movies'
        domain: mymediaserver.com
        share: 'O:\\some\weird\windows\share'
      - name: pictures
        user: testuser
        pass: changeme
        mountpoint: '/pictures'
        domain: mymediaserver.com
        share: 'O:\\some\weird\windows\share'
  roles:
    - cifs
```


License
-------

GPLv3

Author Information
------------------

Aaron (aaron@0x29a.ch)
