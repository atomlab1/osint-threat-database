## Overview

This report presents a detailed investigation into the phishing website **www-checkactives2025.info**, which impersonates the **Meta (Facebook) Help Center**. The primary goal of the site is to steal user credentials. Through in-depth analysis of the website's structure, JavaScript behavior, image assets, and integration with external services, we successfully uncovered the phishing logic and operational workflow. The investigation confirmed that the site uses **Cloudflare CDN** to hide its backend and leverages **Google Apps Script** combined with **Telegram** for credential exfiltration.

---

## 1. Website Structure and Phishing Strategy

The phishing website is designed to impersonate the Meta Help Center. The page is titled **"Page Help Center"** and claims that the user's account has been restricted due to "violating community standards," encouraging the user to submit their password at `/business.html` to "appeal the restriction."

The site uses **Bootstrap 5.3.2**, **jQuery 3.5.1**, **Font Awesome 6.5.1**, and the **Next.js** framework to simulate a legitimate website environment. It contains counterfeit Meta logos and icons, including:

- `/img/logo.jpg` – main logo  
- `/img/xike.ico` – favicon  
- `/img/icon_1.png` to `/img/icon_17.png` – supporting icons  

The site also includes a copyright statement: `© 2024 Meta`.

To enhance credibility, the site dynamically translates its content using the **Google Translate API** (`translate-pa.googleapis.com`) based on the visitor's IP address. For example, users from Taiwan receive a zh-TW localized interface.  

The core phishing page `/business.html` contains a password input form:

```html
<input id="password" type="password">
<button id="submit-password">Continue</button>
````

Users are guided to submit their credentials directly into this form.

---

## 2. Credential Theft Logic

The website's JavaScript (`/js/index.js`) sends POST requests to a **Google Apps Script endpoint**:

```
script.google.com/macro...
```

This endpoint processes the submitted passwords, storing them in **Google Sheets**, and relays them to the phishing operators via a **Telegram Bot** using the `sendTelegram` function. The script response contains a Vietnamese message:

```
Đã ghi dữ liệu vào Google Sheet và gửi Telegram
```

This indicates the data has been written to Google Sheets and sent to Telegram, hinting that the operators may be located in Vietnam or using a Vietnamese interface.

Geo-location of the visitor is captured using **api.db-ip.com** and **get.geojs.io**, allowing the site to dynamically adjust language and content based on the user’s location.

---

## 3. Image and Asset Analysis

The site uses a set of images to enhance legitimacy. Each image has been hashed and analyzed:

* `/img/B2Y8S9I.jpg` – SHA256: `998c1ca10eefd2d893be9b62340dc4443aac5c98f048a36298622930f1c39cf5`
  Vector illustration (1280x720), theme: security protection, no EXIF data
* `/img/logo.jpg` – SHA256: `07ec2d7448f9a634670ea637682bda745c57004b0f74f0b2a22613ab80883c27`
  Fake Meta logo (313x310), no EXIF data
* `/img/xike.ico` – SHA256: `88ae5454a7c32c630703440849d35c58f570d8eecc23c071dbe68d63ce6a40d7`
  Site favicon (16x16), no metadata

These images share templates with other phishing sites, indicating the same threat actor operates multiple phishing campaigns and removes metadata to avoid tracking.

---

## 4. Cloudflare Protection

The phishing site uses **Cloudflare CDN** to hide its origin servers:

* DNS resolves to Cloudflare IPs: `172.67.208.80`, `104.21.69.125`
* TLS certificate issued by **Google Trust Services** (CN=WE1/WE2), valid until 2026-01-03
* No non-Cloudflare IP records exposed

Additional defenses include:

* `robots.txt` configured to allow search engine indexing (`search=yes`) while blocking AI training (`ai-train=no`)
* Specific bots blocked (e.g., GPTBot, @ClaudeBot)
* `disable-devtool@latest` prevents developer tools inspection
* Fake responses for version-controlled paths (e.g., `.git/HEAD`, `.svn/entries`) to prevent directory traversal detection

---

## 5. External Service Integration

The phishing operation integrates multiple external services:

* **Google Translate API**: dynamic content translation (`translate-pa.googleapis.com`)
* **GeoJS**: geolocation (`get.geojs.io`)
* **Google Apps Script**: credential submission (`script.google.com`)
* **DB-IP API**: additional geolocation (`api.db-ip.com`)
* **Telegram**: credentials exfiltration using `sendTelegram`

These services allow the attacker to run a phishing campaign without hosting infrastructure, while maintaining functionality and targeting accuracy.

---

## 6. Operational Workflow Summary

The workflow of the phishing operation is as follows:

1. User visits `www-checkactives2025.info` and is redirected to `/business.html`, showing a "Page Restricted" notice
2. User inputs password and clicks "Continue"
3. `/js/index.js` sends the password to Google Apps Script
4. Data is stored in Google Sheets and sent to Telegram in real time
5. Cloudflare CDN hides the origin server
6. Dynamic translation and geolocation enhance perceived legitimacy

---

## 7. Conclusion

This investigation successfully uncovered the phishing operation of **www-checkactives2025.info**. The attackers utilize **template-based site designs**, meaning multiple phishing sites share the same vulnerabilities and structural patterns.

The Vietnamese response from the backend indicates the threat actors may be operating in **Vietnam or Southeast Asia**.

This case serves as a showcase of open-source intelligence (OSINT) research on real-world phishing operations and demonstrates how attackers leverage common cloud services to execute efficient and scalable attacks.

```

