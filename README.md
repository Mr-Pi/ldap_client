# ldap-client

This role configures `ldap.conf` to use the old faveve LDAP.

## Requirements

None.

## Role Variables

| Name                                     | Required/Default                             | Description                                                                                                                                                                    |
|------------------------------------------|:--------------------------------------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ldap_client_base`                       | `dc=faveve, dc=uni-stuttgart, dc=de`         | `BASE` value to set                                                                                                                                                            |
| `ldap_client_uris`                       | `[ldaps://ldap01.faveve.uni-stuttgart.de/]`  | List of URIs to set                                                                                                                                                            |
| `ldap_client_ldap_version`               | `3`                                          | LDAP version to use                                                                                                                                                            |
| `ldap_client_pam_password`               | `crypt`                                      | PAM password method                                                                                                                                                            |
| `ldap_client_tls_cacert`                 | `/etc/ssl/certs/ca-certificates.crt`         | Path to the CA certificate to check against                                                                                                                                    |
| `ldap_client_tls_cacertdir`              | `/etc/ssl/certs`                             | Directory where single CA certificates are placed (this is checked if `ldap_client_tls_cacert` doesn't work)                                                                   |
| `ldap_client_tls_reqcert`                | `demand`                                     | Method of checking the CA cert (`never`, `allow` (allow no cert, checking and bad certs), `try` (no cert or valid certs are allowed), `demand` (valid certificate is required) |
| `ldap_client_nss_initgroups_ignoreusers` | _see [defaults/main.yml](defaults/main.yml)_ | List of users that should never be queried to LDAP (`nss_ldap` module is necessary)                                                                                            |

## Example Playbook

```yml
- hosts: zammad
  roles:
  - ldap-client
  vars:
    ldap_client_reqcert: allow
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Markus Mroch (Mr. Pi)](https://github.com/Mr-Pi) _markus.mroch@stuvus.uni-stuttgart.de_
- [Michel Weitbrecht (SlothOfAnarchy)](https://github.com/SlothOfAnarchy) _michel.weitbrecht@stuvus.uni-stuttgart.de_
