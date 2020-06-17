# ansible-openvpn

Ansible playbook to install and configure an OpenVPN server. This also do the following:
* Generate the certificates and private keys necessary for OpenVPN.
* Configure ufw to allow incoming OpenVPN connections and add the necessary NAT rules for outbound traffic.

This was tested to work with Debian-based OSes (and at least Ubuntu 16.04). Also, plays nicely to OpenVZ virtualization.
