# NCB Mobile: run your agent team from your phone

[← Back to main page](../../README.en.md) · [Tiếng Việt](../mobile.md)

> **Status: in development, not publicly released yet.** This page describes the scope and architecture that have been settled. Test builds will ship through **TestFlight** (iOS) and a **signed APK** (Android); when they exist, the links will appear on this repository's [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases) page.

## What it is for (first-release scope)

You should not have to sit at the main machine to know what your agent team is doing. The NCB Mobile app for iPhone and Android connects to your NextCore Browser so you can:

| Task | Details |
|---|---|
| **See machines and quota** | Machines on the same account, each machine's state, the 5-hour and 7-day quota of every Claude account, and the tabs currently working |
| **Chat with NextCore Command** | Send text and images, receive new messages with push notifications, preview content |
| **Control terminals remotely** | List each machine's tabs, open a new tab, view the screen, type commands, and **approve permission prompts** when an agent asks |
| **Assign work and read the task book** | Hand an issue to an agent, see what is running, waiting and done |
| **Your inbox** | Anything that needs your decision shows up as a question with options you tap to choose |

The terminal screen on the phone is designed for fingers: an extra key row with sticky Ctrl and Alt, a session bar, gestures, and raw keys such as Ctrl-C, single characters and function keys.

## Connection architecture

- **Pairing by QR code plus a short authentication string (SAS).** The phone scans the QR code on the main machine and both sides compare a short code before trusting each other.
- **End-to-end encryption.** Content passing through the relay is encrypted with AES-GCM; the relay only forwards ciphertext. Push notifications (APNs for iOS, FCM for Android) also carry **ciphertext**, never readable content.
- **Tolerates latency and drops.** The relay keeps a queue while the target machine is away; the app reconnects and catches up.
- **NextCore account sign-in on the phone.** Each phone receives a mobile-type device token, and each device can be revoked.
- **Permissions.** Choose a permission level for the phone: view only, type into terminals, or approve destructive actions as well.
- **Same foundation as NextCore Browser.** The app shares the protocol with the desktop version, so anything you can do from the phone is something the main machine already does.

## Technology

The app is built with **Capacitor 8 and React**, following the NEXTCORE DESIGN drawings of each screen (every screen with 5 states at 375, 390, 430 and 768 px). iOS ships through TestFlight (external testing with a public link) and Android through a signed APK.

## Path to the test build

1. **Protocol and bridge in NCB:** events, terminal commands, task book, inbox, a single entry point for app functions. Mostly done, final wiring in progress.
2. **Drawings and app:** drawings for 9 screens plus the Sync and NCB Features screens, a Capacitor app that follows the drawings, NextCore sign-in on the phone. Done.
3. **Real pairing and encrypted channel through the relay, the Terminal screen, push notifications:** in progress.
4. **iOS (TestFlight) and Android (APK) test builds, with a three-step install guide with screenshots:** next.

Every acceptance of NCB Mobile counts only on **the app installed on a real device** (iPhone, Android), not on a web build or an emulator, because push, camera, biometrics and keyboard can only be verified on real hardware.

## Want early access

Watch the [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases) page or [open an issue](https://github.com/kennetvn/nextcore-browser-releases/issues/new/choose) saying you want to join the test build, with your phone OS (iOS or Android).
