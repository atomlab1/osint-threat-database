# OSINT & CTI Research Methodology

This document defines the **standardized, repeatable methodology** used for every CTI report in this portfolio. All tools are **free / open-source or have generous free tiers**. No paid enterprise licenses required.

## 1. Core Principles & Ethical Guidelines
- Passive-first approach  
- Multi-source verification  
- Reproducibility & zero-harm testing  
- Attack Chain Reconstruction (Cyber Kill Chain + MITRE ATT&CK)  

## 2. Standard Research Workflow
1. Target Identification & Triage  
2. Domain / Infrastructure Recon  
3. Web & Traffic Analysis  
4. APK / Malware Analysis  
5. Scam / Threat Feed Cross-Check  
6. Web3 / Blockchain Tracing  
7. Attack Chain & Risk Assessment  
8. Professional Report Writing  

## 3. Tools & Resources by Category (Awesome-Style Directory)

### 3.1 Domain & Infrastructure Reconnaissance
- **[subfinder](https://github.com/projectdiscovery/subfinder)** – Fast passive subdomain enumeration (download latest release)
- **[Amass](https://github.com/owasp-amass/amass)** – OWASP attack surface mapping & asset discovery
- **[findomain](https://github.com/Findomain/Findomain)** – Cross-platform subdomain enumerator
- **[assetfinder](https://github.com/tomnomnom/assetfinder)** – Passive asset discovery
- **[Sublist3r](https://github.com/aboul3la/Sublist3r)** – Subdomain enumeration (Python)
- **[SecurityTrails](https://securitytrails.com/)** – Historical & passive DNS (free tier)
- **[DNSDumpster](https://dnsdumpster.com/)** – Free DNS reconnaissance web tool
- **[Censys](https://censys.io/)** – Internet-wide asset search (free account)
- **[Shodan](https://www.shodan.io/)** – Search engine for Internet-connected devices (free tier)
- **[Wayback Machine](https://archive.org/web/)** – Historical website snapshots
- **[Recon-ng](https://github.com/lanmaster53/recon-ng)** – Full-featured reconnaissance framework
- **[theHarvester](https://github.com/laramies/theHarvester)** – Email, subdomain & employee OSINT
- **[SpiderFoot](https://github.com/smicallef/spiderfoot)** – Automated OSINT collection & correlation
- **[gobuster](https://github.com/OJ/gobuster)** – Directory & DNS brute-forcing
- **[feroxbuster](https://github.com/epi052/feroxbuster)** – Fast recursive content discovery
- **[dirb](http://dirb.sourceforge.net/)** – Classic web content scanner
- **[katana](https://github.com/projectdiscovery/katana)** – Next-generation crawling & spidering (ProjectDiscovery)
- **[nmap](https://nmap.org/download.html)** – Network discovery & security auditing
- **[Wappalyzer](https://www.wappalyzer.com/)** – Web technology fingerprinting (browser extension + online)
- **[BuiltWith](https://builtwith.com/)** – Website technology profiler
- **[WhatWeb](https://github.com/urbanadventurer/WhatWeb)** – Website identification engine

### 3.2 Web Investigation & Traffic Analysis
- **[Burp Suite Community Edition](https://portswigger.net/burp/communitydownload)** – Web proxy & traffic interception (official download)
- **[OWASP ZAP](https://www.zaproxy.org/download/)** – Free & open-source web app scanner
- **[urlscan.io](https://urlscan.io/)** – Website scanner & threat analysis (web-based)
- **[CheckPhish.ai](https://checkphish.ai/)** – AI-powered phishing & threat detection (free scans)
- **[URLVoid](https://www.urlvoid.com/)** – URL reputation & threat check (web-based)

### 3.3 Scam, Phishing & Threat Monitoring Feeds / Websites
- **[URLhaus](https://urlhaus.abuse.ch/)** – Real-time malicious URL database
- **[MalwareBazaar](https://bazaar.abuse.ch/)** – Free malware sample repository (APKs included)
- **[ThreatFox](https://threatfox.abuse.ch/)** – IoC sharing platform (abuse.ch)
- **[PhishTank](https://phishtank.org/)** – Community-driven phishing URL database
- **[OpenPhish](https://openphish.com/)** – Real-time phishing feed
- **[AlienVault OTX](https://otx.alienvault.com/)** – Open Threat Exchange (free account)
- **[VirusTotal](https://www.virustotal.com/)** – File & URL scanner (free tier)
- **[Hybrid-Analysis](https://www.hybrid-analysis.com/)** – Automated malware analysis (free)
- **[Any.Run](https://any.run/)** – Interactive malware sandbox (free tier)

### 3.4 APK / Mobile Malware Analysis
- **[MobSF (Mobile Security Framework)](https://github.com/MobSF/Mobile-Security-Framework-MobSF)** – All-in-one Android/iOS/Windows analysis (official repo + Docker)
- **[Apktool](https://ibotpeaches.github.io/Apktool/)** – Android APK reverse engineering
- **[Jadx-GUI](https://github.com/skylot/jadx)** – Dex to Java decompiler (GUI version)
- **[Frida](https://frida.re/)** – Dynamic instrumentation toolkit
- **[Ghidra](https://ghidra-sre.org/)** – NSA reverse-engineering framework (download)

### 3.5 Web3 / Blockchain OSINT (Crypto Scams & Wallet Drainers)
**Explorers**
- **[Etherscan](https://etherscan.io/)** – Ethereum blockchain explorer
- **[Blockchair](https://blockchair.com/)** – Multi-crypto blockchain explorer
- **[Solscan](https://solscan.io/)** – Solana blockchain explorer
**Analytics & Tracing**
- **[Arkham Intelligence](https://intel.arkm.com/)** – On-chain intelligence & entity tracking
- **[Breadcrumbs.app](https://www.breadcrumbs.app/)** – Visual address clustering & fund flow
- **[ChainAbuse](https://www.chainabuse.com/)** – Crypto scam reporting database
- **[BitcoinAbuse](https://www.bitcoinabuse.com/)** – Bitcoin scam address database
- **[Dune Analytics](https://dune.com/)** – On-chain query dashboard (free)
**Awesome Web3 OSINT List**: [aaarghhh/awesome_osint_blockchain_analysis](https://github.com/aaarghhh/awesome_osint_blockchain_analysis)

### 3.6 General OSINT & Automation Tools
- **[Maltego CE](https://www.maltego.com/downloads/)** – Community Edition link analysis
- **[ExifTool](https://exiftool.org/)** – Metadata reader/writer
- **[OSINT Framework](https://osintframework.com/)** – Web-based OSINT tool directory (clickable tree)

### 3.7 Curated Awesome Lists (One-Click Starting Points)
- **[Awesome OSINT (jivoi)](https://github.com/jivoi/awesome-osint)** – Most starred OSINT list
- **[Awesome OSINT (awesomelistsio)](https://github.com/awesomelistsio/awesome-osint)** – High-quality curated edition
- **[Awesome OSINT For Everything](https://github.com/Astrosp/Awesome-OSINT-For-Everything)** – 200+ categories
- **[Awesome Intelligence](https://github.com/ARPSyndicate/awesome-intelligence)** – Threat intel focus

### 3.8 Additional Threat Intelligence Tools (For Tracking Cyber Criminals and Criminal Activity)
These tools are sourced from the Awesome OSINT repository and additional 2026 research, focusing on threat actor profiling, cyber threat maps, and intelligence feeds for monitoring criminal activities.
- **[Abusech](https://hunting.abuse.ch)** – Hunt across all abuse.ch platforms with one simple query
- **[Cisco Talos Intelligence](https://talosintelligence.com/reputation_center)** – IP and Domain Reputation Center for real-time threat detection
- **[Cloudflare Radar](https://radar.cloudflare.com)** – Internet traffic patterns, attacks, and technology trends
- **[Criminal IP](https://www.criminalip.io/)** – Cyber Threat Intelligence Search Engine and Attack Surface Management(ASM) platform
- **[Fortiguard Labs](https://fortiguard.fortinet.com/threat-map)** – FortiGuard Outbreak Alerts for on-going cybersecurity attacks
- **[HCL Threat Map](https://www.hcltech.com/hcl-threat-map)** – Cyber Threat Map by HCLTech
- **[IBM X-Force Exchange](https://exchange.xforce.ibmcloud.com/activity/map)** – Current Malicious Activity map
- **[Imperva Live Threat Map](https://www.imperva.com/cyber-threat-attack-map/)** – Real-time global view of DDoS attacks, hacking attempts, and bot assaults
- **[Kaspersky Cyberthreat Map](https://cybermap.kaspersky.com/)** – Live cyber-attack map
- **[LIONIC Cyber Threat Map](https://www.lionic.com/monitoring/)** – Global cyber threat visualization
- **[NETSCOUT Cyber Threat Map](https://horizon.netscout.com/)** – Real-Time DDoS Attack Map
- **[Radware Live Cyber Threat Map](https://livethreatmap.radware.com/)** – Near real-time information about cyberattacks
- **[Secure Gateway Live Cyber Threat Map](https://securegateway.com/map/v5/)** – Live cyber threat visualization
- **[Thale's Cyberthreat Map](https://cds.thalesgroup.com/en/cyberthreat/hitmap)** – Cybersecurity trends with targeted areas, attacks, sectors, and malware
- **[ThreatsEye](https://threatseye.io/threats-map)** – Real-time visualization of global cyber attacks and threats
- **[Zscaler Global Threat Map Dashboard](https://threatlabz.zscaler.com/cloud-insights/threat-map-dashboard)** – 24-hour threats detected by antivirus engines and APTs
- **[APT Groups and Operations](https://docs.google.com/spreadsheets/u/0/d/1H9_xaxQHpWaa4O_Son4Gx0YOIzlcBWMsdvePFX68EKU/pubhtml?pli=1#)** – Threat actors, sponsored countries, tools, methods
- **[APTWiki](https://apt.threatradar.net/)** – Historical wiki with 214 actor entries
- **[Bi.Zone](https://gti.bi.zone/)** – 148 threat groups with detailed TTPs
- **[BreachHQ](https://breach-hq.com/threat-actors)** – List of all known cyber threat actors
- **[Cybergeist](https://cybergeist.io/threat-actor)** – Intelligence profiles about key threats and context
- **[Dark Web Informer](https://darkwebinformer.com/threat-actor-database/)** – Tracking 854 Threat Actors
- **[ETDA](https://apt.etda.or.th/cgi-bin/listgroups.cgi)** – Search for Threat Actor groups and tools
- **[FortiGuard Labs](https://www.fortiguard.com/threat-actor)** – Actionable insights on threat actors
- **[KNOWLEDGENOW](https://know.netenrich.com/content/track/threat-actor)** – Trending Threats
- **[lazarusholic](https://lazarus.day/actors/)** – Total 203 threat actors
- **[Malpedia](https://malpedia.caad.fkie.fraunhofer.de/actors)** – List of threat actor groups
- **[MISP Galaxy](https://www.misp-galaxy.org/360net/)** – Adversary groups identified by 360.net
- **[OPENHUNTING.IO](https://openhunting.io/threat-library)** – Threat Library Collecting Information
- **[SOCRadar LABS](https://socradar.io/labs/threat-actor/)** – Threat actor profiles and activities
- **[Thales](https://cds.thalesgroup.com/en/cyberthreat/attacks-page)** – Threat actor groups in graphical explorer
- **[Bitdefender Threat Map](https://threatmap.bitdefender.com/)** – Cyberthreat Real Time Map
- **[BunkerWeb Live Cyber Attack Threat Map](https://threatmap.bunkerweb.io/)** – Live cyber attacks blocked by BunkerWeb
- **[Check Point Live Cyber Threat Map](https://threatmap.checkpoint.com/)** – Top cyber threats of 2026
- **[Threat Actor Usernames Scrape](https://github.com/spmedia/Threat-Actor-Usernames-Scrape)** – 350k+ threat actor usernames from cybercrime sources
- **[GitGuardian](https://www.gitguardian.com/monitor-public-github-for-secrets)** – Monitor public GitHub for secrets
- **[OnionScan](https://github.com/s-rah/onionscan)** – Tool for investigating the Dark Web
- **[onion-lookup](https://onion.ail-project.org/)** – Check Tor hidden services and metadata
- **[OTX AlienVault](https://otx.alienvault.com/)** – Open Threat Exchange for collaborative threat sharing
- **[PhishingSecLists](https://github.com/spmedia/PhishingSecLists)** – Lists for fuzzing phishing and scam sites
- **[REScure Threat Intel Feed](https://rescure.fruxlabs.com/)** – Independent threat intelligence project
- **[Columbus Project](https://github.com/elmasy-com/columbus)** – Advanced subdomain discovery service
- **[Merklemap](https://www.merklemap.com/)** – Enumerate all subdomains from certificate transparency logs
- **[aa419 Fake Sites Database](https://db.aa419.org/fakebankslist.php)** – Fraudulent websites identified by Artists Against 419
- **[Abuseipdb](https://www.abuseipdb.com/)** – Repository of abuses for IPs, Domains, and subnets
- **[BGP.tools](https://bgp.tools)** – Modern BGP toolkit for network reconnaissance
- **[BrightCloud](https://brightcloud.com/tools/url-ip-lookup.php)** – Reputation, category, and threats for URL or IP
- **[CertKit Certificate Search](https://www.certkit.io/tools/ct-logs/)** – Search for public SSL/TLS certificates
- **[FOFA](https://en.fofa.info/)** – Asset search and analysis tool
- **[FullHunt](https://fullhunt.io/)** – Secure External Attack Surface
- **[GrayNoise](https://viz.greynoise.io/)** – Search Exposed Internet assets, Malicious IPs
- **[Hunter Search Engine](https://hunter.how/)** – Search Exposed Internet assets
- **[Intelligence X](https://intelx.io/tools)** – Search across dark web and data leaks
- **[Netlas.io](https://app.netlas.io/)** – Network asset discovery
- **[ODIN](https://search.odin.io/)** – Search for Hosts, CVEs, Exposed Buckets
- **[Search Abuseipdb](https://github.com/oseasfr/search-abuseipdb)** – Query IPs, ranges in AbuseIPDB
- **[Shadowserver](https://dashboard.shadowserver.org/)** – Global cyber threat statistics

### 3.9 Malware Analysis & Disassembly Tools (For Analyzing and Disassembling Malware Operations)
These tools help in tracking malware locations, analyzing samples, and disassembling code to understand criminal techniques.
- **[MalwareBazaar](https://bazaar.abuse.ch/browse/)** – Search and download malware samples by hash, family, tag
- **[YARAify](https://yaraify.abuse.ch/scan/)** – Collaborative YARA engine for file pattern matching
- **[Cuckoo Sandbox](https://cuckoosandbox.org/)** – Open-source automated malware analysis system
- **[x64dbg](https://x64dbg.com/)** – Open-source debugger for Windows binaries
- **[Wireshark](https://www.wireshark.org/)** – Network protocol analyzer for malware traffic
- **[Radare2 (r2)](https://rada.re/n/)** – Reverse engineering framework for static malware analysis
- **[IDA Pro](https://hex-rays.com/ida-pro/)** – Interactive disassembler for binary analysis (free version available)
- **[OllyDbg](https://www.ollydbg.de/)** – 32-bit debugger for Windows malware
- **[ClamAV](https://www.clamav.net/)** – Open-source antivirus for malware detection
- **[Snort](https://www.snort.org/)** – Network intrusion detection for malware tracking
- **[Suricata](https://suricata.io/)** – Network threat detection engine
- **[awesome-malware-analysis](https://github.com/rshipp/awesome-malware-analysis)** – Curated list of malware analysis tools

### 3.10 Scam Site & Phishing Analysis Tools (For Tracking and Analyzing Scam Operations)
Tools focused on identifying, scanning, and analyzing scam websites and phishing campaigns.
- **[PhishStats](https://phishstats.info/)** – Phishing statistics and database
- **[urlDNA](https://urldna.io/)** – Analyze URLs, monitor brands, track phishing sites
- **[Islegitsite](https://www.islegitsite.com/)** – Checks website trustworthiness and security
- **[CredenShow](https://credenshow.com/)** – Identify compromised credentials
- **[HIB Ransomed](https://haveibeenransom.com/)** – Check if data has been leaked
- **[HEROIC.NOW](https://heroic.com/)** – Dark web data leak scanner
- **[IKnowYour.Dad](https://iknowyour.dad/)** – Data Breach Search Engine
- **[StealSeek](https://stealseek.io/)** – Search and analyze data breaches
- **[Venacus](https://venacus.com/)** – Search for data breaches and notifications
- **[Ahmia](https://ahmia.fi)** – Dark Web Search Engine
- **[Aleph Open Search](https://open-search.aleph-networks.eu)** – Dark Web Search Engine
- **[DataSploit](https://github.com/DataSploit/datasploit)** – Aggregates data from multiple sources
- **[Cyble ODIN](https://odin.io/)** – Scans internet assets, exposed buckets, vulnerabilities
- **[Google Dorks](https://securitytrails.com/blog/google-hacking-techniques)** – Specialized Google queries for investigations
- **[NexVision](https://nexvision.io/)** – Large OSINT data pool for surface/dark web
- **[Hudson Rock](https://hudsonrock.com/)** – Cybercrime intelligence API
- **[Metagoofil](https://github.com/laramies/metagoofil)** – Metadata extraction from documents
- **[Recon-Ng](https://github.com/lanmaster53/recon-ng)** – Reconnaissance framework
- **[Check Usernames](https://github.com/sherlock-project/sherlock)** – Username availability checker
- **[TinEye](https://tineye.com/)** – Reverse image search
- **[Creepy](https://github.com/jkakavas/creepy)** – Geolocation OSINT tool
- **[Videris](https://blackdotsolutions.com/videris/)** – Full-spectrum OSINT for collection and analysis
- **[i2 Analyst’s Notebook](https://www.ibm.com/uk-en/products/i2-analysts-notebook)** – Data visualization and analysis
- **[OSINT Industries](https://www.osint.industries/)** – Tools for online investigations, fraud detection
- **[SL Crimewall](https://sociallinks.io/)** – All-in-one OSINT for investigations
- **[Recorded Future](https://www.recordedfuture.com/)** – Threat intelligence with darknet monitoring
- **[Hunt.io](https://hunt.io/)** – Tracks malicious infrastructure, C2 servers
- **[BeVigil-CLI](https://github.com/Bevigil/BeVigil-OSINT-CLI)** – Searches assets from mobile apps
- **[Cyberbro](https://github.com/stanfrbd/cyberbro)** – Searches and checks reputation of observables
- **[CyberGordon](https://cybergordon.com)** – Threat intelligence search with 30+ sources
- **[Discoshell](https://github.com/foozzi/discoshell)** – Discovery script using multiple tools
- **[FOCA](https://github.com/ElevenPaths/FOCA)** – Metadata and hidden info finder
- **[Greynoise](https://greynoise.io/)** – Anti-Threat Intelligence for background noise
- **[IntelHub](https://github.com/tomsec8/IntelHub)** – Browser-based OSINT extension
- **[Orbit](https://github.com/s0md3v/Orbit)** – Crypto wallet relationships crawler
- **[OSINT-Tool](https://www.osint-tool.com/)** – Browser extension for OSINT utilities
- **[OSINT.SH](https://osint.sh/)** – Information Gathering Toolset
- **[Photon](https://github.com/s0md3v/Photon)** – Crawler for OSINT
- **[SerpApi](https://serpapi.com/)** – Scrapes search engines
- **[SerpScan](https://github.com/Alaa-abdulridha/SerpScan)** – PHP script for dorking
- **[Sintelix](https://sintelix.com/)** – Graphical link analysis for OSINT
- **[sn0int](https://github.com/kpcyrd/sn0int)** – Semi-automatic OSINT framework
- **[SpiderSuite](https://github.com/3nock/SpiderSuite)** – GUI web security crawler
- **[Sub3 Suite](https://github.com/3nock/sub3suite)** – Intelligence gathering suite
- **[Unfurl](https://dfir.blog/unfurl/)** – Breaks down URLs for forensics
- **[Waybackurls](https://github.com/tomnomnom/waybackurls)** – Fetches URLs from Wayback Machine
- **[Zen](https://github.com/s0md3v/Zen)** – Finds email addresses of GitHub users
- **[Lampyre](https://lampyre.io/)** – All-in-one OSINT for people, businesses, crypto
- **[Social Links (Crimewall)](https://sociallinks.io/)** – Social media and dark web investigations

## 4. Attack Structure Analysis Framework
- **Delivery** (email, ad, fake site)
- **Landing / Social Engineering**
- **Credential Harvesting / Seed Phrase Theft**
- **Proxy / C2 Layer** (e.g., secureproxy.php)
- **Exfiltration** (Telegram bot, Google Apps Script, blockchain)
- **Monetization** (wallet drain, ransomware, etc.)
- **Infrastructure Attribution** (Cloudflare, Gandi, registrar, developer OSINT)

Cross-referenced with MITRE ATT&CK:
- TA0001 Initial Access
- TA0006 Credential Access
- TA0010 Exfiltration
- TA0040 Impact

---

**This methodology + hyperlinked tool directory** is publicly shared to demonstrate transparency, professionalism, and depth of knowledge to potential employers in the OSINT / Cyber Threat Intelligence field.

Last updated: 19 February 2026
