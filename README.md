# Nextcloud Configuration Templates for Small Business

Reference configuration templates for a self-hosted Nextcloud deployment
using Nginx, PHP 8.3 FPM, Redis, APCu, and Tailscale. These files are examples,
not drop-in or production-ready configuration. Review and test them against
your Nextcloud release, operating system, threat model, storage, and network.

The templates intentionally contain placeholder values for secrets, domains,
and addresses. Replace every placeholder before deployment. Keep a completed
`config.php`, TLS private keys, credentials, and backups out of Git.

## Files

- `nginx_template.conf` — example Nginx virtual host and TLS paths.
- `php_template.php` — example Nextcloud settings, including Redis/APCu.
- `php8.3_fpm_template.ini` — PHP-FPM settings for PHP 8.3.
- `redis_template.conf` — Redis Unix-socket example.
- `.gitignore` — ignores local configuration secrets and generated files.

## Before deployment

1. Confirm the Nextcloud, PHP, Nginx, Redis, and operating-system versions
   supported by your installation; these examples target PHP 8.3.
2. Replace all `REPLACE_WITH_`, `YOUR_`, and `xxxx` values with
   deployment-specific values. Generate fresh Nextcloud `secret` and
   `passwordsalt` values; never reuse values from another installation.
3. Review `trusted_domains`, `trusted_proxies`, forwarded-header handling,
   Tailscale exposure, TLS certificate paths, and filesystem permissions for
   your actual topology.
4. Review PHP and Nginx upload limits alongside available disk space, memory,
   timeouts, and backup capacity.
5. Validate Nginx configuration (`nginx -t`), PHP-FPM configuration, and
   Redis socket ownership and permissions before restarting services.
6. Back up existing configuration and data, then test changes in a staging
   environment before applying them to a live Nextcloud server.

The repository does not include an installed `config.php` or private TLS key.
The `.gitignore` excludes common local secrets, but check `git status` before
each commit and never commit database or SMTP passwords. Configuration choices
must be evaluated for your environment; this repository is not a substitute
for a security review or Nextcloud's current administrator documentation.
