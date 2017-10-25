# No more ads, tracking and other virtual garbage
This repository provides a host and domainname based blocklist specifically designed for use with dnsmasq.
Most entries are gathered from multiple, actively maintained sources and automatically updated, cleaned, optimized and moderated on a daily basis.

The optimizer makes full use of dnsmasqs capability to block entire domains such as *.doubleclick.net ([domains.txt](https://raw.github.com/notracking/hosts-blocklists/master/domains.txt)). This reduces the chance of missing any new subdomains and significantly reduces the size of the blocklists. Hostnames that cannot be blocked on a domain level will still be listed in a regular hostname based blocklist ([hostnames.txt](https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt)).

It's important to use both these blocklists simultaniously to get full coverage against the contaminated parts of the internet.

## General policies
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks fake websites
 - Blocks malware servers

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
 - Restart dnsmasq `sudo service dnsmasq restart`

## For a pi-hole setup
Unfortunately pi-hole currently does not provide an easy way to use dnsmasqs 'conf-file' feature, making the key feature of this blocklist (blocking domains) useless, see [this post](https://www.reddit.com/r/pihole/comments/4rn1b6/are_wildcards_a_thing/d52spwi) for more info. Using only our hostname list will not give you full coverage.
At this moment it is recommended to set up you own dnsmasq configuration to make full use of our blocklists.

# Sources
**Domain and hostname lists**
 - http://winhelp2002.mvps.org/hosts.txt
 - http://www.malwaredomainlist.com/hostslist/hosts.txt
 - http://someonewhocares.org/hosts/hosts/
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malvertising.txt
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malware.txt
 - http://hosts-file.net/ad_servers.txt
 - http://hosts-file.net/exp.txt
 - http://hosts-file.net/mmt.txt
 - http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts
 - https://raw.github.com/StevenBlack/hosts/master/hosts
 - https://raw.githubusercontent.com/Dawsey21/Lists/master/adblock-list.txt
 - https://raw.githubusercontent.com/quidsup/notrack/master/trackers.txt
 - http://malwaredomains.lehigh.edu/files/BOOT
 - http://malwaredomains.lehigh.edu/files/immortal_domains.txt
 - https://raw.githubusercontent.com/vokins/yhosts/master/hosts.txt `Excluding legit license servers`
 - https://raw.githubusercontent.com/piwik/referrer-spam-blacklist/master/spammers.txt
 - https://raw.githubusercontent.com/crazy-max/WindowsSpyBlocker/master/data/hosts/win7/spy.txt
 - https://raw.githubusercontent.com/crazy-max/WindowsSpyBlocker/master/data/hosts/win81/spy.txt
 - https://raw.githubusercontent.com/crazy-max/WindowsSpyBlocker/master/data/hosts/win10/spy.txt
 - https://raw.githubusercontent.com/AdAway/adaway.github.io/master/hosts.txt
 - http://www.dshield.org/feeds/suspiciousdomains_Medium.txt
 - https://raw.githubusercontent.com/mitchellkrogza/Badd-Boyz-Hosts/master/hosts
 - http://www.shallalist.de/Downloads/shallalist.tar.gz `only 'adv' & 'tracker' lists`
 - http://dsi.ut-capitole.fr/blacklists/download/publicite.tar.gz `only 'publicite' list`
 - https://ssl.bblck.me/blacklists/hosts-file.txt
 - https://raw.githubusercontent.com/bkrcrc/turk-adlist/master/hosts
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

# Lists that will NOT be included
 - http://hosts-file.net/fsa.txt `too many false calls`
 - http://hosts-file.net/emd.txt `too many false calls`
 - http://rlwpx.free.fr/WPFF/hosts.htm `too many false calls, focussed on content blocking`
 - https://github.com/AdguardTeam/AdguardDNS `they parse all domains from adblock filters, causing loads of false calls`
 - http://www.joewein.de/sw/bl-text.htm `very outdated, almost all domains expired`
