# No more ads, tracking and other virtual garbage
All blocklists are gathered from multiple, actively maintained sources and automatically updated, cleaned, optimized and moderated on a daily basis. The main [domains.txt](domains.txt) and [hostnames.txt](hostnames.txt) are designed for usage with [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html), but a [dnscrypt-proxy](https://github.com/DNSCrypt/dnscrypt-proxy) [combined blacklist](dnscrypt-proxy/dnscrypt-proxy.blacklist.txt) with the same coverage is also available as it has the added benifit of being able to [block](https://github.com/DNSCrypt/dnscrypt-proxy/issues/1067) [cnames](https://github.com/uBlockOrigin/uBlock-issues/issues/780).

## General blocklist policies
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks scam websites
 - Blocks malware servers
 - Blocks webminers
 - Blocks phishing servers
 
## Optimization
The optimizer makes full use of domainname based wildcard filtering `*.doubleclick.net`, this reduces the chance of missing any new subdomains and significantly reduces the size of the blocklists. Hostnames that cannot be blocked on a domain level will still be listed in a regular hostname based blocklist.

## Dead hosts removal
All hostname DNS records are constantly monitored for updates. In case the A, AAAA, CNAME and NS records return NXDOMAIN they will be marked as dead and removed from hostnames.txt. Domains are tested on their whois data, all unregistered domains will be filtered out of domains.txt.

The current list of dead hostnames can be found [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/hostnames.dead.txt) and have a look [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/domains.dead.txt) for all unregistered domains.

## DNS over HTTPS (DOH)
DNS over HTTPS will prevent clients in your network from using the default local DNS services. Mozilla Firefox has a feature to disable DOH network wide for all clients as described [here](https://support.mozilla.org/en-US/kb/configuring-networks-disable-dns-over-https).

All domain and combined lists will block the canary domain `use-application-dns.net`, disabeling DOH by default on all clients.

# How to install
 - [Instructions for dnsmasq](https://github.com/notracking/hosts-blocklists/wiki/Install-dnsmasq)
 - [Instructions for dnscrypt-proxy](https://github.com/notracking/hosts-blocklists/wiki/Install-dnscrypt-proxy)
 - [Instructions for Pi-hole](https://github.com/notracking/hosts-blocklists/wiki/Install-pi-hole)

## Supporting Notracking blocklist
You can support in multiple ways:
 - Submit false positives
 - Submit new (tested) sources
 - [Donate with Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=VPTVYWY3B7XWG&source=url)
 
*Donations are used to pay for hosting bills, generation of the blocklists cost more resources then you might expect (running databases, 24/7 active updating of whois info etc..)*

# Sources
**Domain and hostname lists**
 - http://winhelp2002.mvps.org/hosts.txt
 - https://www.malwaredomainlist.com/hostslist/hosts.txt
 - https://someonewhocares.org/hosts/
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malvertising.txt
 - https://pgl.yoyo.org/as/serverlist.php?hostformat=hosts
 - https://raw.githubusercontent.com/StevenBlack/hosts/master/data/StevenBlack/hosts
 - http://malwaredomains.lehigh.edu/files/BOOT
 - http://malwaredomains.lehigh.edu/files/immortal_domains.txt
 - https://raw.githubusercontent.com/vokins/yhosts/master/hosts.txt `Excluding legit license servers`
 - https://raw.githubusercontent.com/piwik/referrer-spam-blacklist/master/spammers.txt
 - https://raw.githubusercontent.com/crazy-max/WindowsSpyBlocker/master/data/hosts/spy.txt
 - https://raw.githubusercontent.com/AdAway/adaway.github.io/master/hosts.txt
 - https://www.dshield.org/feeds/suspiciousdomains_Medium.txt
 - https://raw.githubusercontent.com/mitchellkrogza/Badd-Boyz-Hosts/master/hosts
 - https://dsi.ut-capitole.fr/blacklists/download/publicite.tar.gz `only 'publicite' list`
 - https://ssl.bblck.me/blacklists/hosts-file.txt
 - https://v.firebog.net/hosts/static/w3kbl.txt
 - https://raw.githubusercontent.com/Yhonay/antipopads/master/hosts
 - https://raw.githubusercontent.com/MajkiIT/polish-ads-filter/master/polish-pihole-filters/hostfile.txt
 - https://gitlab.com/ZeroDot1/CoinBlockerLists/raw/master/list_browser.txt
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/StreamingAds/hosts
 - https://raw.githubusercontent.com/azet12/KADhosts/master/KADhosts.txt
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/UncheckyAds/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Spam/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Risk/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Dead/hosts
 - https://raw.githubusercontent.com/mitchellkrogza/The-Big-List-of-Hacked-Malware-Web-Sites/master/.dev-tools/output/domains/ACTIVE/list
 - https://malc0de.com/bl/BOOT
 - https://raw.githubusercontent.com/hoshsadiq/adblock-nocoin-list/master/hosts.txt
 - https://data.netlab.360.com/feeds/dga/dircrypt.txt
 - https://data.netlab.360.com/feeds/dga/fobber.txt
 - https://data.netlab.360.com/feeds/dga/ccleaner.txt
 - https://data.netlab.360.com/feeds/dga/matsnu.txt
 - https://data.netlab.360.com/feeds/dga/tofsee.txt
 - https://data.netlab.360.com/feeds/dga/xshellghost.txt
 - https://osint.bambenekconsulting.com/feeds/c2-dommasterlist-high.txt
 - http://security-research.dyndns.org/pub/malware-feeds/ponmocup-infected-domains-shadowserver.csv
 - https://raw.githubusercontent.com/DandelionSprout/adfilt/master/NorwegianExperimentalList%20alternate%20versions/NordicFiltersDnsmasq.conf
 - https://raw.githubusercontent.com/DandelionSprout/adfilt/master/Alternate%20versions%20Anti-Malware%20List/AntiMalwareHosts.txt
 - https://raw.githubusercontent.com/Akamaru/Pi-Hole-Lists/master/gamefake.txt
 - https://raw.githubusercontent.com/Akamaru/Pi-Hole-Lists/master/mobile.txt
 - https://raw.githubusercontent.com/jdlingyu/ad-wars/master/hosts
 - https://raw.githubusercontent.com/neoFelhz/neohosts/data/_data/basic/common.txt
 - https://raw.githubusercontent.com/Perflyst/PiHoleBlocklist/master/SmartTV.txt
 - https://phishing.army/download/phishing_army_blocklist.txt
 - https://dehakkelaar.nl/lists/cryptojacking_campaign.list.txt
 - https://raw.githubusercontent.com/PoorPocketsMcNewHold/SteamScamSites/master/steamscamsite.txt
 - https://raw.githubusercontent.com/Kees1958/WS3_annual_most_used_survey_blocklist/master/w3tech_hostfile.txt
 - https://infosec.cert-pa.it/analyze/listdomains.txt
 - https://www.botvrij.eu/data/ioclist.domain.raw
 - https://www.botvrij.eu/data/ioclist.hostname.raw
 - https://www.joewein.net/dl/bl/dom-bl.txt
 - https://infosharing.cybersaiyan.it/feeds/CS-PIHOLE
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/bad_service.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_fallout.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_grandsoft.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_neutrino.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_purplefox.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_radio.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_rig.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_router.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_shade.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_spelevo.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/ek_underminer.txt
 - https://raw.githubusercontent.com/stamparm/maltrail/master/trails/static/malicious/magentocore.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/cert-pa.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/yoroi.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/citizenlab.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/malware-traffic-analysis.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/pan-unit42.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/tgsoft.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/zscaler.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/checkpoint.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/symantec.txt
 - https://raw.githubusercontent.com/scafroglia93/hosts-blocklists/master/eset.txt
 - https://raw.githubusercontent.com/nextdns/cname-cloaking-blocklist/master/domains
 - https://raw.githubusercontent.com/Spam404/lists/master/main-blacklist.txt
 - https://openphish.com/feed.txt `only full domain filters`
 - https://raw.githubusercontent.com/stamparm/blackbook/master/blackbook.txt
 - a large set of custom entries
  
**Adblock Plus lists** (only full hostname, non-3rd party filters)
 - https://raw.githubusercontent.com/Spam404/lists/master/adblock-list.txt
 - https://www.fanboy.co.nz/enhancedstats.txt
 - https://easylist-downloads.adblockplus.org/easylist.txt
 - https://easylist-downloads.adblockplus.org/easylistchina.txt
 - https://easylist-downloads.adblockplus.org/easylistdutch.txt
 - https://easylist-downloads.adblockplus.org/easylistgermany.txt
 - https://raw.githubusercontent.com/MajkiIT/polish-ads-filter/master/polish-adblock-filters/adblock.txt
 - https://easylist-downloads.adblockplus.org/easylistspanish.txt
 - https://easylist-downloads.adblockplus.org/liste_fr.txt
 - https://easylist-downloads.adblockplus.org/easylistitaly.txt
 - https://www.void.gr/kargig/void-gr-filters.txt
 - https://raw.githubusercontent.com/uBlockOrigin/uAssets/master/filters/badware.txt
 - https://raw.githubusercontent.com/uBlockOrigin/uAssets/master/filters/filters.txt
 - https://raw.githubusercontent.com/uBlockOrigin/uAssets/master/filters/privacy.txt
 - https://raw.githubusercontent.com/uBlockOrigin/uAssets/master/filters/resource-abuse.txt
 - https://raw.githubusercontent.com/abpvn/abpvn/master/filter/src/abpvn_general.txt
 - https://raw.githubusercontent.com/szpeter80/hufilter/master/hufilter.txt
 - https://easylist-downloads.adblockplus.org/advblock.txt
 - https://raw.githubusercontent.com/yous/YousList/master/youslist.txt
 - https://raw.githubusercontent.com/jspenguin2017/uBlockProtector/master/uBlockProtectorList.txt
 - https://filters.adtidy.org/extension/chromium/filters/11.txt
 - https://filters.adtidy.org/extension/chromium/filters/1.txt
 - https://filters.adtidy.org/extension/chromium/filters/16.txt
 - https://filters.adtidy.org/extension/chromium/filters/7.txt
 - https://filters.adtidy.org/extension/chromium/filters/9.txt
 - https://filters.adtidy.org/extension/chromium/filters/13.txt
 - https://easylist-downloads.adblockplus.org/Liste_AR.txt
 - https://raw.githubusercontent.com/easylist/EasyListHebrew/master/EasyListHebrew.txt
 - https://raw.githubusercontent.com/ABPindo/indonesianadblockrules/master/subscriptions/abpindo.txt
 - https://raw.githubusercontent.com/realodix/AdBlockID/master/output/adblockid.txt
 - https://raw.githubusercontent.com/tomasko126/easylistczechandslovak/master/filters.txt
 - https://notabug.org/latvian-list/adblock-latvian/raw/master/lists/latvian-list.txt
