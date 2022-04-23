---
title: Android Overview
icon: material/cellphone-check
---
Android is a secure operating system that has strong [app sandboxing](https://source.android.com/security/app-sandbox), [Verified Boot](https://source.android.com/security/verifiedboot) (AVB), and a robust [permission](https://developer.android.com/guide/topics/permissions/overview) control system.

## Choosing an Android Distribution

When you buy an Android phone, the device's default operating system often comes with invasive integration with apps and services which are not part of the [Android Open Source Project](https://source.android.com/). An example of such is Google Play Services, which has unrevokable privileges to access your files, contacts storage, call logs, SMS messages, location, camera, microphone, hardware identifiers, and so on. These apps and services increase the attack surface of your device and are the source of various privacy concerns with Android.

This problem could be solved by using a custom Android distribution that does not come with such invasive integration. Unfortunately, many custom Android distributions often break the Android security model by not supporting critical security features such as AVB, rollback protection, firmware updates, and so on. Some distributions also ship with [`userdebug`](https://source.android.com/setup/build/building#choose-a-target) builds which expose root via the [Android Debug Bridge](https://developer.android.com/studio/command-line/adb) (ADB) and requires [more permissive](https://github.com/LineageOS/android_system_sepolicy/search?q=userdebug&type=code) SELinux policies to accomodate debugging features, resulting in a further increased attack surface and weakened security model.

Ideally, when choosing a custom Android distribution, you should make sure that it upholds the Android security model. At the very least, the distribution should have production builds, support for AVB, rollback protection, timely firmware and operating system updates, and SELinux in enforcing mode. All of our recommended Android distributions satisfy these criteria.

[Our Android System Recommendations :material-arrow-right:](../android.md){ .md-button }

## Avoid Root

[Rooting](https://en.wikipedia.org/wiki/Rooting_(Android)) Android phones can decrease security significantly as it weakens the complete [Android security model](https://en.wikipedia.org/wiki/Android_(operating_system)#Security_and_privacy). This can decrease privacy should there be an exploit that is assisted by the decreased security. Common rooting methods involve directly tampering with the boot partition, making it impossible to perform successful Verified Boot. Apps that require root will also modify the system partition meaning that Verified Boot would have to remain disabled. Having root exposed directly in the user interface also increases the [attack surface](https://en.wikipedia.org/wiki/Attack_surface) of your device and may assist in [privilege escalation](https://en.wikipedia.org/wiki/Privilege_escalation) vulnerabilities and [SELinux](https://en.wikipedia.org/wiki/Security-Enhanced_Linux) policy bypasses.

Adblockers which modify the [hosts file](https://en.wikipedia.org/wiki/Hosts_(file)) (AdAway) and firewalls (AFWall+) which require root access persistently are dangerous and should not be used. They are also not the correct way to solve their intended purposes. For Adblocking we suggest encrypted [DNS](../dns.md) or [VPN](../vpn.md) server blocking solutions instead. RethinkDNS, TrackerControl and AdAway in non-root mode will take up the VPN slot (by using a local loopback VPN) preventing you from using privacy enhancing services such as Orbot or a real VPN server.

AFWall+ works based on the [packet filtering](https://en.wikipedia.org/wiki/Firewall_(computing)#Packet_filter) approach and may be bypassable in some situations.

We do not believe that the security sacrifices made by rooting a phone are worth the questionable privacy benefits of those apps.

## Firmware Updates

Firmware updates are critical for maintaining security and without them your device cannot be secure. OEMs have support agreements with their partners to provide the closed source components for a limited support period. These are detailed in the monthly [Android Security Bulletins](https://source.android.com/security/bulletin).

As the components of the phone such as the processor and radio technologies rely on closed source components, the updates must be provided by the respective manufacturers. Therefore it is important that you purchase a device within an active support cycle. [Qualcomm](https://www.qualcomm.com/news/releases/2020/12/16/qualcomm-and-google-announce-collaboration-extend-android-os-support-and) and [Samsung](https://news.samsung.com/us/samsung-galaxy-security-extending-updates-knox/) support their devices for 4 years while cheaper products often have shorter support. With the introduction of the [Pixel 6](https://support.google.com/pixelphone/answer/4457705), Google now makes their own system on chip (SoC) and they will provide 5 years of support.

Devices that have reached their end-of-life (EoL) and are no longer supported by the SoC manufacturer, cannot receive firmware updates from OEM vendors or after market Android distributors. This means that security issues with those devices will remain unfixed.

## Android Versions

It's important to not use an [end-of-life](https://endoflife.date/android) version of Android. Newer versions of Android not only receive security updates for the operating system but also important privacy enhancing updates too. For example, [prior to Android 10](https://developer.android.com/about/versions/10/privacy/changes), any user apps with the [`READ_PHONE_STATE`](https://developer.android.com/reference/android/Manifest.permission#READ_PHONE_STATE) permission could access sensitive and unique serial numbers of your phone such as [IMEI](https://en.wikipedia.org/wiki/International_Mobile_Equipment_Identity), [MEID](https://en.wikipedia.org/wiki/Mobile_equipment_identifier), your SIM card's [IMSI](https://en.wikipedia.org/wiki/International_mobile_subscriber_identity), whereas now they must be system apps to do so. System apps are only provided by the OEM or Android distribution.

## Android Permissions

[Permissions on Android](https://developer.android.com/guide/topics/permissions/overview) grant users control over what apps are allowed to access. Google regularly makes [improvements](https://developer.android.com/about/versions/11/privacy/permissions) on the permission system in each successive version. All user installed apps are strictly [sandboxed](https://source.android.com/security/app-sandbox), therefore there is no need to install any antivirus apps. The savings you make from not purchasing or subscribing to security apps is better spent on paying for a supported device in the future.

Should you want to run an app that you're unsure about, consider using a user or work [profile](android/#android-security-privacy).

## User Profiles

Multiple user profiles (Settings → System → Multiple users) are the simplest way to isolate in Android. With user profiles you can limit a user from making calls, SMS or installing apps on the device. Each profile is encrypted using its own encryption key and cannot access the data of any other profiles. Even the device owner cannot view the data of other profiles without knowing their password. Multiple user profiles is a more secure method of isolation.

## Work Profile

[Work Profiles](https://support.google.com/work/android/answer/6191949) are another way to isolate individual apps and may be more convenient than separate user profiles.

A **device controller** such as [Shelter](#recommended-apps) is required, unless you're using CalyxOS which includes one.

The work profile is dependent on a device controller to function. Features such as *File Shuttle* and *contact search blocking* or any kind of isolation features must be implemented by the controller. The user must also fully trust the device controller app, as it has full access to the data inside of the work profile.

This method is generally less secure than a secondary user profile; however, it does allow you the convenience of running apps in both the work and personal profiles simultaneously.

## Verified Boot

[Verified Boot](https://source.android.com/security/verifiedboot) is an important part of the Android security model. It provides protection against [evil maid](https://en.wikipedia.org/wiki/Evil_maid_attack) attacks, malware persistence, and ensures security updates cannot be downgraded with [rollback protection](https://source.android.com/security/verifiedboot/verified-boot#rollback-protection).

Android 10 and above has moved away from full-disk encryption to more flexible [file-based encryption](https://source.android.com/security/encryption/file-based).

Each user's data is encrypted using their own unique encryption key, and the operating system files are left unencrypted. Verified Boot ensures the integrity of the operating system files preventing an adversary with physical access from tampering or installing malware on the device. In the unlikely case that malware is able to exploit other parts of the system and gain higher privileged access, Verified Boot will prevent and revert changes to the system partition upon reboot of the device.

Unfortunately, OEMs are only obliged to support Verified Boot on their stock Android distribution. Only a few OEMs such as Google support custom AVB key enrollment on their devices. Some AOSP derivatives such as LineageOS or /e/ OS do not support Verified Boot even on hardware with Verified Boot support for third party operating systems. We recommend that you check for support **before** purchasing a new device. AOSP derivatives which do not support Verified Boot are **not** recommended.

## VPN Killswitch

Android 7 and above supports a VPN killswitch and it is available without the need to install third party apps. This feature can prevent leaks if the VPN is disconnected. It can be found in ⚙️ Settings → Network & internet → VPN → ⚙️ → Block connections without VPN.

## Global Toggles

Modern Android devices have global toggles for disabling Bluetooth and location services. Android 12 introduced toggles for the camera and microphone. When not in use, we recommend disabling these features. Apps cannot use disabled features (even if granted individual permission) until re-enabled.

## Google

If you are using a device with Google services, either your stock operating system or an operating system that safely sandboxes Google Play Services like GrapheneOS, there are a number of additional changes you can make to improve your privacy. We still recommend avoiding Google services entirely, or limiting Google Play services to a specific user/work profile by combining a device controller like *Shelter* with GrapheneOS's Sandboxed Google Play.

### Advanced Protection Program

If you have a Google account we suggest enrolling in the [Advanced Protection Program](https://landing.google.com/advancedprotection/). It is available at no cost to anyone with two or more hardware security keys with [FIDO](/security/multi-factor-authentication.md#fido-fast-identity-online) support.

The Advanced Protection Program provides enhanced threat monitoring and enables:

- Stricter two factor authentication; e.g. that [FIDO](/security/multi-factor-authentication/#fido-fast-identity-online) **must** be used and disallows the use of [SMS OTPs](/security/multi-factor-authentication/#sms-or-email-mfa), [TOTP](/security/multi-factor-authentication.md#time-based-one-time-password-totp), and [OAuth](https://en.wikipedia.org/wiki/OAuth)
- Only Google and verified third party apps can access account data
- Scanning of incoming emails on Gmail accounts for [phishing](https://en.wikipedia.org/wiki/Phishing#Email_phishing) attempts
- Stricter [safe browser scanning](https://www.google.com/chrome/privacy/whitepaper.html#malware) with Google Chrome
- Stricter recovery process for accounts with lost credentials

 For users that are using the privileged Google Play Services (common on stock operating systems), the Advanced Protection Program also comes with [additional benefits](https://support.google.com/accounts/answer/9764949?hl=en) such as:

- Not allowing app installation outside of the Google Play Store, the OS vendor's app store, or via [`adb`](https://en.wikipedia.org/wiki/Android_Debug_Bridge)
- Mandatory automatic device scanning with [Play Protect](https://support.google.com/googleplay/answer/2812853?hl=en#zippy=%2Chow-malware-protection-works%2Chow-privacy-alerts-work)
- Warning the user about unverified applications

### Advertising ID

All devices with Google Play Services installed automatically generate an [advertising ID](https://support.google.com/googleplay/android-developer/answer/6048248?hl=en) used for targeted advertising. Disable this feature to limit the data collected about you.

On Android distributions with [Sandboxed Google Play](https://grapheneos.org/usage#sandboxed-google-play), go to ⚙️ Settings → Apps → Sandboxed Google Play → Google Settings → Ads and select **Delete advertising ID**.

On Android distributions with privileged Google Play Services (such as stock OSes), the setting may be in one of several locations. Check

- ⚙️ Settings → Google → Ads
- ⚙️ Settings → Privacy → Ads

Depending on your system, you will either be given the option to delete your advertising ID or to "Opt out of interest-based ads". You should delete the advertising ID if you are given the option to, and if you are not, we recommend that you opt out of interested-based ads and then reset your advertising ID.

### SafetyNet and Play Integrity API

[SafetyNet](https://developer.android.com/training/safetynet/attestation) and the [Play Integrity APIs](https://developer.android.com/google/play/integrity) are generally used for [banking apps](https://grapheneos.org/usage#banking-apps). Many banking apps will work fine in GrapheneOS with sandboxed Play services, however some non-financal apps have their own crude anti-tampering mechanisms which might fail. GrapheneOS passes the `basicIntegrity` check, but not the certification check `ctsProfileMatch`. Devices with Android 8 or later have hardware attestation support which cannot be bypassed without leaked keys or serious vulnerabilities.

As for Google Wallet, we don't recommend this due to their [privacy policy](https://payments.google.com/payments/apis-secure/get_legal_document?ldo=0&ldt=privacynotice&ldl=en), which states you must opt-out if you don't want your credit rating and personal information shared with affiliate marketing services.

--8<-- "includes/abbreviations.en.md"
