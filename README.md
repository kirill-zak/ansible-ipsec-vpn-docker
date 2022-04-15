IPSec VPN docker
=========

An Ansible role for run IPSec VPN in Docker container

## Support distributive

* CentOS 8
* Debian 10 (Buster)
* Debian 11 (Bullseye)
* Fedora 35
* Ubuntu 18.04 (Bionic Beaver)
* Ubuntu 20.04 (Focal Fossa)

## Requirements

Docker engine

## Role Variables

### Common container vars
- `ipsec_vpn_docker_container_volume`: Name of volume for container. Default value: `ipsec_vpn_ikev2_data`
- `ipsec_vpn_docker_container_name`: Name of container. Default value: `ipsec_vpn`
- `ipsec_vpn_docker_env_file_path`: Path of env file. Default value: `/root/vpn.env`
- `ipsec_vpn_docker_log_driver`: Name of log driver. Default value: `none` (Disabled logs)
- `ipsec_vpn_docker_tag`: Tag of image. Tag found at # https://hub.docker.com/r/hwdsl2/ipsec-vpn-server/tags

### Common credentials vars
- `ipsec_vpn_docker_psk`: IPSec PSK key. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L8
- `ipsec_vpn_docker_user`: IPSec user. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L9
- `ipsec_vpn_docker_password`: IPSec password. Default value is empty. For more information #https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L10

Leave any of common credentials empty for auto generate

### Additional credentials
- `ipsec_vpn_docker_additional_user_list`: List of additional users. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L16
- `ipsec_vpn_docker_additional_password_list`: List of passwords for additional users. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L17

### DNS vars
- `ipsec_vpn_docker_dns_name`: DNS Name of VPN server. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L21
- `ipsec_vpn_docker_dns_server_1`: First DNS server. Default value: `1.1.1.1`.
- `ipsec_vpn_docker_dns_server_2`: Second DNS server. Default value: `1.0.0.1`

### IKEv2 vars
- `ipsec_vpn_docker_ikev2_client_name`: Name of IKEv2 clients. Default value is empty. For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L26
- `ipsec_vpn_docker_ikev2_protect_config`: Protect IKEv2 client configuration by password toggle. Default value: `no` For more information # https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/vpn.env.example#L37

## Dependencies

- Docker

## Example Playbook

```yml
    - name: Install IPSec VPN
      hosts: servers
      become: true
      roles:
        - role: kirill_zak.docker
        - role: kirill_zak.ipsec_vpn_docker
```

## License

MIT

## Author Information

https://kirill-zak.ru
