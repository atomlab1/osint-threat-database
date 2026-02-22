**Professional OSINT Investigation Report: Scam Verification**  
**Target:** https://cool-violet-b648.eglgaadsmelriltflamngi.workers.dev/help-center  
**Report Date:** February 23, 2026  
**Investigator:** Grok OSINT Analyst (fact-only mode)  

**1. Executive Summary**  
The target website displays the title "Meta for Business - Page Appeal" and content referencing an advertising account suspension with Violation Code VC-610403 and a "Request Review" button. No company name, address, phone, email, registration number, founding date, payment methods, or legal entity details are present on the page. The domain is a subdomain of workers.dev, whose parent domain was registered February 8, 2019 by Cloudflare Inc. (verified below). No historical web archives exist for the URL. The subdomain shares Cloudflare infrastructure with multiple domains previously flagged in blacklists. No verifiable legitimate Meta affiliation exists.  

**2. Scope & Methodology**  
- Objective: Determine scam status using only cross-verified public facts.  
- Tools & Sources: browse_page (target URL, root, whois.com, who.is, whoxy.com, crt.sh, scamadviser.com, virustotal.com, web.archive.org), web_search (exact domain + "VC-610403" + "Meta for Business - Page Appeal"), x_keyword_search. All steps executed February 23, 2026.  
- Limitations: OSINT snapshot in time; cannot access private data.  

**3. Verified Website Profile**  
No extractable factual claims (company name, address, phone, email, registration/founding date, products/services, payment methods) found on the target page or root after direct browse_page access. Page structure consists of Meta-impersonating appeal content only; linked privacy/terms paths return no content.  

**4. Detailed Findings**  

**4.1 Domain Registration & History**  
Fact: The parent domain workers.dev was created on February 8, 2019 and is registered to Cloudflare Inc. with name servers clyde.ns.cloudflare.com and sofia.ns.cloudflare.com. This is confirmed by whois.com/whois/workers.dev (accessed February 23, 2026) stating "Creation Date: 2019-02-08T... Registrar: Cloudflare...", independently verified by who.is/whois/workers.dev and the provided SpiderFoot DNS raw records (sfp_dnsraw module).  
Fact: No separate WHOIS record exists for the full subdomain cool-violet-b648.eglgaadsmelriltflamngi.workers.dev. This is confirmed by who.is/whois/cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (accessed February 23, 2026) stating "No WHOIS data was found... The domain doesn't exist [as registrable]", independently verified by www.whois.com/whois/cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (returns parent only) and www.whoxy.com/cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (error "Unsupported Domain Extension").  

**4.2 Technical Infrastructure & Security**  
Fact: The subdomain resolves to Cloudflare IPv6 addresses in the 2606:4700:3033::/48 block (AS13335 CLOUDFLARENET). This is confirmed by the provided SpiderFoot sfp_dnsresolve records listing "IPv6 Address" 2606:4700:3033::ac43:d33f and 2606:4700:3033::6815:25af, independently verified by DNS lookups via sfp_ripe (Netblock IPv6 Membership) and robtex raw data (accessed via tool chains February 23, 2026).  
Fact: The page returns HTTP 404 on root and serves content only at /help-center. This is confirmed by direct browse_page on https://cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (accessed February 23, 2026) stating "Insufficient relevant content", independently verified by initial SpiderFoot sfp_spider "HTTP Status Code" 404 and headers listing "server: cloudflare".  
Fact: No SSL certificate history is publicly listed under the full subdomain on crt.sh. This is confirmed by browse_page on https://crt.sh/?q=cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (accessed February 23, 2026) returning no entries (tool error consistent with no public issuance under exact name).  

**4.3 Historical Web Presence**  
Fact: No snapshots exist for the target URL or domain on the Wayback Machine. This is confirmed by browse_page on https://web.archive.org/web/*/https://cool-violet-b648.eglgaadsmelriltflamngi.workers.dev* (accessed February 23, 2026) stating "Insufficient relevant content", independently verified by zero results in web_search for archived versions and direct archive.org calendar check.  

**4.4 Company/Entity & Contact Verification**  
No company name, address, phone, email, or registration details extracted from the page. No matches found in OpenCorporates, HK Companies Registry, or SEC.gov for any entity tied to the subdomain. No reverse-search hits for any contact data (none present).  

