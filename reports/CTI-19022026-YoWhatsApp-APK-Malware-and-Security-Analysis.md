**source location : https://apkpure.net/tw/yo-whatsapp/com.yowhatsapp/download**

**downloaded file :  Yo_WhatsApp_2.22.17.76_APKPure.apk**

### Executive Summary

YoWhatsApp (YoWA / YOWA) is an **unofficial, third-party modified version** of WhatsApp Messenger. It is **not** developed, endorsed, or supported by Meta.

**Purpose**  
To provide power users with restricted/omitted features: per-contact privacy controls, deep UI themes, auto-reply, scheduler, bulk messaging, etc.

**Core Mechanism**  
Patched fork of official WhatsApp v2.22.17.76 that connects to the **same Meta servers** (preserving E2EE) while injecting client-side mods.

**Key Risks**  
- High ban risk (violates ToS).  
- History of malicious forks (Kaspersky 2022 Triada Trojan).  
- This build: clear-text traffic, weak AES/ECB, exposed Google API key, malware-like permissions.  
- Sideloaded from untrusted mirrors → supply-chain risk.  
- Associated website (yowamod.app) shows amateur security practices (outdated plugins, weak TLS, missing headers).

**Recommendation**  
**Do not use** for sensitive communication. Use official WhatsApp only.

---

### 1. App Identification & Developer Lineage

- **Package name:** `com.yowhatsapp`  
- **Version:** 2.22.17.76 (~99 MB)  
- **Developers:**  
  - Original creator: **Yousef Al-Basha** (also referred to as **Nawzad Yousef** / “Yousef”) – visible in code paths `com/yowhatsapp/youbasha/` and site authorship.  
  - Current maintainer: **Fouad Mokdad** (FouadMods) – also behind FMWhatsApp & GBWhatsApp. He received permission from Yousef after the original developer stopped updates for personal reasons.  
- **Signature:** Unsigned/self-signed.  
- **Distribution:** Third-party sites (yowamod.app, yowhts.com, yowayousef.app, APKPure). No Play Store listing.

---

### 1.5 Website & Domain OSINT (yowamod.app) – New Section

**Domain Registration (RDAP):**  
- Registered: **2024-05-02**  
- Expires: 2026-05-02  
- Nameservers: Cloudflare (gail.ns.cloudflare.com, vick.ns.cloudflare.com)  
- Status: clientTransferProhibited  
- Google site verification present.

**Wayback Machine Timeline**  
- **2 May 2024** (earliest capture): Site under development using **default WordPress template** (placeholder “Études” architecture firm content – no YoWhatsApp mention).  
- **15 May 2024**: Fully developed site with YoWhatsApp download pages, features, and author bio.

**Author / Social Media Listed on Site**  
- **Nawzad Yousef** (listed as “Yousef” / Author)  
  Bio: “Hi, I am Yousef, a big fan of WhatsApp that’s why I love to share all about Yowa through this blog.”  
- Social links:  
  - Instagram: https://www.instagram.com/nawzad_yousef/  
  - Threads: https://www.threads.com/@nawzad_yousef  
  - X: https://x.com/NawzadYousef (8 followers, low activity)  
  - Facebook: https://www.facebook.com/profile.php?id=100007232895911  
  - TikTok: https://www.tiktok.com/@nawzadyousef  

**Activity Observation**  
Instagram / Threads / X: **Not actively posting**.  
TikTok & Facebook: **Actively used**, but content is personal/lifestyle – **no coding, development, or technical posts** directly linking to YoWhatsApp or website building.

**Security Scan Results (Nuclei-style)**  
- **WAF:** Cloudflare + ApacheGeneric + Wordfence (yet scanning still succeeded – likely free-tier or relaxed rules).  
- **Critical:** CVE-2024-2473 (WPS Hide Login bypass via `?action=postpass`).  
- **Outdated Plugins** (high risk): Akismet 5.4, Ad Inserter 2.8.3, All-in-One WP Migration 7.94, Shortcodes Ultimate 7.4.0, WP Rocket 3.18.3, WordPress SEO 25.2, WP Mail SMTP 4.4.0, etc.  
- **TLS Issues:** Deprecated TLS 1.0 & 1.1, weak ciphers (ECDHE-ECDSA-AES128-CBC-SHA).  
- **Missing Headers:** No HSTS, CSP, X-Frame-Options, Referrer-Policy, etc.  
- **Other:** XML-RPC enabled, user enumeration (“Yousef”), default readme/license files exposed, GeneratePress theme + many plugins.  

**Note on Cloudflare Scanning**  
Even with Cloudflare protection, the scan completed because many free-tier or misconfigured setups still allow direct access to /wp-admin, /xmlrpc.php, plugin readme.txt, etc. This is common for hobbyist sites.

---

### 2. How the App Works (Technical Breakdown)

#### 1. Core Engine
- Reuses official WhatsApp protocol (Noise + Signal Double Ratchet for E2EE).  
- Registers/authenticates via phone number on Meta servers (`pps.whatsapp.net`, `crashlogs.whatsapp.net`, graph.instagram.com, etc.). All server IPs in the scan resolve to Meta/Facebook infrastructure (Hong Kong edge locations/CDN).

#### 2. Modifications Added
- Custom package `com/yowhatsapp/yo/` and `com/yowhatsapp/youbasha/` contain:  
  - `yo.java`, `HomeUI.java`, `Conversation.java` → UI overrides.  
  - `autoschedreply/`, `massmsger/`, `YTranslate.java` → background services for scheduler, bulk sender, translator.  
  - Theme engine (downloads 4000+ themes).  
  - Business Directory map views, UPI payments hooks, hidden services (`YoHiddenService`).  
