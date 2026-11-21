# Blocklist analysis

Snapshot of all **4,301** domains in [`Blocklist.txt`](../Blocklist.txt), generated on 2026-11-21.
Every domain is grouped by type, checked to see if it still exists, cross-checked against other public
blocklists and given a threat score. The full data set is in [`domains.csv`](domains.csv).

> The reasons are reconstructed after the fact from the domain name, the current website, registration
> data and other blocklists. The original reason for every entry is simply: it showed up in the redirect
> chain of a spam mail. Entries marked _low/medium confidence_ are best guesses.

## By category

| Category | Domains | Still exists | Online | Avg. threat score |
|---|---:|---:|---:|---:|
| [Phishing & brand impersonation](phishing.md) | 125 | 70 | 21 | 73 |
| [Fake shops & product scams](fake-shops.md) | 203 | 102 | 72 | 58 |
| [Investment, crypto & money scams](investment-scams.md) | 61 | 26 | 13 | 64 |
| [Malware, PUPs & tech-support scams](malware.md) | 32 | 19 | 11 | 68 |
| [Gambling & casino](casino.md) | 442 | 410 | 304 | 54 |
| [Dating & adult](dating-adult.md) | 73 | 57 | 44 | 42 |
| [Spam, lead-gen & prize scams](spam-leadgen.md) | 434 | 280 | 208 | 49 |
| [Redirects, link tracking & cloaking](redirects-tracking.md) | 469 | 361 | 248 | 52 |
| [Compromised legitimate sites](compromised.md) | 230 | 204 | 172 | 36 |
| [URL shorteners & link-in-bio](shorteners.md) | 110 | 108 | 101 | 30 |
| [Abused hosting, CDN & infrastructure](hosting.md) | 136 | 133 | 107 | 15 |
| [Email marketing & mass-mail infrastructure](email-marketing.md) | 53 | 51 | 44 | 18 |
| [Advertising networks & ad tech](adtech.md) | 320 | 313 | 233 | 14 |
| [Analytics, tracking & data brokers](tracking.md) | 183 | 181 | 127 | 9 |
| [Parked / for-sale domains & parking services](parked.md) | 52 | 51 | 50 | 35 |
| [Mainstream services (likely legitimate)](mainstream.md) | 206 | 206 | 180 | 1 |
| [Unknown purpose](unknown.md) | 1,172 | 492 | 206 | 34 |
| **Total** | **4,301** | **3,064** | **2,141** | |

## Does it still exist?

- **3,064** domains are still registered, **1,144** are gone and **93** could not be determined.
- **970** domains (22%) are also listed on at least one other public blocklist.

| Status | Domains | Meaning |
|---|---:|---|
| Online | 2,023 | Resolves and a web server answers (any HTTP status). |
| Parked | 118 | Online, but only shows a parking or for-sale page. |
| No website | 234 | Resolves in DNS, but no web server answers. |
| No address | 369 | Domain is registered, but has no web address (no A record). |
| DNS error | 119 | The domain's DNS servers are broken (SERVFAIL). |
| Not resolving | 156 | Domain does not resolve (NXDOMAIN) but is still registered. |
| Suspended | 138 | Registry or registrar put the domain on hold (usually an abuse takedown). |
| Gone | 1,144 | Domain is not registered anymore (expired or deleted). Anyone could register it again. |

## Scores

**Threat score (0–100)** is a heuristic for how dangerous a domain is *today*:

| Factor | Points |
|---|---|
| Base score per category | phishing, investment scams, malware 70 · fake shops 60 · casino, spam, redirects 50 · dating 45 · compromised sites, unknown 40 · email marketing, shorteners, parked 30 · ad tech, tracking, hosting 25 · mainstream 5 |
| Listed on a threat-intel list (phishing, malware, scam, fraud) | +15 |
| Ad/tracking domain also on an ad or tracking list | +5 |
| Registered less than 1 year ago / less than 3 years ago / more than 10 years ago | +10 / +5 / −10 |
| Frequently abused TLD (.top, .xyz, .shop, .online, .site, .live …) | +5 |
| Homepage cloaks to Google/Bing (shows bots a harmless page) | +5 |
| Registry hold (confirmed abuse) | +5 |
| Not reachable / not registered anymore | −5 / −15 |
| Popular domain: Tranco top 10k / top 100k | −20 / −10 |

Each row in `domains.csv` has a `score_breakdown` column that lists which factors applied.

**Breakage risk** tells you how likely it is that blocking the domain breaks normal websites or apps:

- **High**: a mainstream service, or a very popular hosting, shortener or mail platform.
- **Medium**: hosting, shorteners, email platforms, consent managers and other popular domains.
- **Low**: everything else. Blocking only stops the spam, scam or tracking.

## High breakage risk (263)

These are probably legitimate services. Blocking them can break normal sites or apps; review whether you want to keep them.

