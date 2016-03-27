letsencrypt
-------------------
Installs letsencrypt and generates/installs a certificate.


Generate Cert
-------------
In order to generate a certificate port 443 needs to be open and the following variables are required.

Required Variables:

- `subdomain:`
- `domain:`
- `letsencrypt_email:`

Optional Variables:
- `server_type:` #apache or nginx. Will use the webserver of your choosing to verify the request (Standalone).
- `revoke:` #Set to `yes` if you want to revoke the certificate
- `force_renewal:` #Set to `yes` to force certificate renewal.

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
    - CorbanR.letsencrypt
```

Defaults
--------
- `authenticator: "standalone"`
- `certificate_path: /etc/letsencrypt/live`
- `letsencrypt_bin: "/root/.local/share/letsencrypt/bin/letsencrypt"`
- `letsencrypt_gitlocation: /opt/letsencrypt`
- `letsencrypt_server: https://acme-staging.api.letsencrypt.org/directory`
- `renew_days: 10`
- `rsa_key_size: 2048`
- `server_type: ""`
- `standalone_supported_challenges: "tls-sni-01"`
- `webroot_path: ""`

To Do
-----
- Multiple certificate logic
- Add logic for authenticator type != "standalone"
- Add cron job to check certificate expiration and auto renew.
