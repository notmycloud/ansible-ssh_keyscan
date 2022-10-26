SSH Keyscan
=========

Simple role to alert on unknown SSH Fingerprint and allow for import to continue Playbook processing.

This role will record the following SSH Host Keys by default (RSA, DSA, ECDSA, ED25519).
Open an issue to support new/additional formats.

Known hosts will be put in a known_hosts.d directory with a file per host (inventory_hostname) for easy separation. Normal known_hosts locations will continue to work as expected.

NOTE: If a host key does not match what is currently saved, or one is not saved, the application will pause until you give the OK to proceed. This can be overridden with a variable.

Requirements
------------

This requires the `dig` command on the Ansible host.

Role Variables
--------------

global_known_hosts: false # Specify true to add to the global known_hosts, or default to the Ansible connection user's known_hosts.
ssh:
  host: host.example.com  # Specify which host to add to the known_hosts.
  port: 8022              # Specify which port to scan the SSH host, defaults to 22.
verify_host_keys: true    # Alert if the host key is new or does not match what is saved. Set to false to accept a new host key without user interaction.

Dependencies
------------

None at this time

Example Playbook
----------------


```yaml
---
- name: Playbook Name
  hosts: MyHosts
  
  roles:
    - role: notmycloud.ssh_keyscan
      vars:
        global_known_hosts: true
        ssh:
          host: github.com
          port: 22
        verify_host_keys: false
```

License
-------

MIT License

Copyright (c) 2022 Not My Cloud <devops@notmy.cloud>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Author Information
------------------

Coming Soon!

Support
------------------

For support, please raise an issue and provide the following items.
Do not reach out directly for support, all requests will be ignored.

- Sample task/playbook to replicate your issue.
- Ansible version `ansible --version`
- Ansible config `ansible-config dump --only-changed -t all`, if using an older version of Ansible, omit the `-t all`.
- Description of what is happening vs what you expect to happen.
