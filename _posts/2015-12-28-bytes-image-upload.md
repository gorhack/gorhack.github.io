---
layout: post
title: "BytesIO to POST file with requests"
author: "Kyle Gorak"
date: "2015/12/28"
output:
  html_document:
    keep_md: true
comments: True
tags: [Python 3, requests, BytesIO, image, file, upload, programming, POST, GET, http]
---

I have been working on a project that prohibits me from saving files to disk. In my case, I needed to download an image from a website and upload that image elsewhere.

#### GET the file as a Byte Stream

This can be done using only [requests](http://docs.python-requests.org/en/latest/) and [BytesIO](https://docs.python.org/3.5/library/io.html#io.BytesIO); no need for [Pillow](https://pillow.readthedocs.org/en/3.0.x/) or any other file manipulation modules! After getting the file through a GET request (`r = requests.get(url)`), read the response [as bytes](http://docs.python-requests.org/en/latest/user/quickstart/#binary-response-content) using `r.content`. These bytes can be used to create a BytesIO object `file = BytesIO(r.content)`.

#### POST the file for upload

Now that you have a BytesIO object, requests can send that object as a [file parameter](http://docs.python-requests.org/en/latest/user/quickstart/#post-a-multipart-encoded-file). Use the `getvalue()` method to read the entire buffer of the BytesIO object. Create the files parameter for the requests encoded-file upload: `files = { 'file':file.getvalue() }`. Now that the parameters are ready, the file is ready for upload `r = requests.post(url, files=files)`.

Putting it all together:
{% gist gorhack/2b09b603a8b2d6e8cbb9 %}

There you have it, upload a file without ever saving it to disk.