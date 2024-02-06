# Name

sysprep - prepare your system to create Packer LXC containers

# Synposis

**sysprep** *[OPTION]*

*(*`sysprep` *must be run from its directoy to have access to its supporting files.)*

# Description

    Install necessary system packages, configure system files and configure personal files to allow creation of LXC containers using Packer. `sysprep` currently supports only **Fedora**.

    `sysprep` has nothing to do with the MS Windows `sysprep` tool. I just found the name appropraite and mildly humorous.

## Options

**-d** set Ansible debug output to sane settings

**-b [NAME]** lxc bridge interface (default = lxcbr0)

**-n [NUM]** number of interfaces to allow the user (default = 10)

**-v** display version information

**-h** display this help

# Author

Jeremy Brubaker [jbrubake@orionarts.dev](mailto:jbru362@gmail.com)

