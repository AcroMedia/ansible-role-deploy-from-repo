# Ansible role: Deploy from Repo

![.github/workflows/molecule.yml](https://github.com/AcroMedia/ansible-role-deploy-from-repo/workflows/.github/workflows/molecule.yml/badge.svg)

Clone the specified git repository locally, push its contents up to a temp directory on the server, and then run the specified command in the uploaded folder.

Intended for use with private repos that have a `make` install process.


## Requirements

Obviously, the operator of the playbook must have read access to the specified repo.

As of this writing, this role only works from a linux workstation because of the `tempfile` task.


## Role Variables

* `repo_src`

  The URL of the private repository.

* `repo_subdir`

  If specified, only the files inside this dir will be pushed to the remote host.

* `make_cmd`

   Only needed if you would run something other than `make -s install`.

## Dependencies

n/a


## Example Playbook

    - hosts: servers
      roles:
         - name: Deploy package xyz
           role: acromedia.deploy-from-private
           repo_src: 'git@git.privateserver.com:account/project.git'
           repo_subdir: src
           make_cmd: make install


## License

GPLv3


## Author Information

Acro Media Inc https://www.acromedia.com