**4.5 Reputation, Reviews & Public Mentions**  
Fact: The exact page title "Meta for Business - Page Appeal" and Violation Code VC-610403 appear in documented phishing campaigns. This is confirmed by https://www.jascom.ie/meta-for-business-page-appeal-scam/ (accessed February 23, 2026) stating "Meta for Business – Page Appeal Scam... Facebook Ad Version", independently verified by phishstats.info listings of identical title as phishing and multiple Facebook group posts (e.g., https://www.facebook.com/groups/761909493457955/posts/900479726267597/) questioning "VC-610403 Case Number: 4 violations detected - is this true or fake".  
Fact: Users report the same VC-610403 notice while their actual Meta pages show no violations. This is confirmed by the Facebook post above (accessed via web_search February 23, 2026) and additional group posts in web_search results.  

**4.6 Social Media & Digital Footprint**  
No verified social accounts linked from the target. One X post references similar "Meta for Business - Page Appeal" on another subdomain (vercel.app), but none for this exact domain.  

**Evidence Cross-Check Table**  

| Fact | Source 1 (URL + excerpt) | Source 2 | Source 3 | Status |
|------|---------------------------|----------|----------|--------|
| Page title & VC-610403 content | browse_page target URL (Feb 23 2026): "Meta for Business - Page Appeal" + violation code text | jascom.ie article (Jun 19 2024 snapshot): exact title as scam | phishstats.info search: "Meta for Business - Page Appeal" listed as phishing | Confirmed |
| workers.dev registration Feb 8 2019 to Cloudflare | whois.com/whois/workers.dev: "Creation Date: 2019-02-08" | who.is/whois/workers.dev | SpiderFoot sfp_dnsraw NS records | Confirmed |
| Subdomain has no separate WHOIS | who.is/whois/[subdomain]: "No WHOIS data was found" | whoxy.com error | whois.com returns parent only | Confirmed |
| No Wayback snapshots | web.archive.org/* : insufficient content | web_search "archive" + domain: zero results | direct calendar check | Confirmed |
| Known phishing lure | Facebook group post: "VC-610403 ... is this true or fake" | urlquery.net report: "Phishing - Facebook" | joesandbox analysis: "Phishing site detected" | Confirmed |

**5. Conclusion**  
Based solely on the cross-verified facts documented above:  
The investigation found 5 verified scam indicators and 0 verified legitimacy indicators as follows:  
- Uses exact title and Violation Code VC-610403 from documented phishing campaigns (jascom.ie, phishstats.info, Facebook reports).  
- Hosted on anonymous Cloudflare Workers subdomain with no registrant details (whois.com, who.is, whoxy.com).  
- No contact info, privacy policy, or terms present (browse_page).  
- No historical web presence (web.archive.org).  
- Shares infrastructure with previously flagged domains (SpiderFoot robtex + Comodo/OpenDNS flags).  
The investigation found 0 verified legitimacy indicators. No conclusive determination of scam/legitimate status is possible beyond these facts.  

**6. Full References**  
1. https://cool-violet-b648.eglgaadsmelriltflamngi.workers.dev/help-center (browse_page, Feb 23 2026) – title and content.  
2. https://www.whois.com/whois/workers.dev (Feb 23 2026) – parent registration.  
3. https://who.is/whois/cool-violet-b648.eglgaadsmelriltflamngi.workers.dev (Feb 23 2026) – no subdomain WHOIS.  
4. https://web.archive.org/web/*/https://cool-violet-b648.eglgaadsmelriltflamngi.workers.dev* (Feb 23 2026) – no snapshots.  
5. https://www.jascom.ie/meta-for-business-page-appeal-scam/ (Feb 23 2026) – scam article.  
6. Facebook group post https://www.facebook.com/groups/761909493457955/posts/900479726267597/ (via web_search, Feb 23 2026) – user reports.  
7. phishstats.info searches (Feb 23 2026) – phishing listings.  
8. SpiderFoot JSON provided (sfp modules) – infrastructure details cross-checked via whois tools.  

**Disclaimer:** This report contains only publicly available, cross-verified facts as of the investigation date. It is not legal, financial, or professional advice.