| Domain | Category | Why it is on the list | Tranco rank |
|---|---|---|---:|
| `mail.ru` | Mainstream services (likely legitimate) | Mail.ru Russian portal/webmail | 24 |
| `bing.com` | Mainstream services (likely legitimate) | Microsoft Bing search | 45 |
| `x.com` | Mainstream services (likely legitimate) | X (Twitter) social network | 48 |
| `yahoo.com` | Mainstream services (likely legitimate) | Yahoo portal/mail | 72 |
| `b-cdn.net` | Abused hosting, CDN & infrastructure | Bunny CDN customer domain | 81 |
| `qq.com` | Mainstream services (likely legitimate) | Tencent QQ portal | 88 |
| `workers.dev` | Abused hosting, CDN & infrastructure | Cloudflare Workers serverless hosting | 90 |
| `msn.com` | Mainstream services (likely legitimate) | Microsoft MSN portal | 94 |
| `yandex.ru` | Mainstream services (likely legitimate) | Yandex search/portal | 112 |
| `aliyuncs.com` | Abused hosting, CDN & infrastructure | Alibaba Cloud object storage/hosting | 116 |
| `cloudflare-dns.com` | Mainstream services (likely legitimate) | Cloudflare 1.1.1.1 DNS resolver | 137 |
| `duckdns.org` | Abused hosting, CDN & infrastructure | Duck DNS free dynamic DNS | 139 |
| `vk.com` | Mainstream services (likely legitimate) | VK social network | 163 |
| `example.com` | Mainstream services (likely legitimate) | IANA reserved example domain | 184 |
| `awswaf.com` | Mainstream services (likely legitimate) | AWS WAF bot-challenge infrastructure | 189 |
| `mts.ru` | Mainstream services (likely legitimate) | MTS Russian telecom | 209 |
| `publicnode.com` | Abused hosting, CDN & infrastructure | Public blockchain RPC endpoints (Allnodes) | 212 |
| `avcdn.net` | Mainstream services (likely legitimate) | Avast/AVG software CDN | 213 |
| `namecheap.com` | Mainstream services (likely legitimate) | Namecheap domain registrar | 226 |
| `msftconnecttest.com` | Mainstream services (likely legitimate) | Windows network connectivity check | 247 |
| `t.co` | URL shorteners & link-in-bio | X/Twitter link shortener | 251 |
| `wixsite.com` | Abused hosting, CDN & infrastructure | Wix free site hosting | 274 |
| `tinyurl.com` | URL shorteners & link-in-bio | URL shortener (TinyURL) | 310 |
| `msftncsi.com` | Mainstream services (likely legitimate) | Windows NCSI connectivity check | 314 |
| `avast.com` | Mainstream services (likely legitimate) | Antivirus vendor (Avast) | 323 |
| `mybluehost.me` | Abused hosting, CDN & infrastructure | Bluehost temporary site domains | 354 |
| `twimg.com` | Mainstream services (likely legitimate) | X/Twitter image CDN | 363 |
| `weebly.com` | Abused hosting, CDN & infrastructure | Weebly free site builder | 371 |
| `aliyun.com` | Mainstream services (likely legitimate) | Alibaba Cloud | 376 |
| `yandex.com` | Mainstream services (likely legitimate) | Yandex search | 413 |
| `substack.com` | Mainstream services (likely legitimate) | Newsletter publishing platform (Substack) | 420 |
| `mcafee.com` | Mainstream services (likely legitimate) | McAfee antivirus vendor (abused in fake-AV scams) | 445 |
| `yahoo.co.jp` | Mainstream services (likely legitimate) | Yahoo! Japan portal | 458 |
| `braze.com` | Email marketing & mass-mail infrastructure | Customer engagement/email platform (Braze) | 459 |
| `foxnews.com` | Mainstream services (likely legitimate) | Fox News | 499 |
| `threads.com` | Mainstream services (likely legitimate) | Threads social network (Meta) | 565 |
| `intercom.io` | Mainstream services (likely legitimate) | Customer messaging SaaS (Intercom) | 610 |
| `supabase.co` | Abused hosting, CDN & infrastructure | Supabase backend/storage platform | 666 |
| `zoho.com` | Mainstream services (likely legitimate) | Zoho business software suite | 738 |
| `ovh.net` | Abused hosting, CDN & infrastructure | OVHcloud hosting infrastructure | 747 |
| `attn.tv` | Email marketing & mass-mail infrastructure | SMS/email marketing (Attentive) | 761 |
| `cloudinary.com` | Abused hosting, CDN & infrastructure | Cloudinary image/video CDN | 782 |
| `digitaloceanspaces.com` | Abused hosting, CDN & infrastructure | DigitalOcean Spaces object storage | 843 |
| `mailchi.mp` | Email marketing & mass-mail infrastructure | Mailchimp hosted pages | 975 |
| `onesignal.com` | Email marketing & mass-mail infrastructure | OneSignal push/email engagement platform | 1026 |
| `it.com` | Abused hosting, CDN & infrastructure | it.com second-level domain registry | 1145 |
| `firebaseio.com` | Abused hosting, CDN & infrastructure | Google Firebase Realtime Database | 1146 |
| `byteoversea.com` | Mainstream services (likely legitimate) | ByteDance/TikTok overseas infrastructure | 1163 |
| `yastatic.net` | Mainstream services (likely legitimate) | Yandex static CDN | 1201 |
| `torob.com` | Mainstream services (likely legitimate) | Torob Iranian price-comparison search engine | 1392 |
| `threads.net` | Mainstream services (likely legitimate) | Threads social network (Meta) | 1733 |
| `pusher.com` | Mainstream services (likely legitimate) | Realtime messaging API (Pusher) | 1785 |
| `tawk.to` | Mainstream services (likely legitimate) | Tawk.to free live-chat widget | 1793 |
| `marketingcloudapis.com` | Email marketing & mass-mail infrastructure | Salesforce Marketing Cloud tracking/APIs | 1796 |
| `overwolf.com` | Mainstream services (likely legitimate) | Overwolf gaming app platform | 1799 |
| `your-server.de` | Abused hosting, CDN & infrastructure | Hetzner customer hosting domain | 1807 |
| `rambler.ru` | Mainstream services (likely legitimate) | Russian web portal (Rambler) | 1815 |
| `cloudfunctions.net` | Abused hosting, CDN & infrastructure | Google Cloud Functions hosting | 1833 |
| `us.com` | Abused hosting, CDN & infrastructure | US.COM subdomain registry (CentralNic), abused subdomains | 1849 |
| `fb.watch` | Mainstream services (likely legitimate) | Facebook Watch short-link domain | 1960 |
| `livechatinc.com` | Mainstream services (likely legitimate) | LiveChat customer chat software | 2010 |
| `locaweb.com.br` | Abused hosting, CDN & infrastructure | Locaweb Brazilian hosting provider | 2023 |
| `symantec.com` | Mainstream services (likely legitimate) | Symantec security vendor (Broadcom) | 2127 |
| `example.org` | Mainstream services (likely legitimate) | IANA reserved example domain | 2211 |
| `aibixby.com` | Mainstream services (likely legitimate) | Samsung Bixby AI service domain | 2305 |
| `telegra.ph` | Abused hosting, CDN & infrastructure | Telegraph anonymous publishing, abused for scam pages | 2313 |
| `secureserver.net` | Abused hosting, CDN & infrastructure | GoDaddy hosting infrastructure | 2347 |
| `shorturl.at` | URL shorteners & link-in-bio | Free URL shortener | 2388 |
| `in.net` | Abused hosting, CDN & infrastructure | Second-level domain registry (in.net subdomains) | 2487 |
| `affirm.com` | Mainstream services (likely legitimate) | Buy-now-pay-later provider (Affirm) | 2521 |
| `ibb.co` | Abused hosting, CDN & infrastructure | ImgBB free image hosting | 2636 |
| `newsbreak.com` | Mainstream services (likely legitimate) | NewsBreak local news app | 2739 |
| `sportradar.com` | Mainstream services (likely legitimate) | Sports data/betting technology company | 2745 |
| `getpocket.com` | Mainstream services (likely legitimate) | Mozilla Pocket read-later service (discontinued) | 2802 |
| `tuyaeu.com` | Mainstream services (likely legitimate) | Tuya IoT smart-home cloud (EU) | 2861 |
| `imgix.net` | Abused hosting, CDN & infrastructure | Image CDN (imgix) | 2995 |
| `intercomcdn.com` | Mainstream services (likely legitimate) | Intercom CDN | 3026 |
| `drpc.org` | Mainstream services (likely legitimate) | dRPC blockchain RPC infrastructure | 3043 |
| `softonic.com` | Mainstream services (likely legitimate) | Software download portal (Softonic) | 3068 |
| `llamarpc.com` | Abused hosting, CDN & infrastructure | Public Ethereum RPC endpoint (crypto infra) | 3146 |
| `hinet.net` | Mainstream services (likely legitimate) | Chunghwa Telecom ISP portal (Taiwan) | 3194 |
| `coingecko.com` | Mainstream services (likely legitimate) | CoinGecko crypto price tracker | 3272 |
| `wixstatic.com` | Abused hosting, CDN & infrastructure | Wix static asset CDN | 3293 |
| `slack-edge.com` | Mainstream services (likely legitimate) | Slack static CDN | 3355 |
| `ibytedtos.com` | Mainstream services (likely legitimate) | ByteDance/TikTok object-storage CDN | 3457 |
| `judge.me` | Mainstream services (likely legitimate) | Shopify product reviews app (Judge.me) | 3614 |
| `sanity.io` | Mainstream services (likely legitimate) | Headless CMS platform (Sanity) | 3635 |
| `coindesk.com` | Mainstream services (likely legitimate) | CoinDesk crypto news | 3730 |
| `zoho.eu` | Mainstream services (likely legitimate) | Zoho business software suite (EU) | 3904 |
| `bingapis.com` | Mainstream services (likely legitimate) | Microsoft Bing API domain | 4021 |
| `dmca.com` | Mainstream services (likely legitimate) | DMCA.com takedown/badge service | 4129 |
| `backblazeb2.com` | Abused hosting, CDN & infrastructure | Backblaze B2 object storage | 4216 |
| `mcusercontent.com` | Email marketing & mass-mail infrastructure | Mailchimp user content hosting | 4284 |
| `is.gd` | URL shorteners & link-in-bio | URL shortener (is.gd) | 4294 |
| `postimg.cc` | Abused hosting, CDN & infrastructure | Free image hosting (Postimages) used for spam images | 4424 |
| `gist.build` | Email marketing & mass-mail infrastructure | Customer.io in-app messaging (Gist) | 4436 |
| `aihelp.net` | Mainstream services (likely legitimate) | Customer-support SaaS (AIHelp) | 4472 |
| `terabox.com` | Abused hosting, CDN & infrastructure | TeraBox cloud storage, abused for file sharing | 4524 |
| `freshchat.com` | Mainstream services (likely legitimate) | Freshworks chat SaaS (Freshchat) | 4594 |
| `zohocdn.com` | Mainstream services (likely legitimate) | Zoho CDN | 4646 |
| `r2.dev` | Abused hosting, CDN & infrastructure | Cloudflare R2 public object storage | 4738 |
| `jp.net` | Abused hosting, CDN & infrastructure | Second-level domain registry (jp.net) | 4785 |
| `kaufland.de` | Mainstream services (likely legitimate) | Kaufland Germany retailer/marketplace | 4801 |
| `zohopublic.com` | Email marketing & mass-mail infrastructure | Zoho Campaigns public/email asset domain | 4824 |
| `page.link` | URL shorteners & link-in-bio | Firebase Dynamic Links (Google) | 4879 |
| `yougov.com` | Mainstream services (likely legitimate) | YouGov market research/surveys | 5113 |
| `dhgate.com` | Mainstream services (likely legitimate) | DHgate Chinese marketplace | 5169 |
| `vix.com` | Mainstream services (likely legitimate) | ViX streaming (TelevisaUnivision) | 5289 |
| `wsimg.com` | Abused hosting, CDN & infrastructure | GoDaddy website-builder static CDN | 5347 |
| `hostingersite.com` | Abused hosting, CDN & infrastructure | Hostinger free/temporary site subdomains | 5782 |
| `ivoox.com` | Mainstream services (likely legitimate) | Spanish podcast platform (iVoox) | 5980 |
| `afterpay.com` | Mainstream services (likely legitimate) | Buy-now-pay-later provider (Afterpay) | 6083 |
| `prismic.io` | Mainstream services (likely legitimate) | Headless CMS platform (Prismic) | 6396 |
| `iot-dns.com` | Mainstream services (likely legitimate) | IoT device cloud/DNS service domain | 6416 |
| `sytes.net` | Abused hosting, CDN & infrastructure | No-IP free dynamic DNS domain | 6508 |
| `mjt.lu` | Email marketing & mass-mail infrastructure | Mailjet link tracking | 6755 |
| `me-qr.com` | URL shorteners & link-in-bio | QR-code generator/redirect service | 6852 |
| `crisp.chat` | Mainstream services (likely legitimate) | Crisp customer-support chat platform | 6885 |
| `hopto.org` | Abused hosting, CDN & infrastructure | No-IP free dynamic DNS domain | 7016 |
| `getjobber.com` | Mainstream services (likely legitimate) | Field-service business software (Jobber) | 7478 |
| `t.ly` | URL shorteners & link-in-bio | URL shortener (T.LY) | 7552 |
| `sbisec.co.jp` | Mainstream services (likely legitimate) | SBI Securities (Japan) | 7601 |
| `getresponse.com` | Email marketing & mass-mail infrastructure | Email marketing platform (GetResponse) | 7815 |
| `hubspotemail.net` | Email marketing & mass-mail infrastructure | HubSpot email sending/tracking | 8370 |
| `rebrand.ly` | URL shorteners & link-in-bio | Rebrandly URL shortener | 8608 |
| `sa.com` | Abused hosting, CDN & infrastructure | CentralNic SLD namespace abused for spam subdomains | 8739 |
| `kozow.com` | Abused hosting, CDN & infrastructure | Dynu free dynamic DNS domain | 8792 |
| `outreach.io` | Email marketing & mass-mail infrastructure | Outreach sales-engagement email platform | 8871 |
| `rb.gy` | URL shorteners & link-in-bio | Free URL shortener (Rebrandly rb.gy) | 9233 |
| `detran.sp.gov.br` | Mainstream services (likely legitimate) | Sao Paulo state traffic department (gov) | 9604 |
| `confirmit.com` | Mainstream services (likely legitimate) | Forsta/Confirmit survey research platform | 10021 |
| `omny.fm` | Mainstream services (likely legitimate) | Omny Studio podcast hosting (Triton) | 10229 |
| `ettoday.net` | Mainstream services (likely legitimate) | ETtoday Taiwanese news portal | 11021 |
| `google.vu` | Mainstream services (likely legitimate) | Google Vanuatu search (abused as open redirect) | 11542 |
| `gyazo.com` | Mainstream services (likely legitimate) | Screenshot sharing service (Gyazo) | 11650 |
| `filmfreeway.com` | Mainstream services (likely legitimate) | FilmFreeway festival submission platform | 11765 |
| `avastbrowser.com` | Mainstream services (likely legitimate) | Avast Secure Browser | 11812 |
| `schemaapp.com` | Mainstream services (likely legitimate) | Schema markup SaaS | 11872 |
| `rmbl.ws` | Mainstream services (likely legitimate) | Rumble video short domain | 11873 |
| `blockchain.com` | Mainstream services (likely legitimate) | Crypto wallet/exchange (Blockchain.com) | 11884 |
| `swagbucks.com` | Mainstream services (likely legitimate) | Swagbucks rewards/survey site (Prodege), used in lead-gen funnels | 11917 |
| `enamad.ir` | Mainstream services (likely legitimate) | Iranian government e-commerce trust seal | 13177 |
| `walletconnect.org` | Mainstream services (likely legitimate) | WalletConnect crypto wallet protocol | 13348 |
| `wenxuecity.com` | Mainstream services (likely legitimate) | Wenxuecity Chinese-language news portal | 13751 |
| `blogblog.com` | Mainstream services (likely legitimate) | Google Blogger legacy domain | 15693 |
| `shortpixel.ai` | Mainstream services (likely legitimate) | Image optimization CDN (ShortPixel) | 16280 |
| `download.com` | Mainstream services (likely legitimate) | CNET Download software portal | 16343 |
| `teamwork.com` | Mainstream services (likely legitimate) | Teamwork.com project management SaaS | 16706 |
| `bnbchain.org` | Mainstream services (likely legitimate) | BNB Chain blockchain official site | 16749 |
| `privacypolicies.com` | Mainstream services (likely legitimate) | Privacy policy generator service | 17240 |
| `talentlms.com` | Mainstream services (likely legitimate) | TalentLMS e-learning SaaS | 17568 |
| `searchspring.net` | Mainstream services (likely legitimate) | E-commerce site search (Searchspring/Athos) | 18101 |
| `decagon.ai` | Mainstream services (likely legitimate) | Decagon AI customer-service company | 18832 |
| `westfield.com` | Mainstream services (likely legitimate) | Westfield shopping centres | 19540 |
| `picsum.photos` | Mainstream services (likely legitimate) | Lorem Picsum placeholder image service | 20265 |
| `ionicframework.com` | Mainstream services (likely legitimate) | Ionic app development framework | 20340 |
| `base.org` | Mainstream services (likely legitimate) | Coinbase Base blockchain network | 21073 |
| `tines.com` | Mainstream services (likely legitimate) | Tines security automation SaaS | 21428 |
| `ita-airways.com` | Mainstream services (likely legitimate) | ITA Airways (Italian airline) | 23908 |
| `bitvavo.com` | Mainstream services (likely legitimate) | Dutch crypto exchange (Bitvavo) | 24042 |
| `wpforms.com` | Mainstream services (likely legitimate) | WordPress form plugin vendor (WPForms) | 24141 |
| `web3modal.org` | Mainstream services (likely legitimate) | WalletConnect Web3Modal API domain used by crypto dApps | 26414 |
| `cbsistatic.com` | Mainstream services (likely legitimate) | CBS Interactive static content CDN | 27634 |
| `meo.pt` | Mainstream services (likely legitimate) | MEO Portuguese telecom | 27973 |
| `stylecraze.com` | Mainstream services (likely legitimate) | Beauty content website (StyleCraze) | 29329 |
| `ui-avatars.com` | Mainstream services (likely legitimate) | Avatar image API (UI Avatars) | 34955 |
| `helloextend.com` | Mainstream services (likely legitimate) | Product warranty platform (Extend) | 37138 |
| `wallpaperaccess.com` | Mainstream services (likely legitimate) | Free wallpaper site, likely image hotlinking | 37783 |
| `investorplace.com` | Mainstream services (likely legitimate) | Stock newsletter publisher (InvestorPlace), heavy email marketing | 38102 |
| `vcita.com` | Mainstream services (likely legitimate) | vcita small-business CRM/scheduling SaaS | 38130 |
| `omnycontent.com` | Mainstream services (likely legitimate) | Omny Studio podcast content CDN | 38764 |
| `legitscript.com` | Mainstream services (likely legitimate) | LegitScript merchant certification/monitoring service | 39732 |
| `cookiepedia.co.uk` | Mainstream services (likely legitimate) | OneTrust cookie information site | 40748 |
| `revenuehunt.com` | Mainstream services (likely legitimate) | Shopify product recommendation quiz app | 41180 |
| `judicialwatch.org` | Mainstream services (likely legitimate) | US political watchdog org (Judicial Watch), mass mailer | 44067 |
| `enjin.com` | Mainstream services (likely legitimate) | Enjin blockchain gaming platform | 44083 |
| `redbutton.de` | Mainstream services (likely legitimate) | German HbbTV red-button TV platform | 45419 |
| `linda.nl` | Mainstream services (likely legitimate) | LINDA. Dutch magazine (DPG Media) | 45596 |
| `cex.io` | Mainstream services (likely legitimate) | CEX.IO crypto exchange | 48137 |
| `towbook.com` | Mainstream services (likely legitimate) | Towing dispatch software SaaS (Towbook) | 53215 |
| `kustom.co` | Mainstream services (likely legitimate) | Checkout/payments platform (Kustom) | 53935 |
| `nexo.com` | Mainstream services (likely legitimate) | Nexo crypto lending platform | 55521 |
| `octocom.ai` | Mainstream services (likely legitimate) | Octocom AI customer-support SaaS | 55737 |
| `sleekplan.com` | Mainstream services (likely legitimate) | Customer feedback SaaS | 58245 |
| `mamma.com` | Mainstream services (likely legitimate) | Legacy metasearch portal (Mamma.com) | 60951 |
| `chatbro.com` | Mainstream services (likely legitimate) | ChatBro website chat widget service | 69601 |
| `yourmechanic.com` | Mainstream services (likely legitimate) | YourMechanic auto repair service | 71197 |
| `enjin.io` | Mainstream services (likely legitimate) | Enjin blockchain gaming platform | 87410 |
| `megaeth.com` | Mainstream services (likely legitimate) | MegaETH blockchain project | 105964 |
| `coinlib.io` | Mainstream services (likely legitimate) | Coinlib crypto price site | 107154 |
| `toontrack.com` | Mainstream services (likely legitimate) | Music production software vendor (Toontrack) | 110626 |
| `paytomorrow.com` | Mainstream services (likely legitimate) | PayTomorrow consumer financing | 111676 |
| `cloudflare-terms-of-service-abuse.com` | Mainstream services (likely legitimate) | Cloudflare abuse interstitial domain | 116364 |
| `mediahuis.be` | Mainstream services (likely legitimate) | Mediahuis Belgian news publisher | 126165 |
| `fakturownia.pl` | Mainstream services (likely legitimate) | Polish online invoicing SaaS | 128221 |
| `logos-world.net` | Mainstream services (likely legitimate) | Logo image reference site (images used in mails) | 130230 |
| `brightside.com` | Mainstream services (likely legitimate) | Viral content publisher (Bright Side) | 136273 |
| `softonic.nl` | Mainstream services (likely legitimate) | Softonic Dutch download portal | 142140 |
| `associates-amazon.com` | Mainstream services (likely legitimate) | Amazon Associates affiliate domain | 144015 |
| `ixopay.com` | Mainstream services (likely legitimate) | Payment orchestration (IXOPAY) | 145454 |
| `mcafeeassets.com` | Mainstream services (likely legitimate) | McAfee asset CDN | 155768 |
| `urbanmatter.com` | Mainstream services (likely legitimate) | Local news/entertainment site (UrbanMatter) | 185569 |
| `intrum.com` | Mainstream services (likely legitimate) | Debt collection company (Intrum) | 186170 |
| `dealclub.de` | Mainstream services (likely legitimate) | German discount deal shop | 192445 |
| `lifelinescreening.com` | Mainstream services (likely legitimate) | Life Line Screening health-screening company | 227039 |
| `offeringtree.com` | Mainstream services (likely legitimate) | OfferingTree fitness business software | 231113 |
| `linkedinmobileapp.com` | Mainstream services (likely legitimate) | LinkedIn official app redirect domain | 235079 |
| `lesechos.com` | Mainstream services (likely legitimate) | Les Echos French financial newspaper | 237313 |
| `eventleaf.com` | Mainstream services (likely legitimate) | Eventleaf event management software | 248200 |
| `repairshopr.com` | Mainstream services (likely legitimate) | Computer repair shop CRM software | 265740 |
| `gamingcommission.ca` | Mainstream services (likely legitimate) | Kahnawake Gaming Commission regulator (linked from casino footers) | 266789 |
| `followchain.org` | Mainstream services (likely legitimate) | Social-media how-to content site | 303957 |
| `adlock.com` | Mainstream services (likely legitimate) | Commercial ad-blocker vendor (AdLock) | 318479 |
| `itsocial.fr` | Mainstream services (likely legitimate) | French IT news media (IT Social) | 319304 |
| `invidio.us` | Mainstream services (likely legitimate) | Invidious YouTube front-end (defunct) | 325165 |
| `be-mobile.biz` | Mainstream services (likely legitimate) | Smart mobility company (Be-Mobile) | 332302 |
| `skin1004.com` | Mainstream services (likely legitimate) | Korean skincare brand | 336125 |
| `eventbookings.com` | Mainstream services (likely legitimate) | EventBookings ticketing platform | 376095 |
| `newspark.ca` | Mainstream services (likely legitimate) | NewSpark UGC platform | 402703 |
| `momo.com` | Mainstream services (likely legitimate) | MOMO motorsport brand site | 427871 |
| `squidex.io` | Mainstream services (likely legitimate) | Open-source headless CMS (Squidex) | 454456 |
| `ofix.com` | Mainstream services (likely legitimate) | Ofix Turkish office supplies retailer | 464729 |
| `saopaulo.sp.gov.br` | Mainstream services (likely legitimate) | Sao Paulo state government | 503548 |
| `jeux.ca` | Mainstream services (likely legitimate) | French-Canadian gaming news site | 556984 |
| `monclubsportif.com` | Mainstream services (likely legitimate) | Sports team management software | 678048 |
| `talpanetwork.com` | Mainstream services (likely legitimate) | Talpa Network Dutch media company | 689668 |
| `tradehq.com.au` | Mainstream services (likely legitimate) | Job management SaaS for tradespeople (TradeHQ) | 735812 |
| `avastdns.com` | Mainstream services (likely legitimate) | Avast DNS infrastructure | 891517 |
| `salmonbusiness.com` | Mainstream services (likely legitimate) | Salmon industry news site | 907520 |
| `ketogenic.com` | Mainstream services (likely legitimate) | Keto diet information site | 983871 |
| `amazonantitrustlitigation.com` | Mainstream services (likely legitimate) | Class-action settlement notice site (Epiq) | – |
| `arqiva.tv` | Mainstream services (likely legitimate) | UK broadcast infrastructure company (Arqiva) | – |
| `attendancebot.com` | Mainstream services (likely legitimate) | Attendance tracking SaaS (AttendanceBot) | – |
| `barbera.io` | Mainstream services (likely legitimate) | Salon booking/POS SaaS (Barbera) | – |
| `bigtechinterviews.com` | Mainstream services (likely legitimate) | Tech interview prep site | – |
| `billgrid.com` | Mainstream services (likely legitimate) | Invoicing SaaS (BillGrid) | – |
| `buildern.com` | Mainstream services (likely legitimate) | Construction management SaaS (Buildern) | – |
| `com.br` | Mainstream services (likely legitimate) | Brazilian public suffix (registry SLD); never block whole | – |
| `corp.google.com` | Mainstream services (likely legitimate) | Google internal corporate domain | – |
| `ebayclassifieds.net` | Mainstream services (likely legitimate) | Likely eBay defensive domain | – |
| `electrabel.com` | Mainstream services (likely legitimate) | Electrabel/ENGIE Belgian energy company | – |
| `geekai.co` | Mainstream services (likely legitimate) | Chinese AI chatbot aggregator (GeekAI) | – |
| `ia.media-imdb.com` | Mainstream services (likely legitimate) | IMDb/Amazon image CDN | – |
| `invoicehippo.nl` | Mainstream services (likely legitimate) | Dutch invoicing SaaS (InvoiceHippo) | – |
| `line.pm` | Mainstream services (likely legitimate) | Line Budgeter production-budget SaaS short domain | – |
| `login.corp.google.com` | Mainstream services (likely legitimate) | Google corporate SSO | – |
| `merchantpool1.linkedin.com` | Mainstream services (likely legitimate) | LinkedIn infrastructure host | – |
| `net.in` | Mainstream services (likely legitimate) | Indian .net.in public-suffix zone, blocking causes collateral | – |
| `oddgrenland.no` | Mainstream services (likely legitimate) | ODD Grenland Norwegian football club site | – |
| `or.jp` | Mainstream services (likely legitimate) | Japanese .or.jp public-suffix zone, blocking causes collateral | – |
| `publicsonar.com` | Mainstream services (likely legitimate) | Media monitoring, now Maltego Monitor | – |
| `rsvpify.org` | Mainstream services (likely legitimate) | RSVPify event RSVP software | – |
| `safebrowsing.googleapis.com` | Mainstream services (likely legitimate) | Google Safe Browsing API | – |
| `sendcloud.fr` | Mainstream services (likely legitimate) | Parcel shipping platform (Sendcloud) | – |
| `sharesale.com` | Mainstream services (likely legitimate) | ShareASale typo domain redirecting to News UK | – |
| `skybot.fr` | Mainstream services (likely legitimate) | French Discord bot site | – |
| `solvvy.com` | Mainstream services (likely legitimate) | Support chatbot, now Zoom Virtual Agent | – |
| `topics.nl` | Mainstream services (likely legitimate) | DPG Media property (Dutch publisher) | – |
| `trytines.com` | Mainstream services (likely legitimate) | Tines marketing domain redirecting to tines.com | – |
| `userlocation.googleapis.com` | Mainstream services (likely legitimate) | Google user-location API endpoint | – |
| `valap.com` | Mainstream services (likely legitimate) | French wine private-sales retailer (Vente a la Propriete) | – |
| `vatsim.com` | Mainstream services (likely legitimate) | VATSIM flight-sim network domain | – |
| `vorlagen.com` | Mainstream services (likely legitimate) | German Office template download site | – |

