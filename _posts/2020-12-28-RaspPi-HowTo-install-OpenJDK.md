---
layout: page
title: "How-To Install OpenJDK on a Raspberry Pi"
excerpt: "This post shows how to install the latest release of OpenJDK on a Raspberry Pi…"
---

<br>
This short post explains how to install the latest release of OpenJDK, or any release for that matter on a Raspberry Pi.
At the time of writing (Decemeber 2020), the current release is 15.0.1.

Please note that Oracle supports 64-bit ARM for both Oracle JDK builds and Oracle OpenJDK builds (see [here](https://blogs.oracle.com/java-platform-group/update-on-64-bit-arm-support-for-oracle-openjdk-and-oracle-jdk)). 

<p align="center">
	<img alt="book cover" src="/images/blog/PiPic-small.jpg" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/>
</p>


This post is using **Unbuntu 20.10 (RPi 4/400)** on the newer **Pi 400** but any other Pi models, or any other ARM64 (AArch64) hardware, with any supported 64 bits Linux variants should work. 

<h3>1. Configure your Raspberry Pi</h3>


Installing the OS is straight-forward, just refer to this Raspberry Pi Foundation [document](https://www.raspberrypi.org/software/). Make sure to pick a 64-bit OS.


<h3>2. Download OpenJDK</h3>


Go to [https://jdk.java.net](https://jdk.java.net) and choose a release, either the current one, aka 'GA Release' or 'Ready for use', or an Early-Access build. In any case, make sure to select the **Linux / AArch64**	build. Take note of the selected OpenJDK archive and checksum URLs.

<p align="center">
	<a href="https://jdk.java.net/15/"><img alt="OpenJDK" src="/images/blog/HowTo1.png" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/></a>
</p>


Download the OpenJDK bits.

```
wget -P /tmp https://download.java.net/java/GA/jdk15.0.1/51f4f36ad4ef43e39d0dfdbaf6549e32/9/GPL/openjdk-15.0.1_linux-aarch64_bin.tar.gz
```

💡 You might want to compare and validate the checksum of the downloaded archive. 

```
curl https://download.java.net/java/GA/jdk15.0.1/51f4f36ad4ef43e39d0dfdbaf6549e32/9/GPL/openjdk-15.0.1_linux-aarch64_bin.tar.gz.sha256
sha256sum /tmp/openjdk-15.0.1_linux-aarch64_bin.tar.gz | cut -d " " -f 1
```

<h3>3. Untar OpenJDK</h3>

OpenJDK will be installed under `/usr/lib/jvm`, create this directory if it doesn't exit yet.

```
sudo mkdir -p /usr/lib/jvm
```

Untar the archive in `/usr/lib/jvm`.

```
sudo tar -x -C /usr/lib/jvm -f /tmp/openjdk-15.0.1_linux-aarch64_bin.tar.gz
```

You can now invoke the Java launcher to test the bits.

```
/usr/lib/jvm/jdk-15.0.1/bin/java -version
```

<h3>4. Configure the environment</h3>

```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-15.0.1/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-15.0.1/bin/javac 1
```
💡 Depending on your needs you might want to configure additional JDK tools such as, ex. `jlink`, `javap`, …

Set the Java home.

```
echo 'JAVA_HOME=/usr/lib/jvm/jdk-15.0.1' | sudo tee -a /etc/environment
source /etc/environment
```

<center>~</center>
