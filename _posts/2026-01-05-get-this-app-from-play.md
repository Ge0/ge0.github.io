---
layout: post
title: "Get this app from play"
date: 2026-01-05
categories: Tech
---

Recently, we have seen errors when sideloading Android apps, outside of the Google Play Store.

(image)

This article aims at understanding while this error arise, and how to circumvent it when we want to audit a 3rd-party app.

## First steps: fetch and disass the apk.

Start by pulling your app with `adb pull` and then disassemble the "base" apk (if it is a split one, which is likely to be) with `apktool`.

## Launch the app.

When launching the side-loaded app, you obviously get redirected to an error message stating that you need to get the app from Google Play. In between, in the logcat, you may see this line:

```
ActivityTaskManager: Activity top resumed state loss timeout for ActivityRecord{1870271 u0 com.app/com.pairip.licensecheck.LicenseActivity t-1 f}}
```

Note: I have hidden the original app’s package name and put `com.app` in the output.