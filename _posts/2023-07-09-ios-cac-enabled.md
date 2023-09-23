---
layout: post
title: "Access CAC enabled websites on iOS"
author: "Kyle Gorak"
date: "2023/07/09"
output:
html_document:
keep_md: true
comments: True
tags: [Army, Military, CAC, iOS, iPadOS, CryptoTokenKit]
---
####Update 22 Sep 2023:
Confirmed the iPhone 15 Pro with a
[USB-C Smart Card reader](https://www.amazon.com/Identiv-SCR3310v2-0-Smart-Card-Reader/dp/B07VVSY96H/)
connected directly to it works without any special connector (you can still use a
USB Type A to USB Type C adapter, if your smart card reader requires it).

###Native Smart Card Support in iOS/iPadOS
Starting with iOS 16 and iPadOS 16.1, Apple
[natively](https://support.apple.com/guide/deployment/use-a-smart-card-on-iphone-and-ipad-dep8b8c8927a/web)
supports smart card readers and authentication, signing, and encryption using your Common Access Card (CAC) through the
[CryptoTokenKit](https://developer.apple.com/documentation/cryptotokenkit) framework.
You no longer need to utilize expensive software or hardware devices previously required from third party
sites to use CAC-enabled websites on your Apple mobile devices. Now all you need is an On The Go (OTG) adapter
([1](https://www.apple.com/shop/product/MD821AM/A/lightning-to-usb-camera-adapter),
[2](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter),
[3](https://www.amazon.com/apple-lightning-usb-camera-adapter/s?k=apple+lightning+to+usb+otg+adapter))
to access websites such as [webmail](https://webmail.apps.mil/mail/), [HRC](https://www.hrc.army.mil/),
[DTS](https://www.defensetravel.osd.mil/), etc.

###Setup
First, you will need to download the DoD's PKI Certificate Authority
[certificates](https://public.cyber.mil/announcement/new-dod-pki-cas-released/) onto your Apple device.
(*note: some websites may require additional certificates, which can be downloaded from
[DISA](https://crl.gds.disa.mil)*). Once downloaded, open the `dod_pke_chain.pem` file within the zip file from your
downloads folder. You will install them on your iPhone by clicking it, then navigating to your
`Settings->Profile Downloaded->Install`. Recommend you always verify the certificates are authentic by following the
instructions in the README included in the zip file.

Once installed, plugin your adapter, smart card reader, and CAC and navigate to the webpage of your choice. You
will be prompted to select your certificate and enter your pin.

![Cac Enabled Sites on an iPhone!]({{ site.url }}/assets/images/cac-enabled-sites.png){: .center-image}

###Certificate Management
All certificates are accessible in `Settings->General->VPN & Device Management->Configuration Profiles`
while the root certificates are managed in `Settings->General->About->Certificate Trust Settings`.

![Certificates]({{ site.url }}/assets/images/cert_management.png){: .center-image}

I tested this with an iPhone 12 with the
[USB-3 camera adapter](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter)
and a generic OTG lightning to USB3.0 adapter from
[Amazon](https://www.amazon.com/Certified-Lightning-Portable-iPhone13-Keyboard/dp/B09NND4R8N/).
However, this should work with any OTG adapter or
[USB-C smart card reader](https://www.amazon.com/Identiv-SCR3310v2-0-Smart-Card-Reader/dp/B07VVSY96H/)
directly to a USB-C iPad.

###Troubleshooting:

####This Connection is Not Private
Click `Show Details->view the certificate` and download
the respective public certificate from [disa](https://crl.gds.disa.mil). 

![Connection is Not Private]({{ site.url }}/assets/images/connection_not_private.png){: .center-image}

For example, IPPS-A currently uses the `DOD SW CA-60` certificate, which is not included in the
`DoD Root CA 3` certificate installed in the Setup above. Selecting the `DOD SW CA-60` in DISA's
[DoD PKI Management](https://crl.gds.disa.mil) and downloading it will allow you to install it.

You may also have to `reduce protections` if you have any additional privacy & security settings enabled for
Safari such as `Advanced Tracking and Fingerprinting Protection` or `Show IP Address` if you have iCloud
Private Relay turned on. 

####Cannot Use Accessory
I did run into some issues with Apple's Lightning to USB 3 Camera Adapter where the power provided by the adapter was
insufficient, but this was solved by plugging in a charger to the lightning port on the adapter.

![Smart Card Reader Power]({{ site.url }}/assets/images/usb-3-camera-cac.png){: .center-image}

