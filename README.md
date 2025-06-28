# OIDCWarden Railway Template

OIDCWarden is a soft fork of Vaultwarden that implements OIDC SSO. This repository is based on the Railway template for Vaultwarden.

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/5sr9Tw?referralCode=h0iQGD)

You will have to first deploy Postgres, and then set the following environment variables:

```env
ADMIN_TOKEN="secure_string"
DOMAIN="https://${{RAILWAY_STATIC_URL}}"
I_REALLY_WANT_VOLATILE_STORAGE="true"
PGDATABASE="${{Postgres.PGDATABASE}}"
PGHOST="${{Postgres.PGHOST}}"
PGPASSWORD="${{Postgres.PGPASSWORD}}"
PGPORT="${{Postgres.PGPORT}}"
PGUSER="${{Postgres.PGUSER}}"
PORT="8000"
```

The only variable that needs configuration is `ADMIN_TOKEN`, which you can generate with a command like the following:

```bash
openssl rand -base64 24
```
