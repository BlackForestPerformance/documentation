---
title: File Storage and Sharing
layout: default
parent: How To
---

# File Storage and Sharing
{: .info-title }
{: .no_toc}

#### Table of Contents
{: .no_toc}

1. TOC
{:toc}

We have to differentiate between two (actually three) types of file storage:

1. **File Sharing**: Send a file to someone else, it's just too big to send via email or WhatsApp.
2. **File Storage**: Store files in a cloud, accessible by multiple people. In a convenient place, just to collaborate with everyone.
3. **Large File Storage**: Store files in a cloud, accessible by less people. This one is for large amounts of data, like Images or Videos. This is mainly for the Marketing and Media Team. If you have something to put there, talk to them.

## File Sharing

So you want to get that big file to someone else? Or maybe another device of yours?

We use the solution of the HFU (actually RWTH Aachen) for this.<br/>
It's called [GigaMove].

This will let you upload files up to 100 GB and share a link to download it with someone else.
Keep in mind that the files are only available for 7 days (or so). After that, they will be deleted.

## File Storage

Our standard solution is the [Felix Course].

There should be a place for every use-case. If you need a new one, just ask the IT Team, and we will create it for you.

## Large File Storage

This is a special case.<br/>
The Marketing and Media Team has had its own, thrown-together, solution since the beginning of time. But we are working on a new, larger solution for this.

Parts of the files are already copied to the new solution, but we will have to update it when we switch in the future.

The solution im talking about is [BwSync&Share].

The HFU IT told us they can't make a storage account without a person behind it, but they can give a person a larger amount of storage; if needed.

### How to get access

You can open [BwSync&Share] in your browser and log in with your HFU credentials.

If you already have access to the shared folder, you can see it under "Shares" or "Shared with you."

If you don't have access, ask the IT or Marketing Team for access.

#### WebDav

You can use the WebDav protocol to use it directly in your Windows explorer.

To do this, go to the [BwSync&Share] website and log in.

Then go to "File Settings" and "WebDAV."
![Screenshot](https://i.imgur.com/0lgeRC3.png)

Below your WebDav URL, you can find a link to add an Application password.

Here, add a new password and copy both username AND password.
![Screenshot](https://i.imgur.com/FLd3y66.png)
![Screenshot](https://i.imgur.com/0KCTklU.png)

**Windows:**

You can go to "This PC", right click and select "Add a network location."
![Screenshot](https://i.imgur.com/TKHvLVj.png)

Just follow the process, add your URL, then fill in the username and password you generated earlier.

I don't have a screenshot for this, but it should be simple.

If this doesn't work for any reason, don't try 100 times; they will lock your account for too many failed attempts.

#### Windows, Linux, Mac, Android, iOS Client

There is a client for all platforms available.

You can find them on a [NextCloud page].

----

[GigaMove]: https://gigamove.rwth-aachen.de/
[Felix Course]: https://felix.hs-furtwangen.de/url/RepositoryEntry/25429284
[BwSync&Share]: https://bwsyncandshare.kit.edu/
[NextCloud page]: https://customerupdates.nextcloud.com/kk1eoZCTo0kI5HpGE3IT/
