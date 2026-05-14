# Xiaomi Redmi Note 12 Security Hardening Report

## Complete Command History

```bash
adb devices

adb shell pm list packages | grep google
adb shell pm list packages | grep miui
adb shell pm list packages | grep xiaomi
adb shell pm list packages | grep ads
adb shell pm list packages | grep one
adb shell pm list packages -3
adb shell pm list packages

adb shell pm uninstall --user 0 com.google.android.googlequicksearchbox
adb shell pm uninstall --user 0 com.google.android.as
adb shell pm uninstall --user 0 com.google.android.as.oss
adb shell pm uninstall --user 0 com.google.android.federatedcompute
adb shell pm uninstall --user 0 com.google.mainline.telemetry
adb shell pm uninstall --user 0 com.google.android.adservices.api
adb shell pm uninstall --user 0 com.google.mainline.adservices
adb shell pm uninstall --user 0 com.google.android.feedback
adb shell pm uninstall --user 0 com.google.android.gms.location.history
adb shell pm uninstall --user 0 com.android.hotwordenrollment.okgoogle
adb shell pm uninstall --user 0 com.android.hotwordenrollment.xgoogle

adb shell pm uninstall --user 0 com.miui.analytics
adb shell pm uninstall --user 0 com.miui.daemon
adb shell pm uninstall --user 0 com.miui.bugreport
adb shell pm uninstall --user 0 com.miui.yellowpage
adb shell pm uninstall --user 0 com.miui.thirdappassistant
adb shell pm uninstall --user 0 com.miui.misightservice
adb shell pm uninstall --user 0 com.miui.cloudservice
adb shell pm uninstall --user 0 com.miui.cloudbackup
adb shell pm uninstall --user 0 com.miui.micloudsync
adb shell pm uninstall --user 0 com.miui.virtualsim
adb shell pm uninstall --user 0 com.miui.vsimcore
adb shell pm uninstall --user 0 com.miui.cleaner
adb shell pm uninstall --user 0 com.miui.msa.global

adb shell pm uninstall --user 0 com.xiaomi.discover
adb shell pm uninstall --user 0 com.xiaomi.mipicks
adb shell pm uninstall --user 0 com.xiaomi.joyose
adb shell pm uninstall --user 0 com.xiaomi.ugd
adb shell pm uninstall --user 0 com.xiaomi.calendar
adb shell pm uninstall --user 0 cn.wps.xiaomi.abroad.lite
adb shell pm uninstall --user 0 com.xiaomi.finddevice
adb shell pm uninstall --user 0 com.xiaomi.aiasst.vision
adb shell pm uninstall --user 0 com.xiaomi.cameramind
adb shell pm uninstall --user 0 com.xiaomi.payment
adb shell pm uninstall --user 0 com.xiaomi.scanner
adb shell pm disable-user --user 0 com.xiaomi.midrop

adb shell pm uninstall --user 0 com.google.android.apps.docs
adb shell pm uninstall --user 0 com.google.android.apps.youtube.music
adb shell pm uninstall --user 0 com.google.android.videos
adb shell pm uninstall --user 0 com.google.android.apps.tachyon
adb shell pm uninstall --user 0 com.google.android.apps.subscriptions.red
adb shell pm uninstall --user 0 com.google.android.apps.maps
adb shell pm uninstall --user 0 com.google.android.apps.photos
adb shell pm uninstall --user 0 com.google.android.apps.restore
adb shell pm uninstall --user 0 com.google.android.syncadapters.calendar
adb shell pm uninstall --user 0 com.google.android.projection.gearhead
adb shell pm uninstall --user 0 com.google.android.healthconnect.controller
adb shell pm uninstall --user 0 com.google.android.apps.healthdata
adb shell pm uninstall --user 0 com.google.android.apps.wellbeing
adb shell pm uninstall --user 0 com.google.android.youtube
adb shell pm uninstall --user 0 com.google.android.gm
adb shell pm uninstall --user 0 com.google.android.apps.safetyhub
adb shell pm uninstall --user 0 com.google.android.ondevicepersonalization.services
adb shell pm uninstall --user 0 com.google.android.sdksandbox

adb shell pm revoke com.xiaomi.barrage android.permission.SYSTEM_ALERT_WINDOW
adb shell pm revoke com.xiaomi.barrage android.permission.POST_NOTIFICATIONS

adb shell cmd appops set com.xiaomi.barrage SYSTEM_ALERT_WINDOW ignore
adb shell cmd appops set com.xiaomi.barrage RUN_IN_BACKGROUND ignore
adb shell cmd appops set com.xiaomi.barrage WAKE_LOCK ignore
adb shell cmd appops set com.xiaomi.barrage POST_NOTIFICATION ignore
adb shell cmd appops get com.xiaomi.barrage

adb shell settings get secure enabled_notification_listeners
adb shell settings put secure enabled_notification_listeners com.google.android.projection.gearhead/com.google.android.gearhead.notifications.SharedNotificationListenerManager\$ListenerService

adb shell dumpsys accessibility
adb shell dpm list active-admins
adb shell settings get secure enabled_accessibility_services
adb shell cmd appops query-op SYSTEM_ALERT_WINDOW allow

adb shell getprop ro.crypto.state

mkdir -p ~/android_scan
adb pull /sdcard/Download ~/android_scan
adb pull /sdcard ~/android_scan/full_sdcard

adb reboot
```

