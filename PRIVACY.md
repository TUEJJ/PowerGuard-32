# Privacy Policy for PowerGuard 32

Last updated: 26 November 2026

This policy covers the Android app "PowerGuard 32 - Charge Limit" (package `com.tuejj.powerguard32`), published on Google Play by the developer TUEJJ.

## Summary

The app does not collect, store on a server, share or sell any personal data. It has no internet access, no ads, no analytics and no user accounts.

## What the app does with data

- **Battery level and charge limit.** The app reads your phone's battery level and sends it, together with the charge limit you chose, over Bluetooth Low Energy to your own ESP32 device. This data goes only to that device. The developer never receives it.
- **Settings on your phone.** The app stores one small flag on your phone (whether the welcome message was shown). It stays on your device and may be included in the device backup that Android offers through your Google account.

The app does not have the Android internet permission, so it cannot send data to the developer or to anyone else over the network.

## Permissions

| Permission | Why the app asks for it |
|---|---|
| Nearby devices (Bluetooth scan and connect), Android 12 and newer | To find and connect to your ESP32. The app declares that it does not use Bluetooth scans to derive your location. |
| Location, Android 11 and older only | On these Android versions the system requires the location permission for every Bluetooth Low Energy scan. The app does not read, store or transmit your location. |
| Notifications, Android 13 and newer | To show the status notification with connection state, limit and battery level. |
| Foreground service (connected device) | To keep reporting the battery level to your ESP32 while the app is in the background. |

You can withdraw permissions at any time in the Android settings. Without the Bluetooth permission (or location on Android 11 and older) the app cannot find the ESP32.

## Third parties

The app contains no third-party advertising, analytics or tracking code.

Versions up to 0.2.12 (2023) showed a banner ad through Google AdMob, which could process the advertising ID and device information under Google's privacy policy. This was removed completely in version 0.3.0. If you still have an old version installed, update it.

The app contains a link to the project page on GitHub. If you open it, your browser loads that page and GitHub's own privacy policy applies.

## Children

The app is a technical tool and is not directed at children. It collects no data from anyone.

## Deleting data

Because nothing is collected, there is nothing to delete on the developer's side. Uninstalling the app removes the setting stored on your phone.

## Changes

If this policy changes, the new version is published at this address with a new date.

## Contact

Questions about this policy: contact@tuejj.com
