fastlane documentation
----

# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```sh
xcode-select --install
```

For _fastlane_ installation instructions, see [Installing _fastlane_](https://docs.fastlane.tools/#installing-fastlane)

# Available Actions

## iOS

### ios unsigned

```sh
[bundle exec] fastlane ios unsigned
```

İmzasız IPA oluştur — AltStore / Sideloadly için

### ios simulator

```sh
[bundle exec] fastlane ios simulator
```

iOS Simulator'da derle ve başlat

### ios dev

```sh
[bundle exec] fastlane ios dev
```

Apple ID ile imzalı IPA — cihaza yüklenebilir (7 gün geçerli)

### ios beta

```sh
[bundle exec] fastlane ios beta
```

TestFlight'a yükle — API Key ile

### ios release

```sh
[bundle exec] fastlane ios release
```

App Store Connect'e gönder

----

This README.md is auto-generated and will be re-generated every time [_fastlane_](https://fastlane.tools) is run.

More information about _fastlane_ can be found on [fastlane.tools](https://fastlane.tools).

The documentation of _fastlane_ can be found on [docs.fastlane.tools](https://docs.fastlane.tools).
