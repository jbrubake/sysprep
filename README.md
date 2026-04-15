# packer-lxc

Configure a Fedora system to build [LXC](https://linuxcontainers.org/lxc/) containers using
[packer](https://developer.hashicorp.com/packer).

## Description

Install necessary system packages, configure system files and configure personal
files to allow creation of LXC containers using Packer. `packer-lxc` currently
supports only **Fedora**.

## Requirements

- None

## Role Variables

### User Variables

Name                    | Description                                         | Default        | Internal Name
----                    | -----------                                         | -------        | -------------
packer_lxc.id_start:    | Starting sub?id                                     | 524289         | packer_lxc__id_start
packer_lxc.id_num:      | Maximum sub?id                                      | 65536          | packer_lxc__id_num
packer_lxc.lxcbr:       | Name of LXC network bridge                          | lxcbr0         | packer_lxc__lxcbr
packer_lxc.max_lxc_if:  | Maximum interfaces a user can attach to LXC bridge  | 10             | packer_lxc__max_lxc_if
packer_lxc.users:       | List of users to configure                          | []             | packer_lxc__user
packer_lxc.bindir:      | Where to install tar(1) wrapper (absolute path)     | /usr/local/bin | packer_lxc__bindir
packer_lxc.user_bindir: | Where to install tar(1) wrapper (relative to $HOME) | .local/bin     | packer_lxc__user_bindir


### Internal Variables

Name                    | Description            | Value
----                    | -----------            | -----
packer_lxc__packages    | Packages to install    | ['lxc', 'lxc-templates', 'python3-lxc']
packer_lxc__tar_wrapper | Path to tar(1) wrapper | files/tar-packer-lxc-wrapper
packer_lxc__config_home | XDG_CONFIG_HOME        | ansible_env.XDG_CONFIG_HOME | d([ansible_env.HOME, '.config'] | path_join)

## Dependencies

- None

## Example Playbook

```
- hosts: workstation
  vars:
    packer_lxc:
      id_start: 50000
      id_num: 60000
      lxcbr: lxcbr0
      max_lxc_if: 10
      users:
        - foo
        - bar
      bindir: /usr/local/bin
      user_bindir: bin
  roles:
    - packer-lxc
```

## License

GPL Version 3.0 or later

## Author Information

Jeremy Brubaker [jbrubake@orionarts.io](mailto:jbrubake@orionarts.io)

