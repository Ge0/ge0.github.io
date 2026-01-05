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

Looking for the `LicenseActivity` pattern in the smali disassembly, we can locate the file responsible for implementing this activity. But this is not the class we are interested in.

Indeed, there is a `LicenseClient` present in the `com.pairip.licensecheck` package. Specifically, it implements an `initializeLicenseCheck` public method, such as follow:

```smali
.method public initializeLicenseCheck()V
    .locals 2

    .line 123
    sget-object v0, Lcom/pairip/licensecheck/LicenseClient;->licenseCheckState:Lcom/pairip/licensecheck/LicenseClient$LicenseCheckState;

    invoke-virtual {v0}, Lcom/pairip/licensecheck/LicenseClient$LicenseCheckState;->ordinal()I

    move-result v0

    if-eqz v0, :cond_2

    const/4 v1, 0x1

    if-eq v0, v1, :cond_1

    const/4 v1, 0x4

    if-eq v0, v1, :cond_0

    return-void

    .line 157
    :cond_0
    invoke-direct {p0}, Lcom/pairip/licensecheck/LicenseClient;->connectToLicensingService()V

    return-void

    .line 148
    :cond_1
    :try_start_0
    sget-object v0, Lcom/pairip/licensecheck/LicenseClient;->responsePayload:Landroid/os/Bundle;

    sget-object v1, Lcom/pairip/licensecheck/LicenseClient;->packageName:Ljava/lang/String;

    invoke-static {v0, v1}, Lcom/pairip/licensecheck/LicenseResponseHelper;->validateResponse(Landroid/os/Bundle;Ljava/lang/String;)V
    :try_end_0
    .catch Lcom/pairip/licensecheck/LicenseCheckException; {:try_start_0 .. :try_end_0} :catch_0

    return-void

    :catch_0
    move-exception v0

    .line 150
    invoke-direct {p0, v0}, Lcom/pairip/licensecheck/LicenseClient;->handleError(Lcom/pairip/licensecheck/LicenseCheckException;)V

    return-void

    .line 125
    :cond_2
    sget-boolean v0, Lcom/pairip/licensecheck/LicenseClient;->localCheckEnabled:Z

    if-eqz v0, :cond_3

    .line 127
    sget-object v0, Lcom/pairip/licensecheck/LicenseClient;->backgroundRunner:Lcom/pairip/licensecheck/LicenseClient$ImmediateTaskExecutor;

    new-instance v1, Lcom/pairip/licensecheck/LicenseClient$$ExternalSyntheticLambda4;

    invoke-direct {v1, p0}, Lcom/pairip/licensecheck/LicenseClient$$ExternalSyntheticLambda4;-><init>(Lcom/pairip/licensecheck/LicenseClient;)V

    invoke-interface {v0, v1}, Lcom/pairip/licensecheck/LicenseClient$ImmediateTaskExecutor;->run(Ljava/lang/Runnable;)V

    return-void

    .line 143
    :cond_3
    invoke-direct {p0}, Lcom/pairip/licensecheck/LicenseClient;->connectToLicensingService()V

    return-void
.end method
```

The trick is simply to override this method to do nothing:

```javascript
Java.perform(() => {
    const LicenseClient = Java.use(
      "com.pairip.licensecheck.LicenseClient"
    );
    
    const constructor = LicenseClient.initializeLicenseCheck;

    constructor.implementation = function() {
      // Do nothing.
      console.log("[+] initializeLicenseCheck() was called.")
    }
});
```

Inject this frida snippet into your app and… Happy hacking!

(I will try to elaborate further another time, as this blog post serves as a self reminder for now.)
