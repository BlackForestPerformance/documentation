---
title: Services
layout: default
parent: Admins
---

# Services
{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

## Mailcow
([Mailcow Admin panel], [Webmail], [Rspamd])

[Mailcow] is used as an all-in-one mail server. It is a set of Docker containers that are managed by `docker-compose`. It includes a web interface for administration, a webmail client, a spam filter, virus scanner, and more. ([Mailcow Documentation])

Mailcow already includes a NGINX inside the container, but we use a second NGINX on the host to relay everything with the `mail.` subdomain and all MX requests to the Mailcow container.

In the Belwue network, you are not allowed to run mail servers because of security policies. You can receive emails, but you can't send them. For this reason, an extra service ([Mailjet](#mailjet)) is used to send the emails.

## Mailjet
([Customer Login])

[Mailjet] is used to send our emails. We are sending them to Mailjet via HTTPS and they are sending them out using their own SMTP servers. THIS IS NOT HOSTED ON OUR VM, its a service we use.

The free plan of Mailjet allows sending 6000 emails per month (200 per day). It will limit to 1500 Contacts though. This is why a under `/usr/local/bin` a script `deleteAllMailJetContacts.sh` can be found that will delete all contacts from the Mailjet account. This script will be run by a cronjob every day at 2 am. (`0 2 * * * /usr/local/bin/deleteAllMailJetContacts.sh`)

## Vaultwarden
([Password manager], [Vaultwarden Admin Panel])

[Vaultwarden] is used as a central password manager. It is a self-hosted Bitwarden compatible server.

## NGINX

[NGINX] is used as a reverse proxy for the Mailcow container. We actually use two NGINX instances. One is inside the Mailcow container and the other one is on the host.

The config of the host NGINX can be found at `/etc/nginx/nginx.conf`. (This links to `/etc/nginx/sites-enabled/`, etc.)

The config of the Mailcow NGINX can be found at #TODO.

## Guacamole
([Guacamole Panel])

Apache [Guacamole] is a clientless remote desktop gateway. It supports standard protocols like VNC, RDP, and SSH.

We use it to connect to the VM in the university network. Sadly in the university network, ssh is not possible. So we use Guacamole to connect to the VM.

## Just the Docs
([Documentation Page])

This very page is created using the [Just the Docs] Jekyll theme. It is a simple and easy-to-use theme for documentation.
It's hosted on GitHub Pages.

----

[Mailcow Admin panel]: https://mail.bfp-racing.de/
[Webmail]: https://mail.bfp-racing.de/SOGo/
[Rspamd]: https://mail.bfp-racing.de/rspamd/
[Mailcow]: https://github.com/mailcow/mailcow-dockerized
[Mailcow Documentation]: https://docs.mailcow.email/

[Mailjet]: https://www.mailjet.com/
[Customer Login]: https://app.mailjet.com/signin

[Password manager]: https://password.bfp-racing.de
[Vaultwarden Admin Panel]: https://password.bfp-racing.de/admin
[Vaultwarden]: https://www.vaultwarden.net/

[NGINX]: https://www.nginx.com/

[Guacamole Panel]: https://remote.bfp-racing.de/guacamole/
[Guacamole]: https://guacamole.apache.org/

[Documentation Page]: /
[Just the Docs]: https://just-the-docs.com/

