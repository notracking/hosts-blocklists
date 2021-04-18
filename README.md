# No more ads, tracking and other virtual garbage
The NoTracking blocklist is a DNS based filter list for blocking ads, malware, phising and other online garbage.

## General blocklist policies
 - Should not break useful and commonly used services
 - Blocks tracking servers
 - Blocks advertising servers
 - Blocks analytics servers
 - Blocks scam websites
 - Blocks malware servers
 - Blocks webminers
 - Blocks phishing servers
 
## Optimization
The optimizer makes full use of domainname based wildcard filtering `*.adhost.net`, this reduces the chance of missing any new subdomains and significantly reduces the size of the blocklists.

## Dead hosts removal
All hostnames are constantly monitored for updates. In case the A, AAAA, CNAME and NS records return NXDOMAIN they will be marked as dead and removed. Domains are tested on their whois data and removed if they have been unregistered for a certain time.

The current list of dead hostnames can be found [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/hostnames.dead.txt) and have a look [here](https://github.com/notracking/hosts-blocklists-scripts/blob/master/domains.dead.txt) for all unregistered domains.

## Sources
Most sources come from public hostfile type lists, though several AdblockPlus lists are also included only for their non-3rd party networking filters `||evilhost.com^`. See [SOURCES.md](SOURCES.md) for the full overview of all included lists.

## Versions
| List | Compatibility |
| ------------- | ------------- |
| [dnsmasq/dnsmasq.blacklist.txt](https://github.com/notracking/hosts-blocklists/raw/master/dnsmasq/dnsmasq.blacklist.txt) | Dnsmasq |
| [adblock/adblock.txt](https://github.com/notracking/hosts-blocklists/raw/master/adblock/adblock.txt)| Adguard Home, uBlock Origin |
| [dnscrypt-proxy/dnscrypt-proxy.blacklist.txt](https://github.com/notracking/hosts-blocklists/raw/master/dnscrypt-proxy/dnscrypt-proxy.blacklist.txt)| Dnscrypt-proxy |
| [unbound/unbound.blacklist.conf](https://github.com/notracking/hosts-blocklists/raw/master/unbound/unbound.blacklist.conf)| Unbound |
| [hostnames.txt](https://github.com/notracking/hosts-blocklists/raw/master/hostnames.txt) & [domains.txt](https://github.com/notracking/hosts-blocklists/raw/master/domains.txt)| Dnsmasq (version < 2.80 only, use both files) |

## How to install
 - [Instructions for AdblockPlus](https://github.com/notracking/hosts-blocklists/wiki/Install-AdblockPlus) (eg. [uBlock](https://github.com/gorhill/uBlock), [Adguard Home](https://github.com/AdguardTeam/AdGuardHome/))
 - [Instructions for dnscrypt-proxy](https://github.com/notracking/hosts-blocklists/wiki/Install-dnscrypt-proxy)
 - [Instructions for dnsmasq](https://github.com/notracking/hosts-blocklists/wiki/Install-dnsmasq)
 - [Instructions for dnsmasq (old: pre v2.80)](https://github.com/notracking/hosts-blocklists/wiki/Install-dnsmasq-(old:-pre-v2.80))
 - [Instructions for Pi-hole](https://github.com/notracking/hosts-blocklists/wiki/Install-pi-hole)
 - [Instructions for unbound](https://github.com/notracking/hosts-blocklists/wiki/Install-unbound)

## Supporting Notracking blocklist
If you are intrested in supporting the project you can:
 - Submit false positives
 - [Donate with Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=VPTVYWY3B7XWG&source=url)
 - [Become a Patreon](https://www.patreon.com/notracking)
 - Donate Bitcoin: 1MVHQVRoEvFFmEo4ndJQynMbvAdy3qJbij