- Privacy hooks: intercept “online”, “typing”, “blue ticks”, “deleted for everyone” messages **client-side**.  
- App lock (fingerprint/biometric), DND mode, status downloader, anti-delete viewer.

#### 3. Persistence & Background Behavior
- `RECEIVE_BOOT_COMPLETED`, `FOREGROUND_SERVICE`, `WAKE_LOCK` → starts on boot and stays alive.  
- Custom receivers for auto-reply, backups, notifications.

**Result:** The app behaves like official WhatsApp for sending/receiving messages/calls, but locally adds dozens of extra controls and visual changes.

---

### 3. Permission Analysis (Why It Looks Like Malware)

The scan flags **top-tier malware permissions**:

| Category          | Dangerous Permissions Granted                              | Mod-Specific Use                          |
|-------------------|------------------------------------------------------------|-------------------------------------------|
| Location          | `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION`          | Business Directory maps                   |
| Contacts & Calls  | `READ_CONTACTS`, `READ_CALL_LOG`, `CALL_PHONE`, `READ_PHONE_STATE` | Contact picker, caller ID, UPI            |
| Storage & Media   | `READ/WRITE_EXTERNAL_STORAGE`, `READ_MEDIA_*`              | Themes, media downloader, backups         |
| Messaging         | `RECEIVE_SMS`, `SEND_SMS`                                  | OTP handling, UPI, bulk sender            |
| Media Capture     | `CAMERA`, `RECORD_AUDIO`                                   | Standard + extra media tools              |
| System            | `SYSTEM_ALERT_WINDOW`, `INSTALL_SHORTCUT`, `POST_NOTIFICATIONS` | Floating windows, shortcuts, persistent UI |

These are **not all required** by official WhatsApp; many are added exclusively for mod features.

---

### 4. Security & Code Issues (MobSF Findings)

- **Network Security:** Base config allows **clear-text HTTP** to all domains → traffic can be intercepted.  
- **Cryptography Failures:**  
  - AES in **ECB mode** (default, insecure).  
  - CBC + PKCS5/PKCS7 padding → vulnerable to padding-oracle attacks.  
  - CWE-327, OWASP M5: Insufficient Cryptography, MASVS MSTG-CRYPTO-2/3.  
- **Hardcoded Secrets:** 195+ strings, including Google API key `AIzaSyCGOJbGQ95SWrXxl8wk-_cRQZcJl42bvDU` (used for crash reporting/backups).  
- **Abused Permissions:** Matches known malware patterns (Triada Trojan family previously found in YoWhatsApp variants).

**Past Incidents:** Kaspersky (Oct 2022) documented YoWhatsApp bundles dropping the Triada modular Trojan (ads, premium subscriptions, WhatsApp session theft).

---

### 5. Server & Infrastructure Footprint

All critical endpoints belong to **Meta**:
- `crashlogs.whatsapp.net`, `pps.whatsapp.net` → WhatsApp backend.  
- `fb.com`, `instagram.com` domains → Meta ecosystem.  
- Google services (API key, Firebase, etc.).

No custom C2 servers detected in this scan, but third-party mods can silently add them in later builds.

---

### 6. Developer Identity Analysis (New – For Verification)

**Profile Summary of “Nawzad Yousef / Yousef”**  
- **Likely Age & Background:** Young adult / hobbyist developer or website operator (quick 13-day turnaround from default WP to full e-commerce-style site in May 2024).  
- **Technical Skill Level:** **Beginner-to-intermediate**. Uses off-the-shelf WordPress + popular plugins (many outdated), Cloudflare free tier, Google Trust Services SSL. No evidence of custom backend or advanced coding on socials.  
- **Motivation:** Self-described “big fan of WhatsApp” who runs a fan/blog site for mod downloads. Not a full-time professional security-conscious developer.  
- **Risk Indicators:** Poor security hygiene (outdated plugins, weak TLS, missing headers, CVE exposure) – typical of enthusiastic but non-professional operators.  
- **Identity Red Flags:**  
  - Social media shows **no coding/portfolio content**.  
  - X account has only 8 followers → very low visibility.  
  - Name variations (Yousef Al-Basha, Nawzad Yousef, “Yousef”) common in modding communities (possible pseudonym).  
  - **No evidence of ID theft** found; site explicitly credits him as author and bio matches the “original Yousef” who handed over app development to Fouad Mokdad.  
- **Cross-Verification Suggestion**  
  Compare TikTok/Facebook videos (active ones) with any voice/photos against known Fouad Mokdad content. If the person in active TikTok/FB posts matches the bio and site ownership, it is almost certainly the legitimate site maintainer (not stolen ID).

**Conclusion on Identity**  
High probability that **Nawzad Yousef = the original Yousef (Al-Basha)** who created the YoWhatsApp mod and now runs yowamod.app as a distribution/blog site. Fouad Mokdad handles the actual APK development.

---

### 7. Conclusion & Risk Assessment

**Purpose Achieved:** Delivers extra features via official server fork.

**But at what cost?**  
- Account ban risk: High.  
- Privacy/Security risk: **Extreme** (weak app crypto + amateur website with multiple CVEs and outdated components).  
- Data theft risk: Any mod + vulnerable download site increases chance of supply-chain attacks.

**Verdict**  
High-risk third-party modification. The associated website shows classic signs of a **hobbyist-run fan site** rather than a professional operation.

**Recommendations**  
1. Uninstall YoWhatsApp immediately.  
2. If used, change number + enable 2FA.  
3. Use only official WhatsApp.  
4. For privacy: Switch to Signal or use official disappearing messages.

**Sources**  
MobSF report, Nuclei scan results, Wayback Machine (May 2024 snapshots), RDAP/WHOIS, yowamod.app (About/Contact pages), Kaspersky Securelist, FouadMods references, X/TikTok/Facebook profiles.

---

**End of Updated Report.**
