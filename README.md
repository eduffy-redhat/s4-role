S4 Ansible Role
=========

Used to create or destroy s3 buckets on an s4 enpoint

[See the s4 repo for more info on how to use it.](https://github.com/rh-aiservices-bu/s4)

Requirements
------------

An s4 enpoint, the host information and credentials should be specified in variables, see the below section for explanations of each variable

Role Variables
--------------

- s4_s4: S4 Endpoint Information
    - endpointProtocol: Either 'http' or 'https'
    - endpointAddress: Hostname of the s4 server
    - endpointPort: Port for the s4 server, this is 7480 by default
    - endpointUser: The s4 server username, default is "s4admin"
    - endpointPassword: The s4 server password, default is "s4secret"
- s4_destroy: Default is false. true will destroy the specified bucket. false or omitting this will create the specified bucket
- s4_buckets: A list of strings defining the bucket names to operate on, see the below example for how this should look

Dependencies
------------

- amazon.aws.s3_bucket

Example Playbook
----------------

```
---
- name: "Test s4 Role"
  hosts: localhost
  remote_user: root
  roles:
    - role: s4
      s4_buckets:
        - "test"
        - "test2"
    - role: s4
      s4_destroy: true
      s4_buckets:
        - "test"
        - "test2"
```

License
-------

Apache-2.0

Author Information
------------------

