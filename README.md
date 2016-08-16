ansible-module-users
====================

Role to manage users on a system.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

* users_create_per_user_group (default: true) 
  when creating users, also create a group with the same username and make
  that the user's primary group.
* users_group (default: users)
  if users_create_per_user_group is _not_ set,
  then this is the primary group for all created users.
* users_default_shell (default: /bin/bash)
  the default shell if none is specified for the user.
* users_create_homedirs (default: true) - create home directories for new
  users. Set this to false is you manage home directories separately.

* username - The user's username.
* name - The full name of the user (gecos field)
* uid - The numeric user id for the user. This is required for uid consistency
  across systems.
* password - If a hash is provided then that will be used, but otherwise the
  account will be locked
* groups - a list of supplementary groups for the user.
* ssh-key - This should be a list of ssh keys for the user. Each ssh key
  should be included directly and should have no newlines.
* shell - The user's shell. This defaults to /bin/bash. The default is
  configurable using the users_default_shell variable if you want to give all
  users the same shell, but it is different than /bin/bash.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

    ---
    users:
      - username: foo
        name: Foo Barrington
        groups: ['wheel','systemd-journal']
        uid: 1001
        ssh_key:
          - "ssh-rsa AAAAA.... foo@machine"
          - "ssh-rsa AAAAB.... foo2@machine"
    users_deleted:
      - username: bar
        name: Bar User
        uid: 1002

License
-------

GPLv3

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
