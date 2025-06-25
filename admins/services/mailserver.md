---
title: Mailserver
layout: default
parent: Service Overview
---

# Mailserver
{: .no_toc }
[Mailcow Admin panel]{: .btn }
[Webmail]{: .btn }
[Rspamd]{: .btn }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

## Installation

{: .warning-title }
> TBD

## Mail Configuration

{: .highlight-title }
> TBD

### Domain : BFP-Racing

At the moment, there only is one

#### Rate Limit

{: .warning-title }
> TBD
> 
> Values might have changed since this was written.

This is set to 190 mails per day. Mailjet has a free tier with up to 6000 mails per month. This is 200 mails per day.
We set the limit to 190 mails per day to be sure that we don't hit the limit.

#### Domain wide footer

The domain wide footer is stored at the [Mailfooter Repo].

This will be applied to all mails sent from the domain. No exceptions.

### Mailboxes

Each mailbox, except admin, has a 1 GB quota and a rate limit of 5 mails per second. Anything else is unchanged.

Currently, the following mailboxes are set up:
- `admin`
- `contact`
- `financials`
- `management`
- `marketing`

### Aliases

Following aliases are set up:
- `privacy`: Will be forwarded to marketing, management and admin. This is the standard mail for privacy requests.
- `support`: Will be forwarded to `admin`.
- `postmaster`: Will be forwarded to `admin`. This is the standard mail for mail server Admins.
- `info`: Will be forwarded to `contact`. This is the standard mail for contact requests.
- `<empty>`: This is a catch-all alias. All mails will be used to "learn as spam."

## Server Configuration

{: .warning-title }
> TBD

### ARC/DKIM

{: .warning-title }
> TBD

### Fail2Ban

{: .warning-title }
> TBD

### Password Policy

{: .warning-title }
> TBD

### Routing

{: .highlight-title }
> TBD
> 
> Important, because I don't know shit about this.

This is the link to the [Brevo] explanation, the service we use to send mails through the belwue blockage.


----

[Mailcow Admin panel]: https://mail.bfp-racing.de/
[Webmail]: https://mail.bfp-racing.de/SOGo/
[Rspamd]: https://mail.bfp-racing.de/rspamd/

[Mailfooter Repo]: /admins/github/#mail-footer

[Brevo]: /admins/services/#brevo