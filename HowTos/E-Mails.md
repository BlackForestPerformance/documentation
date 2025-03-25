---
title: E-Mails
layout: default
parent: How To
---

# E-Mails
{: .no_toc}
#### Table of Contents
{: .no_toc}
1. TOC
{:toc}

## Add new Mailbox

{: .warning-title }
> Please consider using an alias instead of a new mailbox
> 
> In many cases an alias is the better option because it wont use additional storage space on our server and the user wont have to log off / log on when using two E-Mails.

{: .info-title }
> What you need
> 
> - Someone with access to the "Management" Collection on Vaultwarden

1. Navigate to the [Mailcow admin panel]
2. Log in with the credentials you have.
3. In the Header, choose "E-Mail" > "Configuration"
4. Now switch to the "Mailboxes" > "Mailboxes" tab.
5. Select the "Add mailbox" button.
6. Change:
    - **Username**: this is the part before the @ in the E-Mail address
    - **Full name**: this is the name that will be displayed to the recipient
    - **Password**: Just select "generate", on the first login the user will be prompted to change it.
7. **new tab:** Add the Username and password to Vaultwarden under the corresponding collection.
    - It's recommended to copy an existing E-Mail entry by clicking the three dots on the right and selecting "Clone". This way the URL will automatically be filled in correctly.
8. Save the new mailbox.

## Add new E-Mail alias

{: .info-title }
> What you need
> 
> - Someone with access to the "Management" Collection on Vaultwarden

1. Navigate to the [Mailcow admin panel]
2. Log in with the credentials you have.
3. In the Header, choose "E-Mail" > "Configuration"
4. Now switch to the "Aliases" > "Aliases" tab.
5. Select the "Add alias" button.
6. Change:
    - **Alias address**: this is the E-Mail address the alias should be. (e.g. `info@bfp-racing.de`)
    - **Goto address/es**: this is the E-Mail address the alias should forward to (e.g. `contact@bfp-racing.de`)
    - **Alias is visible in SOGo**: if you check this box, the alias will be visible in the Webmail client. This controlls if the user can send from the alias (using the Webmail client, I don't know what happen to other services)
7. Save the new alias.

## Add labels to Emails

{: .info-title }
> What you need
> 
> - Login credentials for the E-Mail account

1. Login to the [Webmail client]
2. Select the E-Mail you want to label
3. In the Top bar, select the 3-Dot-Menu and choose "Add a Tag"
4. Start the tag with the name of a Label.

### How create / add / remove Labels

1. Select the settings Icon in the top right left card, next to the account name.
2. Select Mail in the Navigation menu on the left.
3. Go to the Labels tag
4. Go nuts (create, add, remove labels)
5. Hit the save Icon.
6. Navigate Back to the Email view with the Header

----
[Mailcow admin panel]: https://mail.bfp-racing.de
[Webmail client]: https://mail.bfp-racing.de/SOGo/