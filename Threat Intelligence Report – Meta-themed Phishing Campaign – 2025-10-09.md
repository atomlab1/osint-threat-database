# Threat Intelligence Report – Meta-themed Phishing Campaign – 2025-10-09

**Author:** AtomLab1  

---

## 1. Target Overview
- Phishing site impersonating Meta (Facebook) Help Center  
- Domain: `www-checkactives2025.info`  
- Hosting: Cloudflare CDN  

## 2. Website Structure & Phishing Strategy
- Impersonates Meta Help Center; page claims user account restricted  
- Directs users to submit password at `/business.html`  
- Technologies: Bootstrap 5.3.2, jQuery 3.5.1, Font Awesome 6.5.1, Next.js  
- Dynamic translation: Google Translate API based on IP (e.g., zh-TW for Taiwan)  

## 3. Credential Theft Logic
- `/js/index.js` sends POST requests to Google Apps Script endpoint  
- Credentials stored in Google Sheets  
- sendTelegram function sends data to Telegram Bot  
- Response in Vietnamese: `Đã ghi dữ liệu vào Google Sheet và gửi Telegram`  
- Geo-location via api.db-ip.com, get.geojs.io  

## 4. Cloudflare Protection & Defense
- DNS resolved to Cloudflare IPs (`172.67.208.80`, `104.21.69.125`), backend IP hidden  
- TLS certificate issued by Google Trust Services  
- Defense mechanisms:  
  - robots.txt controlling search engine & AI bots  
  - disable-devtool prevents developer tools inspection  
  - Fake responses to prevent directory or version leaks  

## 5. External Services Integration
- Google Translate API: `translate-pa.googleapis.com`  
- GeoJS: `get.geojs.io`  
- Google Apps Script: `script.google.com`  
- DB-IP API: `api.db-ip.com`  
- Telegram Bot: delivers stolen credentials  

## 6. Workflow Summary
1. User visits `www-checkactives2025.info` → `/business.html`  
2. Enters password, clicks "Continue"  
3. `/js/index.js` sends data to Google Apps Script  
4. Credentials stored in Google Sheets & sent via Telegram Bot  
5. Cloudflare CDN hides backend  
6. Dynamic translation enhances credibility  

## 7. Conclusion
- Successfully revealed phishing operation  
- Template-based design causes multiple sites to share vulnerabilities  
- Vietnamese response suggests threat actor region: Southeast Asia