## Device Overview

* Device: Xiaomi Redmi Note 12
* OS: MIUI / HyperOS (Android-based)
* Hardening Method: ADB (non-root)
* Host System: Debian 13
* Objective:

  * Reduce telemetry
  * Remove bloatware
  * Reduce Google/Xiaomi tracking
  * Improve operational security
  * Reduce attack surface

---

# Security Actions Performed

## 1. ADB Environment Setup

ADB connectivity verified:

```bash
adb devices
```

USB debugging enabled temporarily for administration.

---

# 2. Google Telemetry & Ad Services Removed

The following telemetry/ad-related Google packages were removed:

```bash
adb shell pm uninstall --user 0 com.google.android.googlequicksearchbox
adb shell pm uninstall --user 0 com.google.android.as
adb shell pm uninstall --user 0 com.google.android.as.oss
adb shell pm uninstall --user 0 com.google.android.federatedcompute
adb shell pm uninstall --user 0 com.google.mainline.telemetry
adb shell pm uninstall --user 0 com.google.android.adservices.api
adb shell pm uninstall --user 0 com.google.mainline.adservices
adb shell pm uninstall --user 0 com.google.android.feedback
adb shell pm uninstall --user 0 com.google.android.gms.location.history
adb shell pm uninstall --user 0 com.android.hotwordenrollment.okgoogle
adb shell pm uninstall --user 0 com.android.hotwordenrollment.xgoogle
```

Impact:

* Reduced telemetry
* Reduced voice-assistant hooks
* Reduced ad personalization
* Reduced background analytics
* Reduced behavioral profiling

---

# 3. Xiaomi Analytics & Advertising Removed

The following Xiaomi telemetry/ad packages were removed:

```bash
adb shell pm uninstall --user 0 com.miui.analytics
adb shell pm uninstall --user 0 com.miui.daemon
adb shell pm uninstall --user 0 com.miui.bugreport
adb shell pm uninstall --user 0 com.miui.yellowpage
adb shell pm uninstall --user 0 com.miui.thirdappassistant
adb shell pm uninstall --user 0 com.miui.misightservice
adb shell pm uninstall --user 0 com.miui.cloudservice
adb shell pm uninstall --user 0 com.miui.cloudbackup
adb shell pm uninstall --user 0 com.miui.micloudsync
adb shell pm uninstall --user 0 com.miui.virtualsim
adb shell pm uninstall --user 0 com.miui.vsimcore
adb shell pm uninstall --user 0 com.miui.cleaner
adb shell pm uninstall --user 0 com.miui.msa.global
```

