# EXTERNAL-IPA

This repository contains the original native Swift/Xcode iOS application.
The uploaded source is not a Flutter project: it contains no Dart source,
`pubspec.yaml`, or Flutter tooling. The Xcode project is therefore preserved
under `ios/` instead of being converted into a misleading Flutter layout.

## Layout

```text
EXTERNAL-IPA/
├── ios/
│   ├── ThreeOneOSFive/
│   └── ThreeOneOSFive.xcodeproj/
├── .github/
│   └── workflows/
│       └── ios-unsigned-ipa.yml
├── build_unsigned.sh
├── build_esign_ready_ipa.sh
└── README.md
```

## Build locally

An unsigned iOS archive must be built on macOS with Xcode:

```bash
./build_unsigned.sh
```

The output is:

```text
build/HYper-Regedit-Key-Enabled-unsigned.ipa
```

To verify that the package is ready for signing:

```bash
./build_esign_ready_ipa.sh
```

The GitHub Actions workflow runs the same build and uploads the IPA as a
workflow artifact. It does not sign the app or include a provisioning profile.

## Important limitation

The GitHub-hosted runner must have an Apple-compatible Xcode toolchain.
The build cannot be executed on a Linux runner, and an unsigned IPA cannot be
installed on a normal iPhone without a separate signing/provisioning step.