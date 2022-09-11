---
title: iOS Overview
icon: material/apple-ios
---
iOS is the operating system that runs on iPhones. iOS is a good choice if you want privacy and security without much effort.

## Configuration

You should consider changing these settings to improve your privacy.

### iCloud

Apple uses **iCloud** to sync your settings, photos, documents, apps, etc. to your other devices. Some of these are E2EE, while others are merely encrypted in transit. You can check [Apple's documentation](https://support.apple.com/en-us/HT202303) for information on which services are E2EE. If something is not E2EE, it may be possible for Apple to access it without your permission. You should disable anything you do not want backed up to **iCloud**.

!!! warning

    Enabling iCloud Backup stores a key for your iMessage messages in iCloud. If you do not wish to store a copy of your iMessage keys, disable iCloud Backup.

On the top of the page, there will be an option with your name on it. Select it, then turn off the switch for services you don't want to sync with iCloud. The apps you see here might vary depending on which apps you have installed that support iCloud, so we won't list them. Instead, here are some highlights:

**Private Relay** is a proxy service that relays your Safari traffic through two servers: one owned by Apple and one owned by Cloudflare. You must purchase [**iCloud+**](https://support.apple.com/en-us/HT201318) to utilize this feature.

Select **Private Relay (Beta)**

- [x] Turn on **Private Relay (Beta)**

You can choose to either **Maintain your general location** to get more localized results, or just use your **country and time zone** to get a broader IP address location.

Select **IP Address Location**

- [x] Select **Use country and time zone**

**Hide My Email** is Apple's email aliasing service for iCloud mail. You must purchase [**iCloud+**](https://support.apple.com/en-us/HT201318) to utilize this feature.

### Media & Purchases

You can disable **Personalized Recommendations** on Apple services.

On the top of the page, there will be an option with your name on it. Select it, then

Select **Media & Purchases**

- [ ] Turn off **Personalized Recommendations**

### Find My

**Find My** is a service that lets you track your Apple devices and share your location with your friends and family. You can disable it if you do not wish to use this feature.

On the top of the page, there will be an option with your name on it. Select it, then

Select **Find My** > **Find My iPhone**

- [ ] Turn off **Find My iPhone**

- [ ] Turn off **Find My network**

- [ ] Turn off **Send Last Location**

### Airplane Mode

Enabling **Airplane Mode** will allow you to stop your phone from contacting cell towers. Obviously, you won't be able to use cellular data while it is enabled. You will still be able to connect to Wi-Fi and Bluetooth, so whenever you are connected to Wi-Fi you can turn this setting on.

- [x] Turn on **Airplane Mode**

### Wi-Fi

You can enable hardware address randomization to protect you from tracking across Wi-Fi networks.

On the network you are currently connected to, press the :material-information: button.

- [x] Turn on **Private Wi-Fi Address**

- [x] Turn on **Limit IP Address Tracking**

### Bluetooth

**Bluetooth** should be disabled when you aren't using it.

- [ ] Turn off **Bluetooth**

### General

Your iPhone's device name will by default contain your Apple ID, and this will be visible on networks you connect to. You should change this to something more generic, like "iPhone."

Select **About** > **Name**

Enter the device name you prefer.

It is important to install **Software Updates** frequently to get the latest security fixes. You can enable **Automatic Updates** to keep your phone up-to-date without needing to constantly check for updates.

Select **Software Update** > **Automatic Updates**

- [x] Turn on **Download iOS Updates**
- [x] Turn on **Install iOS Updates**

**AirDrop** allows you to easily transfer files, but it can allow strangers to send you files you do not want.

- [x] Select **AirDrop** > **Receiving Off**

**AirPlay** lets you seamlessly stream content from your iPhone to a TV; however, you might not always want this.

Select **AirPlay & Handoff** > **Automatically AirPlay to TVs**

- [x] Select **Never**

**Background App Refresh** allows your apps to refresh their content while you're not using them. This may cause them to make unwanted connections. Turning this off can also save battery life.

Select **Background App Refresh** > **Background App Refresh**

- [x] Select **Off**

## Siri & Search

If you don't want anyone to be able to control your phone with Siri when it is locked, you can turn that off here.

- [ ] Turn off **Allow Siri When Locked**

### Touch ID & Passcode

Setting a strong password on your phone is probably the most important step you can take for security and privacy. You'll have to make tradeoffs here between security and convenience; a longer password will be annoying to type in every time, but a shorter password or pin will be easier to guess. Setting up Touch ID or Face ID along with a strong password can be a good compromise between usability and security.

Select **Turn Passcode On** > **Passcode Options** > **Custom Alphanumeric Code**

Set a password that you won't forget. The longer, the better. It might be easier for you to string a few words together and break them up with numbers and symbols.

If you wish to use Touch ID, you can go ahead and set it up now. Your phone will use the password you set up earlier as a fallback in case your fingerprint verification fails. This is just for convenience; if someone gets your fingerprint, they can unlock your phone (although after turning off your phone it will require the password and won't accept your fingerprint).

Select **Add a Fingerprint...**

Follow the onscreen prompts to set up Touch ID.

**Allow Access When Locked** gives you options for what you can allow when your phone is locked. The more of these options you disable, the less someone without your password can do, but it will be less convenient for you. Pick and choose which of these you don't want someone to have access to if they get their hands on your phone.

- [ ] Turn off **Today View and Search**
- [ ] Turn off **Notification Center**
- [ ] Turn off **Control Center**
- [ ] Turn off **Reply with Message**
- [ ] Turn off **Home Control**
- [ ] Turn off **Wallet**
- [ ] Turn off **Return Missed Calls**
- [ ] Turn off **USB Accessories**

You can set your phone to wipe itself after 10 failed passcode attempts, keeping you safe from brute-force attacks; however, your phone will already resist these by making you wait long periods of time after multiple failed attempts.

!!! warning

    With this setting enabled, someone could intentially wipe your phone by entering the wrong password many times. Make sure you have proper backups and only enable this setting if it fits your threat model.

- [x] Turn on **Erase Data**


### Privacy

**Location Services** allow you to use features like Find My and Maps. If you do not need these features, you can disable Location Services. You can also pick which apps can use your location.

Select **Location Services**

- [ ] Turn off **Location Services**

You can decide to allow apps to request to **track** you here. Disabling this disallows all apps from tracking you with your phone's advertising ID.

Select **Tracking** 

- [ ] Turn off **Allow Apps to Request to Track**

You should turn off **Research Sensor & Usage Data** if you do not wish to participate in studies.

Select **Research Sensor & Usage Data**

- [ ] Turn off **Sensor & Usage Data Collection**

You should disable **Analytics & Improvements** if you do not wish to send Apple usage data.

Select **Analytics & Improvements**

- [ ] Turn off **Share iPhone Analytics**

Disable **Personalized Ads** if you do not want targeted ads.

Select **Apple Advertising**

- [ ] Turn off **Personalized Ads**

**App Privacy Report** is a built-in tool that allows you to see what permissions your apps are using.

Select **App Privacy Report**

- [x] Select **Turn On App Privacy Report**

### Safari

**Prevent Cross-Site Tracking** enables WebKit's [Intelligent Tracking Protection](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp). The feature helps protect against unwanted tracking by using on-device machine learning to stop trackers. ITP protects against many common threats, but it does not block all tracking avenues because it is designed to not interfere with website usability.

- [x] Turn on **Prevent Cross-Site Tracking**

Privacy Report provides a snapshot of cross-site trackers currently prevented from profiling you on the website you're visiting. It can also display a weekly report to show which trackers have been blocked over time.

Privacy Report is accessible via the Page Settings menu (:pg-textformat-size:).

Ad click measurement has traditionally used tracking technology that infringes on user privacy. [Private Click Measurement](https://webkit.org/blog/11529/introducing-private-click-measurement-pcm/) is a WebKit feature and proposed web standard aimed towards allowing advertisers to measure the effectiveness of web campaigns without compromising on user privacy.

- [ ] Turn off **Privacy Preserving Ad Measurement**

The feature has little privacy concerns on its own, so while you can choose to leave it on, we consider the fact that it's automatically disabled in Private Browsing to be an indicator for disabling the feature.

If you do not use Apple Pay, you can toggle off the ability for websites to check for it.

- [ ] Turn off **Allow websites to check for Apple Pay and Apple Card**

Safari can be set to always open in a private tab. Open Safari and tap the Tabs button, located in the bottom right. Then, expand the Tab Groups list.

- [x] Select **Private**

Safari's Private Browsing mode offers additional privacy protections. Private Browsing uses a new [ephemeral](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/1410529-ephemeral) session for each tab, meaning tabs are isolated from one another. There are also other smaller privacy benefits with Private Browsing, such as not sending a webpage’s address to Apple when using Safari's translation feature.

Do note that Private Browsing does not save cookies and website data, so it won't be possible to remain signed in to sites. This may be an inconvenience.

##### iCloud Sync

Synchronization of Safari History, Tab Groups, iCloud Tabs, and saved passwords are E2EE. However, bookmarks are [not](https://support.apple.com/en-us/HT202303). Apple can decrypt and access them in accordance with their [privacy policy](https://www.apple.com/legal/privacy/en-ww/).

If you use iCloud, we also recommend checking to ensure Safari's default download location is set to locally on your device. This option can be found in :gear: **Settings** → **Safari** → **General** → **Downloads**.

## Privacy/Security Tips

### E2EE Calls

Normal phone calls made with the Phone app are not E2EE. For E2EE audio and video calls, you can use FaceTime or another app like Signal.

Open **Contacts**

Select the name of the person you wish to call

Under FaceTime, there is a camera icon and a phone handset icon. Select the camera to make a video call and the phone icon to make an audio-only call.

### Avoid Jailbreaking

Jailbreaking an iPhone defeats its security and makes you vulnerable. Running untrusted, third-party software could cause your device to be infected with malware.

### Encrypted iMessage

The color of the message bubble in iMessage indicates whether your messages are E2EE or not. A blue bubble indicates that your messages are using E2EE, while a green bubble indicates they are using the outdated SMS and MMS protocols. Currently, the only way to get E2EE in iMessage is for both parties to be using Apple devices.

If either you or your messaging partner have iCloud backup enabled, the encryption key will be stored on Apple's servers, meaning they can access your messages. Disabling this setting will mean that Apple won't be able to access your messages.

### Password or TouchID/FaceID?

Whether you choose to use TouchID/FaceID or just a regular password on your phone will be determined by your threatmodel. If you are worried about people accessing your phone without your knowledge who might use your fingerprint/face to unlock your phone, such as a roommate or a partner, then you should only use a regular password.

If you are worried about people looking over your shoulder and seeing your password when you enter it, then you should use TouchID/FaceID.

### Airplane Mode

Airplane mode will disable your phone's cellular modem, so it will not be able to ping cell towers. Towers can see that your phone pinged off of them and how far away it is; this is fundamental to how cell networks function. Whenever you don't need cell data, you can turn on airplane mode so that cell towers can't see you.

### Blacking Out Faces/Information

If you need to hide information in a photo, you can use Apple's built-in tools to do so. Open the photo you want to edit, press edit at the top right corner of the screen, then press the markup symbol at the top right. Press the plus at the bottom right of the screen, then press the rectangle icon. Now you can place a rectangle anywhere on the image. Make sure to press the shape icon at the bottom left and select the filled-in rectangle.

--8<-- "includes/abbreviations.en.md"