Impact:

* Removed MIUI ad framework
* Reduced Xiaomi cloud dependency
* Reduced telemetry and analytics
* Reduced recommendation engines

---

# 4. Xiaomi Consumer Services Removed

```bash
adb shell pm uninstall --user 0 com.xiaomi.discover
adb shell pm uninstall --user 0 com.xiaomi.mipicks
adb shell pm uninstall --user 0 com.xiaomi.joyose
adb shell pm uninstall --user 0 com.xiaomi.ugd
adb shell pm uninstall --user 0 com.xiaomi.calendar
adb shell pm uninstall --user 0 cn.wps.xiaomi.abroad.lite
adb shell pm uninstall --user 0 com.xiaomi.finddevice
adb shell pm uninstall --user 0 com.xiaomi.aiasst.vision
adb shell pm uninstall --user 0 com.xiaomi.cameramind
adb shell pm uninstall --user 0 com.xiaomi.payment
```

Impact:

* Reduced cloud integrations
* Removed recommendation systems
* Reduced AI-assisted telemetry
* Reduced attack surface

---

# 5. Google Applications Removed

```bash
adb shell pm uninstall --user 0 com.google.android.apps.docs
adb shell pm uninstall --user 0 com.google.android.apps.youtube.music
adb shell pm uninstall --user 0 com.google.android.videos
adb shell pm uninstall --user 0 com.google.android.apps.tachyon
adb shell pm uninstall --user 0 com.google.android.apps.subscriptions.red
adb shell pm uninstall --user 0 com.google.android.apps.maps
adb shell pm uninstall --user 0 com.google.android.apps.photos
adb shell pm uninstall --user 0 com.google.android.apps.restore
adb shell pm uninstall --user 0 com.google.android.syncadapters.calendar
adb shell pm uninstall --user 0 com.google.android.projection.gearhead
adb shell pm uninstall --user 0 com.google.android.healthconnect.controller
adb shell pm uninstall --user 0 com.google.android.apps.healthdata
adb shell pm uninstall --user 0 com.google.android.apps.wellbeing
```

Removed Applications:

* Google Drive
* YouTube Music
* Google TV
* Google Meet
* Google One
* Google Maps
* Google Photos
* Android Restore
* Android Auto
* Health Connect
* Digital Wellbeing

Impact:

* Reduced Google cloud dependency
* Reduced behavioral analytics
* Reduced location tracking
* Reduced telemetry
* Reduced cloud synchronization

---

# 6. Notification Listener Audit

Notification listeners inspected:

```bash
adb shell settings get secure enabled_notification_listeners
```

Detected:

* Xiaomi Barrage notification monitor

Mitigation applied:

```bash
adb shell cmd appops set com.xiaomi.barrage POST_NOTIFICATION ignore
adb shell cmd appops set com.xiaomi.barrage SYSTEM_ALERT_WINDOW ignore
adb shell cmd appops set com.xiaomi.barrage RUN_IN_BACKGROUND ignore
```

Impact:

* Reduced overlay abuse potential
* Reduced notification monitoring capability
* Reduced background execution

---

# 7. Accessibility Audit

Accessibility services inspected:

```bash
adb shell dumpsys accessibility
```

Findings:

* No suspicious accessibility malware detected
* No unauthorized accessibility service enabled

Impact:

* Reduced risk of accessibility-based spyware/keyloggers

---

# 8. Encryption Verification

Verified:

```bash
adb shell getprop ro.crypto.state
```

Result:

```text
encrypted
```

Impact:

* Device storage encryption active
* Better protection against offline forensic access
* Better protection against physical theft scenarios

---

# 9. Package Audit

Installed packages audited using:

