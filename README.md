# Ansible Role for Finger2020

This is an Ansible role for managing the deployment of the
[Finger2020](https://github.com/michael-lazar/finger2020), a modern
[finger](https://en.wikipedia.org/wiki/Finger_protocol) daemon.

This role was put together quickly for my particular deployment and has only
been tested on Ubuntu 21.04.

Finger me via `finger josh@jbeard.co`.

See <https://rajivshah.com/Case_Studies/Finger/Finger.htm> for more information
about _finger_.

## What This Role Does

* Clones the Finger2020 Git repository for installation.
* Runs the `install.sh` script for installing Finger2020.
* Manages the Finger2020 configuration directory.
* Creates the _finger_ content - contact, project, plan
* Manages the service/socket

## Variables

Refer to [defaults/main.yml](defaults/main.yml).

### gopher_hosts

Required list of hosts to serve.

This sets the `-h` argument and creates content directories.

Default: _none_
Configures the Systemd service/socket

### finger_name

Required string that will represent the user's finger name. This can be any
arbitrary value and does not need to correspond to a real user on the system.

### finger_dir

Absolute path to the directory containing the finger2020 content files,
including the contact, plan, and project files.

Default: `/etc/finger`

### finger_sysconfig

Absolute path to the 'env' file for configuring finger2020

Default: `/etc/sysconfig/finger2020.env`

### finger_src_repo

The URL for a Git repository to download for the finger2020 installation

Default: https://github.com/michael-lazar/finger2020.git

### finger_src_ref

The Git ref (commit hash, branch, tag) to clone

Default: `4c1c8785cadbac7f9e454536ab230887ae6b4705`

### finger_src_dir

The absolute path to where the Git repository should be cloned/cached

Default: `/var/cache/finger2020`

### finger_contact_template_src

The location of the source template for `contact.txt`.
Use something like `{{ playbook_dir }}/templates/contact.txt` for local
overrides.

Default: [`contact.txt`](templates/contact.txt)

### finger_plan_template_src

The location of the source template for `plan.txt`.
Use something like `{{ playbook_dir }}/templates/plan.txt` for local
overrides.

Default: [`plan.txt`](templates/plan.txt)

### finger_project_template_src

The location of the source template for `project.txt`.
Use something like `{{ playbook_dir }}/templates/project.txt` for local
overrides.

Default: [`project.txt`](templates/project.txt)

### finger_install_git

Toggles the task that ensures the 'git' package is installed, which is
required for cloning the Finger2020 repository.

Default: `true`