## Most dangerous domains still online (top 40)

| Domain | Category | Why | Score | Also on |
|---|---|---|---:|---|
| `littlecdn.com` | Malware, PUPs & tech-support scams | Obscure CDN flagged as malware | 95 | BLP-malware |
| `roblox.ly` | Phishing & brand impersonation | Roblox lookalike phishing (.ly) | 95 | RPiList-Malware, RPiList-Phishing, OpenPhish |
| `roblox.com.ml` | Phishing & brand impersonation | Roblox lookalike phishing (com.ml) | 90 | BLP-fraud, BLP-malware, RPiList-Malware, RPiList-Phishing, Phishing.Database |
| `auth-ledger.at` | Phishing & brand impersonation | Ledger wallet phishing lookalike | 85 | BLP-malware, RPiList-Malware |
| `gdmsecure-ig.com` | Phishing & brand impersonation | Likely Instagram 'secure' phishing domain | 85 | BLP-malware |
| `penandinkeyot.online` | Phishing & brand impersonation | Flagged by Cloudflare as phishing | 85 | – |
| `profityxchase.com` | Phishing & brand impersonation | Profity cluster with Chase name, likely phishing | 85 | BLP-malware |
| `realmensgrowth.online` | Fake shops & product scams | Male enhancement video-sales funnel | 85 | BLP-malware |
| `roblox.com.am` | Phishing & brand impersonation | Roblox lookalike phishing (com.am) | 85 | RPiList-Malware, RPiList-Phishing |
| `robloxc.com.es` | Phishing & brand impersonation | Roblox typosquat phishing (com.es) | 85 | BLP-malware, RPiList-Malware, RPiList-Phishing |
| `robloxr.com.es` | Phishing & brand impersonation | Roblox typosquat phishing (com.es) | 85 | BLP-malware, RPiList-Malware |
| `rponline.online` | Investment, crypto & money scams | Likely fake RP Online news page for investment scam | 85 | – |
| `user-id.es` | Phishing & brand impersonation | Cloudflare-flagged phishing domain | 85 | RPiList-Malware, RPiList-Phishing |
| `vodafone-on-line.it` | Phishing & brand impersonation | Vodafone lookalike (Italy) | 85 | RPiList-Malware, RPiList-Phishing |
| `webauthdesktop.co` | Malware, PUPs & tech-support scams | Fake crypto wallet desktop app download | 85 | BLP-malware |
| `app-review.to` | Phishing & brand impersonation | Generic store white page, same template as Ledger phish | 80 | – |
| `conecschoolba.click` | Redirects, link tracking & cloaking | Throwaway .click redirector | 80 | BLP-malware |
| `get-akusoli.com` | Fake shops & product scams | Akusoli insoles dropship funnel | 80 | BLP-malware |
| `get-derila-ergo.com` | Fake shops & product scams | Derila Ergo pillow dropship funnel | 80 | BLP-malware |
| `normanvilleelectrical.com` | Phishing & brand impersonation | Flagged by Cloudflare as phishing | 80 | – |
| `soaurb.com` | Redirects, link tracking & cloaking | Cloaker redirecting bots to Google | 80 | BLP-malware |
| `support-tw.com` | Phishing & brand impersonation | Fake support domain, likely phishing | 80 | – |
| `tollroadways.com` | Phishing & brand impersonation | Toll-road payment phishing lure | 80 | – |
| `trendmakers.shop` | Spam, lead-gen & prize scams | Arabic digital-agency template site, likely spam front | 80 | BLP-malware |
| `247qbonline.com` | Malware, PUPs & tech-support scams | QuickBooks 24/7 support lookalike (tech-support scam) | 75 | – |
| `bonhelth.live` | Fake shops & product scams | Health-named throwaway domain, placeholder | 75 | – |
| `collectivequestioningcompartment.com` | Redirects, link tracking & cloaking | Random three-word ad redirect domain | 75 | BLP-ads, BLP-malware |
| `dry-aging-meat.shop` | Fake shops & product scams | Throwaway shop domain | 75 | – |
| `ewallst.com` | Investment, crypto & money scams | Stock-promotion fake news site | 75 | – |
| `get-derila.com` | Fake shops & product scams | Derila pillow dropship funnel | 75 | BLP-fraud, BLP-malware, RPiList-Malware, StevenBlack |
| `get-matsato.com` | Fake shops & product scams | Matsato knife dropship funnel | 75 | BLP-malware |
| `getnuubu.com` | Fake shops & product scams | Nuubu detox foot patch funnel | 75 | BLP-malware |
| `homedecorhaven.site` | Fake shops & product scams | Throwaway home-decor shop site, suspended | 75 | – |
| `konvektoren.shop` | Fake shops & product scams | Likely German convector-heater fake shop | 75 | – |
| `lebara-shop.nl` | Phishing & brand impersonation | Lebara-branded shop domain, likely lookalike/clone | 75 | – |
| `paperchairone.com` | Spam, lead-gen & prize scams | Random-word spam unsubscribe page domain | 75 | BLP-malware |
| `polyfill.io` | Malware, PUPs & tech-support scams | Polyfill.io CDN hijacked in 2024 supply-chain attack | 75 | BLP-ads, BLP-malware, RPiList-Malware |
| `purefinds.site` | Fake shops & product scams | Likely fake shop/product funnel | 75 | – |
| `smarttechsolutions.store` | Fake shops & product scams | Gadget webshop with 40% off promo, likely fake | 75 | – |
| `techgenuiess.com` | Malware, PUPs & tech-support scams | Misspelled 'tech genius' name, likely tech-support/PUP scam | 75 | – |

