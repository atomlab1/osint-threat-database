# OSINT Report: Phishing Campaign Impersonating UFC Strike Giveaway – Wallet Drainer Analysis

**Methodology**: Traffic interception using Burp Suite with Chrome browser, tested with a brand-new empty wallet (no funds) for safety  
**Data Sources**: Personally captured HTTP requests/responses, domain WHOIS and SecurityTrails subdomain history

## Part 1: Raw Findings by the Researcher

### 1. Attack Entry Point and Domain Information
- Received an unsolicited email containing a link directing to https://giveaway.ufcstrike.net
- The landing page claimed to host a “100K Giveaway | Free ETH NFT Mint”, promising free NFT minting and a chance to win $100,000 in ETH
- Clicking any button on the page did not cause redirection; instead, it persistently displayed a wallet selection interface (Metamask, Unisat, Electrum, etc.)
- The page prompted the user to enter wallet password and seed phrase (mnemonic)
- A fresh, zero-balance wallet was created solely for testing; all traffic was captured via Burp Suite

- **Domain Comparison**:
  - Official UFC Strike website: https://ufcstrike.com
  - Phishing domain received: https://ufcstrike.net and its subdomain giveaway.ufcstrike.net

- **ufcstrike.net root page**:
  - Visiting https://ufcstrike.net shows a default Plesk holding page (no real content)

- **SecurityTrails subdomain history**:
  - giveaway.ufcstrike.net → Cloudflare, Inc.
  - ufcstrike.net → Cloudflare, Inc.
  - webmail.ufcstrike.net → no A record
  - www.ufcstrike.net → Cloudflare, Inc.

- **Historical A record**:
  - 217.70.184.38

- **Domain registration details**:
  - Registrar: http://www.gandi.net
  - Creation date: 2021-03-04 (5 years old)
  - Expiration date: 2024-03-03 (expired 2 years ago? – data may reflect historical snapshot)
  - Overall registration lifespan noted as 3 years (inconsistent data; requires further verification)

### 2. Captured Traffic Summary (Burp Suite)

- **Central endpoint**: All requests routed through `/secureproxy.php` with varying `?e=` parameters
  - Multiple `/secureproxy.php?e=/seed` → 200 OK, response size ~706–745 bytes
  - `/secureproxy.php?e=jscdn/getFile` → POST with JSON body `{"permit_key":"yg23q6kjckh32nj6voc1"}`
  - `/secureproxy.php?e=ping_proxy`
  - `/secureproxy.php?e=/fp/` or `/fp/...` (likely fingerprinting)
  - Several large application/javascript responses from `/secureproxy.php?e=jscdn/...`:
    - 41,751,543 bytes script
    - 1,222,601 bytes script
    - 96,128 bytes script
    - 76,099 bytes script

- **Encryption signature**:
  - POST body starts with `U2FsdGVkX1+` (standard AES-encrypted format – CryptoJS / OpenSSL)
  - Payload size: 3,672 bytes

### 3. Returned JavaScript Files (Four Main Samples)

- **Sample 1 (121,848 bytes)**:
  - Defines `window.rei43iuhf4ofiuhlwtgiulvrha`
  - Generates Unisat-style 24-word seed input form with eye-toggle icons
  - Includes error container displaying “2 words are invalid or misspelled”
  - “Continue” button with id="unisat-import-button"

- **Sample 2 (75,351 bytes)**:
  - Defines `window.rei43iuhf4ofiuhlwtgiulvrhd`
  - Generates Electrum-style interface supporting SLIP39 recovery shares + optional passphrase
  - Error message: “Invalid SLIP39 recovery shares”

- **Sample 3 (95,374 bytes)**:
  - Defines `window.rei43iuhf4ofiuhlwtgiulvrhb`
  - Generates Metamask-style interface (includes fox SVG logo)
  - Error message: “Invalid Secret Recovery Phrase”

- **Sample 4 (very large – truncated at >4 MB)**:
  - Heavily obfuscated JavaScript
  - Contains custom character map, bit-shifting operations, Brotli decompression logic (`BrotliDecompressBuffer`)
  - Dynamically generates data:base64 resources

## Part 2: Grok's Analysis & Interpretation

### 1. Attack Classification
The captured behavior matches a **browser-based wallet drainer phishing campaign**. The goal is to trick victims into manually typing their mnemonic seed phrase rather than tricking them into signing malicious transactions.

### 2. Domain & Infrastructure Observations
- **ufcstrike.net** is clearly impersonating the legitimate **ufcstrike.com** by using a different TLD (.net vs .com) and placing the phishing content under a subdomain (giveaway.).
- The root domain showing a blank Plesk page strongly suggests it exists purely to host subdomains for phishing campaigns.
- Cloudflare protection (evidenced by `cf_clearance` cookie) is commonly abused by phishing sites to bypass some scanners and add legitimacy appearance.
- Historical A record 217.70.184.38 links to Gandi infrastructure in France, consistent with Plesk hosting environments often used for disposable phishing domains.

### 3. Endpoint & Proxy Mechanism
- All communication funnels through a single PHP endpoint `/secureproxy.php` with dynamic `?e=` parameters – classic proxy-layer design used to hide the real C2 backend.
- Common parameters observed:
  - `/seed`: receives encrypted mnemonic data
  - `jscdn/getFile`: dynamically fetches additional malicious JS modules (protected by `permit_key`)
  - `ping_proxy`: likely tests proxy liveness
  - Large `jscdn/...` responses deliver obfuscated JavaScript payloads
- This architecture prevents direct exposure of the C2 server in browser network logs.

### 4. JavaScript Functionality Breakdown
- The four main JS samples are purpose-built to impersonate Unisat, Electrum, and Metamask wallet import screens with high visual fidelity.
- Fake error messages (“invalid words”, etc.) are deliberately shown to build false confidence and reduce suspicion.
- The fourth (largest) sample uses advanced obfuscation and Brotli decompression, indicating an effort to evade static analysis and deliver modular malicious logic.

### 5. Reconstructed Attack Chain
1. Email / advertisement redirects victim to giveaway.ufcstrike.net
2. Page loads large JavaScript payloads via `/secureproxy.php?e=jscdn/...`
3. Based on selected wallet type, renders corresponding fake import UI
4. Victim enters mnemonic → JavaScript collects input → AES encrypts → POST to `/seed`
5. Data forwarded through proxy to real backend (likely resolved dynamically via smart contract)

### 6. Risk Summary
- Any real mnemonic entered would allow immediate wallet drainage (no transaction signing required).
- Test used zero-balance wallet → no actual financial loss occurred.
- No evidence of system-level malware download, persistence, or executable delivery (purely browser-based attack).

**End of Report**
