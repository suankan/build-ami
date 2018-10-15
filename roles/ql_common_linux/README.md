ql_common_linux
===============

This role contains common configuration that should be applied to all Linux instances

Requirements
------------

This role is expecting to be run on a Red Hat based system.  E.g. CentOS or Amazon Linux

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------

Just apply the role, no vars required:

    - hosts: servers
      roles:
         - { role: ql_common_linux }

License
-------

Commercial

Author Information
------------------

Mary