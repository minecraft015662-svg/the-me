# Sarthak34 all-in-one

One Node.js app (no npm install) = admin website + license API + `install.sh` + theme/extension files.

## Run on your VPS
    export ADMIN_PASS='a-long-password'
    export PUBLIC_URL='https://license.yourdomain.com'
    node server.js            # listens on 127.0.0.1:3434

Put HTTPS in front (required, the admin login uses Basic auth). Caddy example:
    license.yourdomain.com { reverse_proxy 127.0.0.1:3434 }

Keep it running (systemd): ExecStart=/usr/bin/node /opt/sarthak34/server.js, with Environment=ADMIN_PASS=... PUBLIC_URL=...

## Use
- Open PUBLIC_URL, log in (user `admin`, your ADMIN_PASS). Create, revoke or restore licenses.
- Customer runs: curl -sSL https://license.yourdomain.com/install.sh | sudo bash
- Add extensions: packages/extensions/<name>/ + packages/index.json.
- Back up data/licenses.json.
