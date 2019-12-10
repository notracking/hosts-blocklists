# No more ads, tracking and other virtual garbage
This repository provides a host and domainname based blocklist specifically designed for use with dnsmasq.
Most entries are gathered from multiple, actively maintained sources and automatically updated, cleaned, optimized and moderated on a daily basis. The blocklists support both ipv4 and ipv6.

## General blocklist policies
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks fake websites
 - Blocks malware servers
 - Blocks webminers
 - Blocks phishing servers
 
## Optimization
The optimizer makes full use of dnsmasqs capability to block entire domains such as *.doubleclick.net ([domains.txt](https://raw.github.com/notracking/hosts-blocklists/master/domains.txt)). This reduces the chance of missing any new subdomains and significantly reduces the size of the blocklists. Hostnames that cannot be blocked on a domain level will still be listed in a regular hostname based blocklist ([hostnames.txt](https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt)).

It's important to use both `domains.txt` and `hostnames.txt` simultaneously in dnsmasq to get full coverage!

## Dead hosts removal
All hostname DNS records are constantly monitored for updates. In case the A, AAAA, CNAME and NS records return NXDOMAIN they will be marked as dead and removed from hostnames.txt. Domains are tested on their whois data, all unregistered domains will be filtered out of domains.txt.

The current list of dead hostnames can be found [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/hostnames.dead.txt) and have a look [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/domains.dead.txt) for all unregistered domains.

# How to install
## Default dnsmasq setup
 - Download the following two files (or use a daily cronjob to do it automatically)
```
https://raw.githubusercontent.com/notracking/hosts-blocklists/master/hostnames.txt
https://raw.githubusercontent.com/notracking/hosts-blocklists/master/domains.txt
```
 - Add the following lines to your dnsmasq.conf
```
conf-file=/path/to/domains.txt
addn-hosts=/path/to/hostnames.txt
```
 - Restart dnsmasq (reload will **not** update list changes) `sudo service dnsmasq restart`

## Automatic update and whitelist script
For automatic updates and whitelisting on Debian based systems you can use the [notracking update script](https://raw.githubusercontent.com/notracking/hosts-blocklists-scripts/master/notracking_update) as a daily cronjob (detailed instructions inside).

## For a Pi-hole setup
Pi-hole is a webinterface (and more) on top of dnsmasq, but it does not support loading of dnsmasq based domain filters ([details here](https://github.com/pi-hole/pi-hole/blob/1e87850952b6d886674b487f57e47fae1c20dc8a/gravity.sh#L338)). In order to use the dnsmasq domain capabilities you should add your own `.conf` file in `/etc/dnsmasq.d/`. This way you can still use the notracking blocklists within Pi-hole. 

Please note that it is required to update the notracking lists automatically by using an external [daily cronjob](https://github.com/notracking/hosts-blocklists#automatic-update-and-whitelist-script) (instructions inside). It's also recommended to remove all default Pi-hole lists, since these are already included in our list in a more efficient manner.

 - Add (and edit) the following lines to `/etc/dnsmasq.d/99-notracking-lists.conf`
```
conf-file=/path/to/domains.txt
addn-hosts=/path/to/hostnames.txt
```
 - Remove the default Pi-hole lists in `/etc/pihole/adlists.list`
 - Update Pi-hole `pihole -g`
 - Add a [daily cronjob](https://github.com/notracking/hosts-blocklists#automatic-update-and-whitelist-script) to automatically update

## DNS over HTTPS (DOH)
DNS over HTTPS will prevent clients in your network from using the default local DNS services. Mozilla Firefox has a feature to disable DOH network wide for all clients as described [here](https://support.mozilla.org/en-US/kb/configuring-networks-disable-dns-over-https).

If you use [domains.txt](https://raw.githubusercontent.com/notracking/hosts-blocklists/master/domains.txt) in your dnsmasq configuration you will have DOH disabled on all clients by default.

## Donations
Donations are welcome and will be used to pay for our dedicated server hosting bills: ❤️ [donate with Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=VPTVYWY3B7XWG&source=url)

# Sources
**Domain and hostname lists**
 - http://winhelp2002.mvps.org/hosts.txt
 - http://www.malwaredomainlist.com/hostslist/hosts.txt
 - http://someonewhocares.org/hosts/hosts/
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malvertising.txt
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malware.txt
 - http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts
 - https://raw.githubusercontent.com/StevenBlack/hosts/master/data/StevenBlack/hosts
 - https://raw.githubusercontent.com/Dawsey21/Lists/master/adblock-list.txt
 - http://malwaredomains.lehigh.edu/files/BOOT
 - http://malwaredomains.lehigh.edu/files/immortal_domains.txt
 - https://raw.githubusercontent.com/vokins/yhosts/master/hosts.txt `Excluding legit license servers`
 - https://raw.githubusercontent.com/piwik/referrer-spam-blacklist/master/spammers.txt
 - https://raw.githubusercontent.com/crazy-max/WindowsSpyBlocker/master/data/hosts/spy.txt
 - https://raw.githubusercontent.com/AdAway/adaway.github.io/master/hosts.txt
 - https://www.dshield.org/feeds/suspiciousdomains_Medium.txt
 - https://raw.githubusercontent.com/mitchellkrogza/Badd-Boyz-Hosts/master/hosts
 - http://www.shallalist.de/Downloads/shallalist.tar.gz `only 'adv' & 'tracker' lists`
 - https://dsi.ut-capitole.fr/blacklists/download/publicite.tar.gz `only 'publicite' list`
 - https://ssl.bblck.me/blacklists/hosts-file.txt
 - https://raw.githubusercontent.com/bkrcrc/turk-adlist/master/hosts
 - https://v.firebog.net/hosts/static/w3kbl.txt
 - https://raw.githubusercontent.com/Yhonay/antipopads/master/hosts
 - https://raw.githubusercontent.com/MajkiIT/polish-ads-filter/master/polish-pihole-filters/hostfile.txt
 - https://gitlab.com/ZeroDot1/CoinBlockerLists/raw/master/list_browser.txt
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/StreamingAds/hosts
 - https://raw.githubusercontent.com/azet12/KADhosts/master/KADhosts.txt
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/UncheckyAds/hosts
 - https://raw.githubusercontent.com/tyzbit/hosts/master/data/tyzbit/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Spam/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Risk/hosts
 - https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Dead/hosts
 - http://www.urlvir.com/export-hosts/
 - https://raw.githubusercontent.com/mitchellkrogza/The-Big-List-of-Hacked-Malware-Web-Sites/master/.dev-tools/output/domains/ACTIVE/list
 - https://malc0de.com/bl/BOOT
 - https://raw.githubusercontent.com/hoshsadiq/adblock-nocoin-list/master/hosts.txt
 - https://data.netlab.360.com/feeds/dga/dircrypt.txt
 - https://data.netlab.360.com/feeds/dga/fobber.txt
 - https://data.netlab.360.com/feeds/dga/ccleaner.txt
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
 - a large set of custom entries
  
**Adblock Plus lists** (only full hostname, non-3rd party filters)
 - https://raw.githubusercontent.com/Dawsey21/Lists/master/adblock-list.txt
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
 - https://raw.githubusercontent.com/k2jp/abp-japanese-filters/master/abpjf.txt
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
