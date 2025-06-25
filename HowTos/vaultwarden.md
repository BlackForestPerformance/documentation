---
title: Password Manager
layout: default
parent: How To
---

# Password Manager
{: .no_toc}
#### Table of Contents
{: .no_toc}
1. TOC
{:toc}

## Add users

{: .info-title }
> What you need
> 
> - Someone with access to "Management" Collection on Vaultwarden
> - Someone with owner rights on the Vaultwarden Organisation or access to the "admin@bfp-racing.de" Vaultwarden Account


1. **admin:**
    1. The user with access to the "Management" Collection logs in to [Vaultwarden].
    2. There is a Note "Vaultwarden Access Token (Admin)" with the "clear" key. Copy the key under "Clear:"
    3. Navigate to the [Admin Panel] and log in using the copied key.
    4. Click on the "Users" tab in the header.
    5. At the bottom of the Page, there is a "Invite User" button. Enter the email of the user and send the invite.
2. **user:**
    1. look through the Mails and accept the invite.
3. **admin:**
    1. The user should now be listed in the "Users" tab.
    2. Go back to [Vaultwarden].
    3. Log into the account with owner privileges.
    4. At the bottom of the sidebar navigate to "Admin Console"
    5. In the sidebar navigate to "Members"
    6. In the top right corner, select "Invite Member"
    7. Enter the email of the user and select the "user" role.
4. **user:**
    1. look through the Mails and accept the invite.
5. Now you probably want to change the permissions of the user. [Change what passwords a user can see and edit]

## Change what passwords a user can see and edit

{: .info-title }
> What you need
> 
> Someone with owner rights on the Vaultwarden Organisation or access to the "admin@bfp-racing.de" Vaultwarden Account

1. **user:** Activate 2FA if not already activated.
    1. Log into Vaultwarden.
    2. Navigate to "Settings" -> "Security" -> "Two-step Login"
    3. Set up 2FA the way you prefer.
2. **admin:**
    1. Log into the account with owner privileges.
    2. At the bottom of the sidebar navigate to "Admin Console"
    3. In the sidebar navigate to "Members"
    4. Select the user you want to change the permissions for.
    5. Switch to the "Collections" tab.
    6. Here you can select Collections and what permissions the user has on them.

## Deactivate / Delete an account

{: .info-title }
> What you need
> 
> Someone with owner rights on the Vaultwarden Organisation or access to the "admin@bfp-racing.de" Vaultwarden Account

1. **admin:**
    1. The user with access to the "Management" Collection logs in to [Vaultwarden].
    2. There is a Note "Vaultwarden Access Token (Admin)" with the "clear" key. Copy the key under "Clear:"
    3. Navigate to the [Admin Panel] and log in using the copied key.
    4. Click on the "Users" tab in the header.
    5. Look or search for the user you want to deactivate.
    6. On the user entry there are four buttons on the right. You can either deactivate or delete the user.
        - Deactivating will prevent the user from logging in but keep the data. Use this option if the User will return later.
        - Deleting will remove the user and all data. Use this option if the user will not return.


----

[Vaultwarden]: https://password.bfp-racing.de
[Admin Panel]: https://password.bfp-racing.de/admin
[Change what passwords a user can see and edit]: #change-what-passwords-a-user-can-see-and-edit
