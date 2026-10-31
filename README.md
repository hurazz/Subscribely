# Subscribely

A small macOS menu bar subscription tracker. Click the credit card icon to see upcoming charges and payment methods.

## Features

- Compact menu bar list with service icons, amount, renewal date, and payment method
- Add and edit subscriptions from Settings
- Light, dark, and system appearance
- Optional Start at Login
- Recurring due date rollover by billing cycle
- Optional macOS notification at 9:00 AM the day before each active subscription is due
- Background version check against the latest public GitHub release, with a link to download it
- Local data storage; no account or bank connection

## Updates

The app checks `https://api.github.com/repos/hurazz/Subscribely/releases/latest` when it launches. Settings shows the installed version and whether a newer published release is available. **Check for updates** opens the GitHub Releases page; downloads and installation remain manual. Publish releases with numeric version tags such as `v1.2.0`, and update `CFBundleShortVersionString` and `CFBundleVersion` in `Info.plist` for each build.

## Build

Requires macOS 13 or later and the Xcode Command Line Tools. Run:

```sh
./build.sh
```

The app bundle is written to `build/Subscribely.app`. The first reminder requires allowing notifications for Subscribely in macOS. For ordinary distribution, sign and notarize the app with an Apple Developer ID.

## Data and backups

Subscription data is stored at `~/Library/Application Support/Subscribely/subscriptions.json`. The first launch of the updated app imports existing subscriptions from the previous WebKit store when there is no JSON file yet. The file survives restarts and can be backed up with Time Machine unless that folder is excluded.

The app bundle, release ZIP, screenshots, icon-generation intermediates, and personal subscription data should not be committed as source. `.gitignore` excludes the generated outputs.

