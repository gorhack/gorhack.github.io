---
layout: post
title: "Access CAC enabled websites on iOS"
author: "Kyle Gorak"
date: "2023/07/09"
output:
html_document:
keep_md: true
comments: True
tags: [Army, iOS]
---

iOS 16 natively supports smart card readers and your Common Access Card (CAC) through the CryptoTokenKit extension. 
Previously, [militarycac.com](https://militarycac.org/mobile.htm) recommended utilizing expensive software and hardware
from third party sites to use CAC-enabled websites on your iOS device. Now all you need is an adapter 
([1](https://www.apple.com/shop/product/MD821AM/A/lightning-to-usb-camera-adapter), 
[2](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter))
to access websites such as [webmail](https://webmail.apps.mil/mail/), [HRC](https://webmail.apps.mil/mail/), 
[DTS](https://www.defensetravel.osd.mil/), etc. You will need to download the 
[Certificate Authority certificates](https://public.cyber.mil/announcement/new-dod-pki-cas-released/) onto your 
iOS device and open the `dod_pke_chain.pem` file within the zip file. You will install them on your iPhone by clicking
it, then navigating to your `Settings->Profile Downloaded->Install`. Recommend you always verify the certificates are
authentic by following the instructions in the README included in the zip file. 

Once installed, plugin your adapter, smart card reader, and CAC and navigate to the webpage of your choice. You
will be prompted to select your certificate and enter your pin.

![Cac Enabled Sites on an iPhone!]({{ site.url }}/assets/images/cac-enabled-sites.png){: .center-image}

I tested this with an iPhone 12 with the 
[USB-3 camera adapter](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter). 
However, this should work with any adapter or USB-C smart card reader directly to a USB-C iPad.
I did run into some issues with using my exact model of smart card reader where the power provided
by the adapter was insufficient, but this was solved by plugging in a charger to the lightning port on
the adapter.

![Smart Card Reader Power]({{ site.url }}/assets/images/usb-3-camera-cac.png){: .center-image}

