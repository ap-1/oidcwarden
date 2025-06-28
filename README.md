# OIDCWarden Railway Template

OIDCWarden is a soft fork of Vaultwarden that implements OIDC SSO. This repository is based on the Railway template for Vaultwarden.

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/5sr9Tw?referralCode=h0iQGD)

You will have to first deploy Postgres, and then set the following environment variables:

```env
ADMIN_TOKEN="secure_string"

SSO_AUTHORITY="oidc_discovery_endpoint"
SSO_CLIENT_ID="sso_client_id"
SSO_CLIENT_SECRET="sso_client_secret"
SSO_SCOPES="email profile offline_access"
SSO_ENABLED="true"
SSO_ONLY="true"

# these should not need any further configuration
DOMAIN="https://${{RAILWAY_STATIC_URL}}"
I_REALLY_WANT_VOLATILE_STORAGE="true"
PGDATABASE="${{Postgres.PGDATABASE}}"
PGHOST="${{Postgres.PGHOST}}"
PGPASSWORD="${{Postgres.PGPASSWORD}}"
PGPORT="${{Postgres.PGPORT}}"
PGUSER="${{Postgres.PGUSER}}"
PORT="8000"
```

1. `ADMIN_TOKEN` should be set to a secure string, which you can generate with a command like the following:

```bash
openssl rand -base64 24
```

2. The `SSO_*` variables may need further configuration. You can find relevant documentation, including specific instructions for your IdP, [here](https://github.com/Timshel/OIDCWarden/blob/main/SSO.md).

3. You should add `https://your.vault.domain/identity/connect/oidc-signin` as an authorized redirect URI in your OIDC provider settings.
