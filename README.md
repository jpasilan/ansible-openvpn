# ansible-openvpn

![Ansible Lint](https://github.com/jpasilan/ansible-openvpn/workflows/Ansible%20Lint/badge.svg)

Ansible playbook to install and configure an OpenVPN server on a VPS. This will do the following:
* Build a CA using EasyRSA.
* Generates the certificates and keys needed by the OpenVPN server.
* Configures ufw to allow incoming OpenVPN connections. Also adds the necessary NAT rules for outbound traffic.

There is also a separate playbook to generate the client ovpn configs.

# Works In

This was tested in the following distros:

* Debian 10.3, 9.12
* Ubuntu 20.04, 19.10, 18.04, and 16.04

Configuration for OpenVZ VPSes is handled as well. Be warned though that it is not recommended to run a VPN on an OpenVZ VPS.

# Setup

Prior to running the playbooks, create the inventory named `hosts.yml` and the vars file, `secret_vars.yml`. Sample files are provided for reference.
Also, create the `clients` directory in the parent directory. This is where the client config files will be downloaded.

# Usage

Run first the playbook for the OpenVPN server, like so:

`ansible-playbook openvpn-server-playbook.yml`

Then, generate the client config file with:

`ansible-playbook openvpn-client-playbook.yml -e "cert_client=name"`

The `cert_client` overrides the default which is `client`.
