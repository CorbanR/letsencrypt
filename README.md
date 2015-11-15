letsencrypt
-------------------
Installs letsencrypt and optionally generates/installs a certificate.

*** This is still in testing ***

Generate Cert
-------------
In order to generate a cert port 443 needs to be open and the following variables are required.

Required Variables:

- `subdomain:`
- `domain:`
- `letsencrypt_email:`

Optional Variables:
- `server_type:` #apache or nginx. Will attempt to automatically install the certificate.
- `revoke:` #Set to `yes` if you want to revoke the certificate


Example:

```
- hosts: letsencrypt
  remote_user: <your_user>
  become: yes
  vars:
    subdomain: www
    domain: example.com
    letsencrypt_email: example@example.com
  roles:
    - letsencrypt
```

Defaults
--------
- `letsencrypt_gitlocation: /opt/letsencrypt`

- `rsa_key_size: 2048`
- `letsencrypt_server: https://acme-staging.api.letsencrypt.org/directory`
- `standalone_supported_challenges: "tls-sni-01"`
- `authenticator: "standalone"`
- `webroot_path: ""`
- `renew_days: 10` #auto renew if expiring in 10 days
- `certificate_path: /etc/letsencrypt/live`

To Do
-----
- Multiple certificate logic
- Add cron job to check certificate expiration and auto renew.