```bash
adb shell pm list packages
adb shell pm list packages -3
```

Goal:

* Detect suspicious software
* Detect hidden bloatware
* Detect telemetry-heavy applications

---

# 10. Recommended Remaining Core Packages

The following packages were intentionally preserved for system stability:

```text
com.google.android.gms
com.google.android.gsf
com.google.android.webview
com.google.android.permissioncontroller
com.google.android.networkstack
com.google.android.packageinstaller
```

Reason:

* Banking app compatibility
* Push notifications
* WebView rendering
* Android networking
* Package installation stability

---

# Package Inventory Removed

## Google Packages Removed

| Package                                             | Purpose                                |
| --------------------------------------------------- | -------------------------------------- |
| com.google.android.googlequicksearchbox             | Google Search / Discover               |
| com.google.android.as                               | Android System Intelligence            |
| com.google.android.as.oss                           | Android System Intelligence OSS Module |
| com.google.android.federatedcompute                 | Federated telemetry / ML               |
| com.google.mainline.telemetry                       | Telemetry module                       |
| com.google.android.adservices.api                   | Android AdServices                     |
| com.google.mainline.adservices                      | Privacy Sandbox AdServices             |
| com.google.android.feedback                         | Feedback / diagnostics                 |
| com.google.android.gms.location.history             | Google location history                |
| com.android.hotwordenrollment.okgoogle              | Voice hotword enrollment               |
| com.android.hotwordenrollment.xgoogle               | Voice hotword enrollment               |
| com.google.android.apps.docs                        | Google Drive                           |
| com.google.android.apps.youtube.music               | YouTube Music                          |
| com.google.android.videos                           | Google TV                              |
| com.google.android.apps.tachyon                     | Google Meet                            |
| com.google.android.apps.subscriptions.red           | Google One                             |
| com.google.android.apps.maps                        | Google Maps                            |
| com.google.android.apps.photos                      | Google Photos                          |
| com.google.android.apps.restore                     | Android Restore Assistant              |
| com.google.android.syncadapters.calendar            | Google Calendar Sync                   |
| com.google.android.projection.gearhead              | Android Auto                           |
| com.google.android.healthconnect.controller         | Health Connect                         |
| com.google.android.apps.healthdata                  | Health Data                            |
| com.google.android.apps.wellbeing                   | Digital Wellbeing                      |
| com.google.android.youtube                          | YouTube                                |
| com.google.android.gm                               | Gmail                                  |
| com.google.android.apps.safetyhub                   | Google Safety Hub                      |
| com.google.android.ondevicepersonalization.services | On-device personalization              |
| com.google.android.sdksandbox                       | Android SDK Sandbox                    |

---

## Xiaomi / MIUI Packages Removed

| Package                    | Purpose                             |
| -------------------------- | ----------------------------------- |
| com.miui.analytics         | Xiaomi telemetry                    |
| com.miui.daemon            | Background analytics daemon         |
| com.miui.bugreport         | Bug reporting                       |
| com.miui.yellowpage        | Yellow pages / recommendations      |
| com.miui.thirdappassistant | Third-party app assistant           |
| com.miui.misightservice    | Diagnostic service                  |
| com.miui.cloudservice      | Xiaomi cloud service                |
| com.miui.cloudbackup       | Xiaomi backup                       |
| com.miui.micloudsync       | Xiaomi sync                         |
| com.miui.virtualsim        | Virtual SIM                         |
| com.miui.vsimcore          | Virtual SIM core                    |
| com.miui.cleaner           | Cleaner utility                     |
| com.miui.msa.global        | MIUI advertising framework          |
| com.xiaomi.discover        | Discover feed                       |
| com.xiaomi.mipicks         | Xiaomi app recommendations          |
| com.xiaomi.joyose          | Optimization/recommendation service |
| com.xiaomi.ugd             | User guidance / recommendations     |
| com.xiaomi.calendar        | Xiaomi calendar                     |
| cn.wps.xiaomi.abroad.lite  | Preinstalled WPS Office             |
| com.xiaomi.finddevice      | Xiaomi device locator               |
| com.xiaomi.aiasst.vision   | Xiaomi AI vision                    |
| com.xiaomi.cameramind      | Camera AI module                    |
| com.xiaomi.payment         | Xiaomi payment service              |

