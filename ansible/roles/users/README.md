# users

Role to manage users on a system.

## Role configuration

* users_default_shell (default: /bin/bash) - the default shell if none is
  specified for the user.

## Creating users

Add a users variable containing the list of users to add. A good place to put
this is in `group_vars/all` or `group_vars/groupname` if you only want the
users to be on certain machines.

The following attributes are required for each user:

* username - The user's username.

In addition, the following items are optional for each user:

* home - The home directory of the user to create (optional, defaults to /home/username).
* uid - The numeric user id for the user (optional). This is required for uid consistency
  across systems.
* password - If a hash is provided then that will be used, but otherwise the
  account will be locked.
* update_password - This can be either 'always' or 'on_create'
  - 'always' will update passwords if they differ. (default)
  - 'on_create' will only set the password for newly created users.
* ssh_key - This should be a list of SSH keys for the user (optional). Each SSH key
  should be included directly and should have no newlines.
* generate_ssh_key - Whether to generate a SSH key for the user (optional, defaults to no).
* shell - The user's shell. This defaults to /bin/bash. The default is
  configurable using the users_default_shell variable if you want to give all
  users the same shell, but it is different than /bin/bash.

Example:

    ---
    users:
      - username: foo
        home: /local/home/foo
        ssh_key:
          - "ssh-rsa AAAAA.... foo@machine"
          - "ssh-rsa AAAAB.... foo2@machine"
