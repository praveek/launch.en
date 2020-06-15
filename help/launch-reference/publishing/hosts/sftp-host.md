---
title: SFTP Hosts
seo-title: SFTP Hosts in Adobe Experience Platform Launch
description: Adobe Experience Platform Launch hosts
seo-description: Adobe Experience Platform Launch hosts
---

# SFTP Hosts

If you do not want to have Adobe manage your hosted libraries, your other option is to have Launch deliver builds to a secured SFTP server that you host.

Launch connects to your SFTP site using an encrypted key. There are a few steps to set this up correctly:

1. You must have a public/private key pair installed on your SFTP server.  You can generate these keys on your server or generate them somewhere else and install them to your server.  See [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key)for an example of how to generate keys.
1. You must encrypt the private key with Launch's public GPG key so that you can provide your private key to Launch during the SFTP host creation process.  See [Encrypting Values](https://developer.adobelaunch.com/api/guides/encrypting_values/) in the Launch developer documentation for instructions and Launch's public GPG keys.  Unless you know you need a different one, use the Production Environment's GPG key.  Finally, you can encrypt your private key from any  machine, so you do not need to install GPG on your server to complete this step.
1. You might need to approve the Launch IP addresses with your company firewall to allow Launch to be able to reach your SFTP server and connect to it.  Those IP Addresses are:
   * `35.170.215.3`
   * `34.202.8.57`
   * `52.21.198.46`

There is a full guide on how to setup SFTP servers for Launch delivery [on the Launch blog](https://medium.com/launch-by-adobe/configuring-an-sftp-server-for-use-with-adobe-launch-bc626027e5a6).

## Create an SFTP host

1. Open the [!UICONTROL Hosts] tab.
1. Create the new Host.
1. Name your host.
1. Select **[!UICONTROL SFTP]** as the host type.
1. Enter the host, path, port, username, and encrypted private key.
1. Click **[!UICONTROL Save]**.

When you click **[!UICONTROL Save]**, Launch tests whether it is able to connect and deliver files to your SFTP server. It creates a folder, writes a file within that folder, checks to make sure the file is there, then cleans up after itself. If the user account on your SFTP server (the one attached to the secure certificate you provided to Launch) does not have the necessary permissions to perform this action, then the Host goes into a "Failed" status.
