S4 Ansible Role
=========

Used to create or destroy s3 buckets on an s4 enpoint

Requirements
------------

An s4 enpoint, the host information and credentials should be specified in variables, see the below section for explanations of each variable

Role Variables
--------------

- s4: S4 Endpoint Information
    - endpointProtocol: Either 'http' or 'https'
    - endpointAddress: Hostname of the s4 server
    - endpointPort: Port for the s4 server, this is 7480 by default
    - endpointUser: The s4 server username, default is "s4admin"
    - endpointPassword: The s4 server password, default is "s4secret"
- destroy: Default is false. true will destroy the specified bucket. false or omitting this will create the specified bucket
- buckets: A list of strings defining the bucket names to operate on, see the below example for how this should look

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
      buckets:
        - "testBucket1"
        - "testBucket2"
    - role: s4
      destroy: true
      buckets:
        - "testBucket1"
        - "testBucket2"
```

License
-------

MIT (I think? idk)

Author Information
------------------

