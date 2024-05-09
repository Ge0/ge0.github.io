---
layout: post
title: "Pretend To Install An APK From The PlayStore"
categories: Tech
comments: true
---
As usual, I am not maintaining a regular pace of posting on this blog, as not only don’t I have anything interesting to say, but besides, I’m being occupied with actual projects.

Thus being said, I’m going to share a little tip today that I want to remember somehow since I sometimes need to use it and that it doesn’t stick in my mind.

If you’re not familiar with the terms “APK” and “PlayStore”, this article is not relevant to you. Otherwise, keep reading.

## Detecting whether an app has been installed from the official Android PlayStore: a programmatic check

Some apps deny any further access when you try to install them outside of the official PlayStore. They can process through this simple check:

```java
boolean verifyInstallerId(Context context) {
    // A list with valid installers package name
    List<String> validInstallers = new ArrayList<>(Arrays.asList("com.android.vending", "com.google.android.feedback"));

    // The package name of the app that has installed your app
    final String installer = context.getPackageManager().getInstallerPackageName(context.getPackageName());

    // true if your app has been downloaded from Play Store 
    return installer != null && validInstallers.contains(installer);
}
```

Source: https://stackoverflow.com/questions/37539949/detect-if-an-app-is-installed-from-play-store

As you can read, the installer’s package name has to be either `com.android.vending` or `com.google.android.feedback`. If it’s not,
the `verifyInstallerId` will return `false` and, upon this case, you may be prompted to leave the app or whatsoever.

It’s quite easy to bypass. A naive solution would be to use apktool, force the boolean to `true` then rebuild it, sign it, reinstall it, etc.

But there is a smarter way:

## Installing the app through adb with the accurate files

First, get the APK of your choice and push it to the `/data/local/tmp` folder of your phone:

```bash
$ adb push my-app.apk /data/local/tmp
```

Then shell into your device:

```bash
$ adb shell
```

Now, `cd` into the `folder` and execute the `pm command as shown below:

```bash
$ cd /data/local/tmp
/data/local/tmp $ pm install -i com.android.vending my-app.apk
```

Note the usage of the `-i` flag above. It lets you specify the package name of the "installer" app.

Nothing more to add. Happy hacking!
