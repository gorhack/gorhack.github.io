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

iOS/iPad OS natively support smart card readers and authentication using your Common Access Card (CAC)
through the [CryptoTokenKit](https://developer.apple.com/documentation/cryptotokenkit) framework.
You no longer need to utilize expensive software or hardware devices previously required from third party
sites to use CAC-enabled websites on your Apple mobile devices. Now all you need is an On The Go (OTG) adapter
([1](https://www.apple.com/shop/product/MD821AM/A/lightning-to-usb-camera-adapter),
[2](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter),
[3](https://www.amazon.com/apple-lightning-usb-camera-adapter/s?k=apple+lightning+to+usb+otg+adapter))
to access websites such as [webmail](https://webmail.apps.mil/mail/), [HRC](https://www.hrc.army.mil/),
[DTS](https://www.defensetravel.osd.mil/), etc.

First, you will need to download DoD's PKI Certificate Authority
[certificates](https://public.cyber.mil/announcement/new-dod-pki-cas-released/) onto your Apple device.
Once downloaded, open the `dod_pke_chain.pem` file within the zip file from your downloads folder.
You will install them on your iPhone by clicking it, then navigating to your
`Settings->Profile Downloaded->Install`. Recommend you always verify the certificates are authentic by
following the instructions in the README included in the zip file.

Once installed, plugin your adapter, smart card reader, and CAC and navigate to the webpage of your choice. You
will be prompted to select your certificate and enter your pin.

![Cac Enabled Sites on an iPhone!]({{ site.url }}/assets/images/cac-enabled-sites.png){: .center-image}

I tested this with an iPhone 12 with the
[USB-3 camera adapter](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter)
and a generic OTG lightning to USB3.0 adapter from
[Amazon](https://www.amazon.com/Certified-Lightning-Portable-iPhone13-Keyboard/dp/B09NND4R8N/).
However, this should work with any OTG adapter or
[USB-C smart card reader](https://www.amazon.com/Identiv-SCR3310v2-0-Smart-Card-Reader/dp/B07VVSY96H/)
directly to a USB-C iPad.

Apple's USB-3 camera adapter did require power to the lightning port on the adapter to work,
while the generic OTG adapter did not require anything additional.

![Smart Card Reader Power]({{ site.url }}/assets/images/usb-3-camera-cac.png){: .center-image}

