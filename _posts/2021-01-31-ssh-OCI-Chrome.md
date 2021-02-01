---
layout: page
title: "Connecting to an OCI instance using the Chrome Secure Shell Extension"
excerpt: "It is sometimes tricky to use SSH on older Windows versions. An alternative solution is to use Chrome Secure Shell Extension…"
redirect_from:
  - /ssh-chrome/
  - /ssh-OCI-Chrome/
---

It is sometimes tricky to use SSH on older Windows versions. An alternative solution is to use Chrome Secure Shell Extension. 

* When creating your OCI instance make sure to save your SSH key pairs, both the **private** and the **public key**.


<p align="center"><img alt="save keys" src="/images/doc/chrome-ssh-oci.png" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/></p>

* Install the Chrome [Secure Shell Extension](https://chrome.google.com/webstore/detail/secure-shell-dev/algkcnfjnajfhgimadimbjhmpaeohhln?hl=en), and not the deprecated _"Chrome Secure Shell Application"_!

* In Chrome, launch the extension (see top-right).

<p align="center"><img alt="start ssh extension" src="/images/doc/chrome-ssh-start.png" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/></p>

* Select **Connection dialogue** ➡ **New connection**.

<p align="center"><img alt="ssh popup" src="/images/doc/chrome-ssh-popup.png" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/></p>

* Fill in the username (ex. "opc"), the instance public IP address, and give the connection a name (ex. "OCI").

* Click **Import** to import an identity, and select the private key (the `ssh-202*` file  with a `.key` extension). Do note that both the public and private keys should be located in the same directory!

* Select **[ENTER] Connect**.

* If you need to establish a second connection, just launch th extension again in a new Chrome tab.

<div class="infobox">
⚠️  
	<div class= "infoboxcol">Make sure to fully assess and validate this extension when using it with sensible SSH keys!.
	</div>
</div>	

