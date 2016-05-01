# Info
This repository provides a host and domainname based blocklist for use with dnsmasq.

Features:
 - Automatic daily updates from public block lists
 - Large set of custom entries
 - Optimized, cleaned and sorted
 - Actively maintained whitelists

Please note that these two lists should be used simultaniously in dnsmasq to get full coverage. The optimizer removes hostnames that are already covered by the domain based blocklist.
Submit a ticket or pull request in case you find any incorrect or missing items.

General policies:
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks fake websites
 - Blocks shock sites
 - Blocks malware servers

# Install
Download the following files:
 - https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt
 - https://raw.github.com/notracking/hosts-blocklists/master/domains.txt

Add the following lines to your dnsmasq.conf:
 - conf-file=/path/to/domains.txt
 - addn-hosts=/path/to/hostnames.txt

Restart dnsmasq:
 - sudo service dnsmasq restart

# Public lists used:
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
