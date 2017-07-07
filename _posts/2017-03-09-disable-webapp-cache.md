---
layout: post
title: disable-webapp-cache.md
author: Antoine
tags: [Antoine,azure]
---
# Disabling caching a webapp

By default, Azure is caching files to speed-up the access to your Web app.

This may be inconvenient when you are developing and frequently uploading files on the FTP server for instance.

You can reach a state where:  `main.js` has been erased on the FTP, but `main.js` is availabke through your browser.

On www.portal.azure.com:

- Go to your Webapp page
- Select `Application settings`
- Scroll down to `App settings`
- Add the key `WEBSITE_DYNAMIC_CACHE` with the value `0`

And voilà !

Don't forget to reenable it once you are done developing.
