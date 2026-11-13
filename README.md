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
pod update Mindbox MindboxNotifications
```

Leave out `MindboxNotifications` if no target uses it: `pod update` stops on a pod that is not installed. A plain
`pod install` keeps the versions locked in `Podfile.lock`, and after a plugin update it stops on a version conflict.

The same two lines cover:

- apps that declare `pod 'Mindbox'` directly;
- notification service and content extensions with `pod 'MindboxNotifications'`;
- the React Native (`mindbox-sdk`) and Flutter (`mindbox`) plugins, which take the native pods through the app's
  `Podfile`.

Swift Package Manager users add https://github.com/mindbox-cloud/ios-sdk directly and do not need this repository.

## Troubleshooting

Some versions are published both here and on trunk. For them CocoaPods prints `Found multiple specifications`; the
copies are identical and the warning does not affect the install.

`CocoaPods could not find compatible versions for pod "Mindbox"` (or `"MindboxNotifications"`) ends with one of these
lines:

```text
None of your spec sources contain a spec satisfying the dependency: `Mindbox (= X.Y.Z)`.
Specs satisfying the `Mindbox, Mindbox (= X.Y.Z)` dependency were found, but they required a higher minimum deployment target.
```

CocoaPods did not find that Mindbox version: the `Podfile` lacks this repository, the local copy of it is out of date,
or `Podfile.lock` pins an older version. The second line mentions the deployment target but appears in these cases
too.

Check that both `source` lines are at the top of the `Podfile`, then run
`pod update Mindbox MindboxNotifications` (without `MindboxNotifications` if no target uses it). It updates the
local copies of the sources and the versions in `Podfile.lock`. If the error stays, check that the app's deployment
target is not below the one Mindbox requires.

## Questions

Open an issue in [mindbox-cloud/ios-sdk](https://github.com/mindbox-cloud/ios-sdk/issues).

## Maintenance

The ios-sdk release workflow writes to this repository. Do not edit podspecs by hand.