---

# Threat Model Considerations

## Threats Reduced

* Telemetry collection
* Advertising identifiers
* Behavioral analytics
* Recommendation profiling
* Cloud synchronization exposure
* Voice assistant hooks
* Notification monitoring abuse
* Overlay abuse potential
* Background execution of unnecessary services

---

## Threats Still Present

* Baseband/carrier telemetry
* Firmware-level vulnerabilities
* Zero-day browser exploits
* Malicious APK installation
* Supply-chain attacks
* Social engineering attacks
* Physical access attacks
* Banking malware
* Accessibility abuse by future applications

---

# Operational Security (OPSEC)

## Recommended User Practices

* Keep USB debugging disabled except during administration
* Avoid cracked or pirated APKs
* Use strong unique passwords
* Use password managers
* Audit installed packages regularly
* Monitor accessibility permissions monthly
* Monitor notification listeners monthly
* Keep Android/WebView updated
* Use trusted repositories only
* Maintain regular backups

---

## Suggested Security Stack

| Category         | Recommended Tool      |
| ---------------- | --------------------- |
| App Repository   | F-Droid               |
| Maps             | Organic Maps          |
| Password Manager | KeePassDX             |
| Messaging        | Signal                |
| DNS Filtering    | NextDNS / AdGuard DNS |
| File Sync        | Syncthing             |
| Browser          | Firefox / Brave       |

---

# Security Assessment

## Current Security Posture

The device is now:

* Heavily debloated
* Reduced telemetry exposure
* Reduced ad ecosystem exposure
* Reduced cloud dependency
* Reduced attack surface
* More privacy-conscious than stock MIUI

---

# Remaining Risks

The device is NOT immune to:

* Malicious APKs
* Phishing attacks
* Browser exploits
* Fake applications
* Accessibility malware installed later
* Carrier telemetry
* Baseband/firmware vulnerabilities
* Physical attacks on unlocked device

---

# Recommended Operational Security Practices

## Strongly Recommended

* Keep Android updated
* Keep WebView updated
* Disable USB debugging after use
* Use strong PIN/password
* Avoid cracked APKs
* Audit permissions monthly
* Use trusted app sources only

---

# Recommended Tools

## DNS Filtering

Recommended Private DNS:

```text
dns.adguard-dns.com
```

or:

```text
dns.nextdns.io
```

Benefits:

* Malware domain blocking
* Tracker blocking
* Ad blocking
* Phishing protection

---

# Recommended Application Sources

Preferred:

* F-Droid
* Official Play Store
* Official vendor websites

Avoid:

* Modded APK websites
* Telegram APK channels
* Pirated software repositories

---

# Recommended Security-Oriented Applications

| Category         | Recommendation        |
| ---------------- | --------------------- |
| Browser          | Firefox / Brave       |
| Password Manager | Bitwarden / KeePassDX |
| Keyboard         | FUTO Keyboard         |
| Maps             | Organic Maps          |
| File Sync        | Syncthing             |


---

# Final Assessment

The smartphone is now significantly more secure and privacy-respecting than a default Xiaomi stock configuration.

Main improvements achieved:

* Reduced telemetry
* Reduced tracking
* Reduced ad ecosystem exposure
* Reduced attack surface
* Reduced cloud dependency
* Reduced unnecessary privileged services

The device maintains:

* System stability
* Encryption
* Banking compatibility (likely)
* Android core functionality
* Push notification support

This represents a strong non-root Android hardening configuration suitable for a privacy-conscious cybersecurity enthusiast.
