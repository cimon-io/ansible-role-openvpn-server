[![Build Status](https://travis-ci.org/cimon-io/ansible-role-openvpn-server.svg?branch=master)](https://travis-ci.org/cimon-io/ansible-role-openvpn-server)

# Ansible Role OpenVPN Server

An ansible role that installs and configures OpenVPN server. It also allows you to install from source OpenSSL.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values.

```yaml
openvpn_config_files: []
# openvpn_config_files: ["files/openvpn/*.conf"]

openvpn_requirements:
  - build-essential
  - git
  - pkg-config
  - libpam0g-dev
  - libsystemd-dev

openvpn_version: "2.4.7"
openvpn_source: "https://swupdate.openvpn.org/community/releases/openvpn-{{ openvpn_version }}.tar.gz"
openvpn_src_path: "/usr/local/src/"

openvpn_conf_path: "/etc/openvpn"
openvpn_install_path: "/opt/openvpn"

openvpn_configure_args: "--prefix={{ openvpn_install_path }} --disable-lzo --enable-iproute2 --enable-systemd --enable-x509-alt-username"
openvpn_configure_env: {}
#  CFLAGS: "-I{{ openvpn_openssl_prefix }}/include -Wl,-rpath={{ openvpn_openssl_prefix }}/lib -L{{ openvpn_openssl_prefix }}/lib"

openvpn_system_openssl: True
openvpn_openssl_version: "1.1.1d"
openvpn_openssl_source: "https://www.openssl.org/source/openssl-{{ openvpn_openssl_version }}.tar.gz"
openvpn_openssl_prefix: "/opt/openssl"
openvpn_openssl_openssldir: "/opt/openssl/ssl"

openvpn_easyrsa_version: "v3.0.6"
openvpn_easyrsa_repo: "https://github.com/OpenVPN/easy-rsa.git"
```

## Dependencies

None

## Notes

You must specify the path to the shared libraries `LD_LIBRARY_PATH={{ openvpn_openssl_prefix }}/lib/` (for easyrsa - `vars` file).

## License

Licensed under the [MIT License](https://opensource.org/licenses/MIT).
