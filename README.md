# chrony

Chrony NTP server

[Chrony website/documentation](https://chrony.tuxfamily.org/)

[Ubuntu Chrony docs](https://ubuntu.com/blog/ubuntu-bionic-using-chrony-to-configure-ntp)

## Requirements

Minimum ansible version: 2.9.5

## Configuration

Add the NTP servers you want to use to the `ntp_pools` list, with a count of
servers per pool.

Add a list of CIDR formatted IP ranges to `ntp_client_allow`, and those systems
will be able to request time information from the server.

## Example Playbook

```yaml
- hosts: all
  vars:
    ntp_pools:
      - name: 0.pool.ntp.org
        count: 1
      - name: 1.pool.ntp.org
        count: 1
      - name: 2.pool.ntp.org
        count: 1
      - name: 3.pool.ntp.org
        count: 1
    ntp_client_allow:
      - "10.0.0.1/24"
  roles:
    - chrony
```

## License and Author

© 2021 Open Networking Foundation <support@opennetworking.org>

License: Apache-2.0