## Sources

- DNS via Google Public DNS (DNS-over-HTTPS), homepage via a plain HTTPS/HTTP request (no JavaScript).
- Registration data via RDAP (the registries' official WHOIS successor). Some TLDs (.de, .us, .ru, .np …) have no public RDAP.
- Other blocklists: [Blocklist Project](https://github.com/blocklistproject/Lists) (ads, tracking, phishing, scam, fraud, malware, gambling, redirect),
  [Phishing.Database](https://github.com/Phishing-Database/Phishing.Database), [OpenPhish](https://openphish.com),
  [StevenBlack hosts](https://github.com/StevenBlack/hosts) and [Firebog](https://firebog.net) lists (AdGuard DNS, EasyList, EasyPrivacy, Prigent, RPiList, Spam404).
- Popularity via the [Tranco](https://tranco-list.eu) top 1 million.

## Columns in `domains.csv`

`domain`, `category`, `category_code`, `reason`, `confidence`, `exists` (yes/no/unknown), `status`, `status_detail`,
`threat_score`, `breakage_risk`, `registered`, `expires`, `registrar`, `registry_status`, `ip`, `nameservers`, `http`
(status code of the homepage), `redirects_to` (if the homepage sends you to another domain), `page_title`,
`other_blocklists`, `other_blocklists_count`, `tranco_rank`, `score_breakdown`.
