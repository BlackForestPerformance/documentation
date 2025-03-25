---
title: Server Requirements
layout: default
parent: Admins
---

# Server Requirements
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Mailcow

|      | minimal               | empfohlen |
|------|-----------------------|-----------|
| CPU  | 1 GHz                 |           |
| RAM  | 6 GB + 1 GB swap      |           |
| Disk | 20 GB (without mails) |           |

### Ports
{: .no_toc }

#### Incoming
{: .no_toc }

| Service             | Protocol | Port   | Container       | Variable                         |
|---------------------|----------|--------|-----------------|----------------------------------|
| Postfix SMTP        | TCP      | 25     | postfix-mailcow | `${SMTP_PORT}`                   |
| Postfix SMTPS       | TCP      | 465    | postfix-mailcow | `${SMTPS_PORT}`                  |
| Postfix Submission  | TCP      | 587    | postfix-mailcow | `${SUBMISSION_PORT}`             |
| Dovecot IMAP        | TCP      | 143    | dovecot-mailcow | `${IMAP_PORT}`                   |
| Dovecot IMAPS       | TCP      | 993    | dovecot-mailcow | `${IMAPS_PORT}`                  |
| Dovecot POP3        | TCP      | 110    | dovecot-mailcow | `${POP_PORT}`                    |
| Dovecot POP3S       | TCP      | 995    | dovecot-mailcow | `${POPS_PORT}`                   |
| Dovecot ManageSieve | TCP      | 4190   | dovecot-mailcow | `${SIEVE_PORT}`                  |
| HTTP(S)             | TCP      | 80/443 | nginx-mailcow   | `${HTTP_PORT}` / `${HTTPS_PORT}` |

#### Outgoing
{: .no_toc }

| Service           | Protocol      | Port    | Target                                | Reason                                                                                       |
|-------------------|---------------|---------|---------------------------------------|----------------------------------------------------------------------------------------------|
| Clamd             | TCP           | 873     | rsync.sanesecurity.net                | Download ClamAV signatures (prebundled in mailcow)                                           |
| Dovecot           | TCP           | 443     | spamassassin.heinlein-support.de      | Download Spamassassin rules processed by Rspamd, downloaded via Dovecot                      |
| mailcow Processes | TCP           | 80/443  | github.com                            | Download mailcow updates (code-based)                                                        |
| mailcow Processes | TCP           | 443     | hub.docker.com                        | Download Docker images (directly from Docker Hub)                                            |
| mailcow Processes | TCP           | 443     | asn-check.mailcow.email               | API request for BAD ASN checks (for Spamhaus Free Blocklists)                                |
| mailcow Processes | TCP           | 80      | ip4.mailcow.email & ip6.mailcow.email | Retrieve public IP address for display in UI (**optional**)                                  |
| Postfix           | TCP           | 25, 465 | Any                                   | Outgoing connection for MTA                                                                  |
| Rspamd            | TCP           | 80      | fuzzy.mailcow.email                   | Download bad subject regex maps (trained by Servercow)                                       |
| Rspamd            | TCP           | 443     | bazaar.abuse.ch                       | Download malware MD5 checksums for detection by Rspamd                                       |
| Rspamd            | TCP           | 443     | urlhaus.abuse.ch                      | Download malware download links for detection in Rspamd                                      |
| Rspamd            | UDP           | 11445   | fuzzy.mailcow.email                   | Connection to global mailcow fuzzy (trained by Servercow + community)                        |
| Rspamd            | UDP           | 11335   | fuzzy1.rspamd.com & fuzzy2.rspamd.com | Connection to global Rspamd fuzzy (trained by the Rspamd team)                               |
| Unbound           | TCP **&** UDP | 53      | Any                                   | DNS resolution for the mailcow stack (for DNSSEC validation and retrieval of spam list info) |

## WordPress

|      | minimal | empfohlen |
|------|---------|-----------|
| CPU  |         | 1 Kern    |
| RAM  |         | 4 GB      |
| Disk |         | 50 GB     |

### Ports
{: .no_toc }

Hab ich nichts richtig dazu gefunden

#### Outgoing
{: .no_toc }

| Service | Protocol | Port |
|---------|----------|------|
| HTTP    |          | 80   |
| HTTPS   |          | 443  |

## NGinX

[Standard NGINX Configuration Deployments]

The following sizing guidelines are for Instance Manager deployments with data plane instances that have standard configurations; that is, up to **40** upstream servers with associated location and server blocks and up to 350 associated certificates.
We recommend using solid-state drives (SSDs) for better storage performance.

| # of Data Plane Instances | CPU    | Memory   | Network   | Storage |
|---------------------------|--------|----------|-----------|---------|
| 10                        | 2 vCPU | 4 GB RAM | 1 GbE NIC | 100 GB  |
| 100                       | 2 vCPU | 4 GB RAM | 1 GbE NIC | 1 TB    |
| 1000                      | 4 vCPU | 8 GB RAM | 1 GbE NIC | 3 TB    |

## We want

{: .quote-title }
> The Mail we sent to Martin Kramer
>
> Hallo Martin,
>
> wir haben uns das ganze Ausmaß jetzt mal angeschaut und sind auf folgende Anforderungen gekommen:
>
> Wir würden gerne Debian nutzen,
>
> mit folgenden Ressourcen:
>
> 6 cores
> 8 GB Ram<br>
> 100 GB Speicher
>
> Ebenfalls sollten folgende Ports geöffnet werden:
>
> Incoming:
>
> TCP 25<br>
> TCP 465<br>
> TCP 587<br>
> TCP 143<br>
> TCP 993<br>
> TCP 110<br>
> TCP 995<br>
> TCP 4190<br>
> HTTP(S) TCP 80/443
>
> Outgoing:
>
> TCP 873<br>
> TCP 443 spamassassin.heinlein-support.de<br>
> TCP 80/443 github.com<br>
> TCP 443 hub.docker.com<br>
> TCP 443 asn-check.mailcow.email<br>
> TCP 80 ip4.mailcow.email & ip6.mailcow.email<br>
> TCP 25, 465 <br>
> TCP 80 fuzzy.mailcow.email<br>
> TCP 443 bazaar.abuse.ch<br>
> TCP 443 urlhaus.abuse.ch<br>
> UDP 11445 fuzzy.mailcow.email<br>
> UDP 11335 fuzzy1.rspamd.com & fuzzy2.rspamd.com<br>
> TCP & UDP 53
>
> Dazu sollten wir (aber ich glaub das ist an dem Punkt verständlich) die Möglichkeit haben per SSH auf den Server drauf zu können.
>
> Fragen:
>
> Sollte eine Ressource nicht ausreichen, kann man die im Nachgang "hotpatchen" oder ist das fest ?<br>
> Brauchst du auch die DNS der Domaine in irgendeiner Art ?
>
>
> Vielen Dank
>
> Mit freundlichen Grüßen<br>
> Christian Zeidler,<br>
> Dominik Meurer

## Infos

### Domain

Welche?

- bf-performance.org
- bfperformance.org
- blackforestperformance.de
- **bfp-racing.de**

{: .new-title }
> [bfp-racing.de] is the domain we bought.

---

[Standard NGINX Configuration Deployments]: https://docs.nginx.com/nginx-management-suite/tech-specs/#standard-nginx-configuration-deployments

[bfp-racing.de]: https://bfp-racing.de

