# Readme
This repository provides hostname and domainname based blocklists for use with dnsmasq.
Most entries are gathered from various, well known public block lists allthough a lot of custom entries have been added manually.

These list are automatically updated.
Common domain names are seperated in the domainname based filter for more efficient blocking and a whitelist is used to prevent false calls from entering the final lists.

General guidelines:
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks fake websites
 - Blocks shock sites
 - Blocks malware hosts

# Install
Download the following files:
 - https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt
 - https://raw.github.com/notracking/hosts-blocklists/master/domains.txt

Update your dnsmasq.conf:
 - Add: conf-file=/path/to/domains.txt
 - Add: addn-hosts=/path/to/hostnames.txt

# Current public sources used:
 - http://winhelp2002.mvps.org/hosts.txt
 - http://www.malwaredomainlist.com/hostslist/hosts.txt
 - http://someonewhocares.org/hosts/hosts/
 - https://s3.amazonaws.com/lists.disconnect.me/simple_malvertising.txt
 - http://hosts-file.net/ad_servers.txt
 - http://hosts-file.net/emd.txt
 - http://hosts-file.net/exp.txt
 - http://hosts-file.net/fsa.txt
 - http://hosts-file.net/mmt.txt
 - http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts
 - https://raw.github.com/StevenBlack/hosts/master/hosts
 - http://malwaredomains.lehigh.edu/files/BOOT
