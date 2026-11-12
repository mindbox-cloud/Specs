# Mindbox CocoaPods Specs

CocoaPods spec repository for the Mindbox iOS SDK pods: `Mindbox`, `MindboxNotifications` and `MindboxLogger`.

CocoaPods trunk stops accepting new podspecs on December 2, 2026. Mindbox releases from 2.16.0 on are published here,
and releases after that date are available only here. Earlier versions stay on trunk and keep installing as before.

## Usage

Add both sources at the top of your `Podfile`:

```ruby
source 'https://github.com/mindbox-cloud/Specs.git'
source 'https://cdn.cocoapods.org/'
```

Listing any source turns off the implicit CocoaPods source, so keep the CDN line for your other pods.

After you change the Mindbox version (or update the React Native or Flutter plugin), run:

```sh
pod update Mindbox MindboxNotifications MindboxLogger
```

A plain `pod install` keeps the versions locked in `Podfile.lock` and reports a version conflict.

The same two lines cover:

- apps that declare `pod 'Mindbox'` directly;
- notification service and content extensions with `pod 'MindboxNotifications'`;
- the React Native (`mindbox-sdk`) and Flutter (`mindbox`) plugins, which take the native pods through the app's
  `Podfile`.

Swift Package Manager users add https://github.com/mindbox-cloud/ios-sdk directly and do not need this repository.

## Questions

Open an issue in [mindbox-cloud/ios-sdk](https://github.com/mindbox-cloud/ios-sdk/issues).

## Maintenance

The ios-sdk release workflow writes to this repository. Do not edit podspecs by hand.
