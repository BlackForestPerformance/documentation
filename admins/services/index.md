---
title: Service Overview
layout: default
parent: Admins
---

# Services
{: .no_toc }

[Uptime]{: .btn }
[Uptime All]{: .btn }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

## Mailcow
([Mailcow Admin panel], [Webmail], [Rspamd])

[Mailcow] is used as an all-in-one mail server. It is a set of Docker containers that are managed by `docker-compose`. It includes a web interface for administration, a webmail client, a spam filter, virus scanner, and more. ([Mailcow Documentation])

Mailcow already includes a NGINX inside the container, but we use a [second NGINX on the host](#nginx) to relay everything with the `mail.` subdomain and all MX requests to the Mailcow container.

In the Belwue network, you are not allowed to run mail servers because of security policies. You can receive emails, but you can't send them. For this reason, an extra service ([Brevo](#brevo)) is used to send the emails.

## Brevo
([Customer Login])

[Brevo] is used to send our emails. We are sending them to Brevo via HTTPS, and they are sending them out using their own SMTP servers. THIS IS NOT HOSTED ON OUR VM; it's a service we use.

The free plan of Brevo allows sending 300 emails per day.

### Mailjet
This was the previously used service to send our emails. It had a limitation of 1500 contacts, which was not enough for us.\
This is why a under `/usr/local/bin` a script `deleteAllMailJetContacts.sh` can be found that will delete all contacts from the Mailjet account. This script will be run by a cronjob every day at 2 am. (`0 2 * * * /usr/local/bin/deleteAllMailJetContacts.sh`)

## Wordpress
([Wordpress], [Wordpress Admin Panel])

[Wordpress] is used as a content management system (CMS) for our website.\
**THE CONTAINER IS NOT PERSISTENT!**\
This means if you rebuild the container, all data will be lost. Or at least we are not sure if it is persistent.\
There are two docker volumes `/var/www/html` and `/var/lib/mysql` that store some data, but we are not sure if this is all of it. Just be careful and make backups before you take any risks.

## Vaultwarden
([Password manager], [Vaultwarden Admin Panel])

[Vaultwarden] is used as a central password manager. It is a self-hosted Bitwarden compatible server.

The docker compose file is located at `/opt/vaultwarden/docker-compose.yml`. The data is stored in the `/opt/vaultwarden/data` directory on the host.

## NGINX

[NGINX] is used as a reverse proxy. We actually use two NGINX instances. One is inside the Mailcow container and the other one is on the host.

The config of the host NGINX can be found at `/etc/nginx/nginx.conf`. (This links to `/etc/nginx/sites-enabled/`, etc.)

The host NGINX instance will use all the certificates provided by Certbot for each subdomain. In theory, it should refresh them, no idea if this works. That's one of the reasons we installed [Uptime Kuma](#uptime-kuma).

The config of the Mailcow NGINX can be found at #TODO. (I'm sorry, I really don't know)

## Guacamole
([Guacamole Panel])

Apache [Guacamole] is a clientless remote desktop gateway. It supports standard protocols like VNC, RDP, and SSH.

Why?\
We use it to connect to the VM in the university network. Sadly, in the university network, ssh is not possible. So we have use Guacamole to connect to the VM.

## Just the Docs
([Documentation Page])

This very page is created using the [Just the Docs] Jekyll theme. It is a simple and easy-to-use theme for documentation.
It's hosted on GitHub Pages.

## Uptime Kuma
([Uptime Kuma])

[Uptime]{: .btn }
[Uptime All]{: .btn }

This is a basic and lightweight uptime monitoring tool. Its currently used to monitor the DNS entries and HTTPS availability of all our services.
In theory, it can also monitor containers directly, specific ports, and more. But we are currently not using it for that.

It can send notifications to a metric ton of services, like Discord, Email, Signal, Telegram, Webhooks, and much, much more.\
The notifications are currently only used by one of the past admins on a personal Discord server.

The docker compose file is nonexistent, but the data is stored in a named volume `uptime-kuma` at `/var/lib/docker/volumes/uptime-kuma/_data`.\
The container was just started using the command from the docs: `sudo docker run -d --restart=always -p 127.0.0.1:3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1`

----

[Mailcow Admin panel]: https://mail.bfp-racing.de/
[Webmail]: https://mail.bfp-racing.de/SOGo/
[Rspamd]: https://mail.bfp-racing.de/rspamd/
[Mailcow]: https://github.com/mailcow/mailcow-dockerized
[Mailcow Documentation]: https://docs.mailcow.email/

[Brevo]: https://www.brevo.com/
[Customer Login]: https://login.brevo.com/

[Wordpress]: https://www.bfp-racing.de/
[Wordpress Admin Panel]: https://www.bfp-racing.de/wp-admin/

[Password manager]: https://password.bfp-racing.de
[Vaultwarden Admin Panel]: https://password.bfp-racing.de/admin
[Vaultwarden]: https://www.vaultwarden.net/

[NGINX]: https://www.nginx.com/

[Guacamole Panel]: https://remote.bfp-racing.de/guacamole/
[Guacamole]: https://guacamole.apache.org/

[Documentation Page]: /
[Just the Docs]: https://just-the-docs.com/

[Uptime Kuma]: https://uptime.bfp-racing.de/dashboard/
[Uptime]: https://uptime.bfp-racing.de/
[Uptime All]: https://uptime.bfp-racing.de/status/all

