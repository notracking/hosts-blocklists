# Info
This repository provides a hostname and domainname based blocklist for use with dnsmasq.
Most entries are gathered from various, well known public block lists combined with a large list of manually added, custom entries.

These blocklists are automatically updated, cleaned and verified; false calls are removed by manually whitelisting them.
Domain names that are common within the hostnames file will be added to the domain blocklist for more efficient blocking.
All hostnames that are covered by a domain based filter are removed from the hostnames list, so it's important to use both blocklists simultaniously active at all time.

General policy:
 - Should not break useful websites or apps
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks fake websites
 - Blocks shock sites
 - Blocks known malware hosts

# Install
Download the following files:
 - https://raw.github.com/notracking/hosts-blocklists/master/hostnames.txt
 - https://raw.github.com/notracking/hosts-blocklists/master/domains.txt

Add the following lines to your dnsmasq.conf (and restart afterwards):
 - conf-file=/path/to/domains.txt
 - addn-hosts=/path/to/hostnames.txt

# Public lists used
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
