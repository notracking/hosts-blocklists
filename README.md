# No Tracking, ADs or any other online garbage!
This repository provides a host and domainname based blocklist specifically designed for use with dnsmasq (/pi-hole).
Most entries are gathered from multiple, actively maintained sources and automatically updated, cleaned, optimized and moderated on a daily basis.

The optimizer makes full use of dnsmasqs capability to block entire domains such as *.doubleclick.net (domains.txt). This reduces the chance of missing any new subdomains and significantly reduces the size of the blocklists. Hostnames that cannot be blocked on a domain level will still be listed in a regular hostname based blocklist (hostnames.txt).

It is therefore important to use both these blocklists simultaniously to achieve full coverage against the contaminated parts of the internet.

## General policies
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks fake websites
 - Blocks shock sites
 - Blocks malware servers

## Public lists that are used as source
 - http://winhelp2002.mvps.org/hosts.txt
 - http://www.malwaredomainlist.com/hostslist/hosts.txt
 - http://someonewhocares.org/hosts/hosts/
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malvertising.txt
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malware.txt
 - http://hosts-file.net/ad_servers.txt
 - http://hosts-file.net/emd.txt
 - http://hosts-file.net/exp.txt
 - http://hosts-file.net/fsa.txt
 - http://hosts-file.net/mmt.txt
 - http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts
 - https://raw.github.com/StevenBlack/hosts/master/hosts
 - https://raw.githubusercontent.com/Dawsey21/Lists/master/adblock-list.txt
 - https://raw.githubusercontent.com/quidsup/notrack/master/trackers.txt
 - http://malwaredomains.lehigh.edu/files/BOOT
 - http://malwaredomains.lehigh.edu/files/immortal_domains.txt

# How to install
## For a pi-hole setup
 - Uncomment the following two lines in `/etc/pihole/adlist.default`
```
https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt
https://raw.github.com/notracking/hosts-blocklists/master/domains.txt
```
 - Comment out any other list that is already [included](#public-lists-that-are-used-as-source)
 - Update blocklists with `pihole -g`

## For any other dnsmasq setups
 - Download the following two files
```
https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt
https://raw.github.com/notracking/hosts-blocklists/master/domains.txt
```
 - Add the following lines to your dnsmasq.conf
```
conf-file=/path/to/domains.txt
addn-hosts=/path/to/hostnames.txt
```
 - Restart dnsmasq `sudo service dnsmasq restart`
