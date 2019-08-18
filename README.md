![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2019-08-18)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
166.70.207.2|this.is.a.tor.node.xmission.com|14
171.25.193.77|tor-exit1-readme.dfri.se|14
171.25.193.235|tor-exit3-readme.dfri.se|14
171.25.193.20|tor-exit0-readme.dfri.se|14
171.25.193.25|tor-exit5-readme.dfri.se|14
199.87.154.255|tor.les.net|13
64.113.32.29|tor.t-3.net|13
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|13
89.234.157.254|marylou.nos-oignons.net|12
171.25.193.78|tor-exit4-readme.dfri.se|12
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|12
77.247.181.162|chomsky.torservers.net|12
5.199.130.188|tor.piratenpartei-nrw.de|12
35.0.127.52|tor-exit.eecs.umich.edu|12
185.117.215.9|tor3.digineo.de|11
164.132.51.91|91.ip-164-132-51.eu|11
185.220.101.33|-|11
185.220.101.1|-|11
185.220.101.28|-|11
94.102.51.78|vps1.torrentflame.org|11
185.220.101.26|-|11
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|11
185.220.102.4|-|11
185.220.102.8|-|11
149.202.170.60|-|11
77.247.181.163|lumumba.torservers.net|11
185.220.101.46|-|11
207.244.70.35|-|11
217.115.10.132|tor2.anonymizer.ccc.de|11
77.247.181.165|politkovskaja.torservers.net|11
185.220.101.34|-|11
162.247.74.202|djb.tor-exit.calyxinstitute.org|10
162.247.74.200|kiriakou.tor-exit.calyxinstitute.org|10
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|10
193.169.255.102|-|10
185.220.101.5|-|10
185.220.101.3|-|10
23.129.64.215|-|10
185.220.101.44|-|10
178.20.55.18|marcuse-2.nos-oignons.net|10
185.220.101.65|-|10
192.160.102.170|ogopogo.relay.coldhak.com|10
185.220.101.27|-|10
185.220.101.20|-|10
185.220.101.21|-|10
163.172.160.182|182-160-172-163.rev.cloud.scaleway.com|10
185.220.102.7|-|10
79.134.234.247|sunfire-cape.gate.wayne-enterprises.company|10
18.85.192.253|-|10
162.247.74.27|turing.tor-exit.calyxinstitute.org|10
185.220.102.6|-|10
31.185.104.19|-|10
144.217.255.89|ns542132.ip-144-217-255.net|10
80.67.172.162|algrothendieck.nos-oignons.net|10
216.239.90.19|tor-gateway.vif.com|10
212.21.66.6|tor-exit-4.all.de|10
185.129.62.62|tor01.zencurity.dk|10
46.182.106.190|tor-exit.critical.cat|10
185.220.101.15|-|10
185.220.101.32|-|10
79.137.79.167|tor-exit.talyn.se|10
185.34.33.2|tor.laquadrature.net|10
185.100.87.207|freki.enn.lu|10
80.82.77.139|dojo.census.shodan.io|9
103.249.100.22|-|9
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|9
78.130.128.106|-|9
82.221.131.5|-|9
31.185.104.20|-|9
31.185.104.21|-|9
54.36.189.105|105.ip-54-36-189.eu|9
109.201.133.100||9
198.96.155.3|exit.tor.uwaterloo.ca|9
185.220.101.6|-|9
185.220.101.0|-|9
185.220.101.45|-|9
178.20.55.16|marcuse-1.nos-oignons.net|9
185.220.101.68|-|9
162.213.0.243|-|9
185.104.121.5|tbc.brasshorncomms.uk|9
185.220.100.253|tor-exit-2.zbau.f3netze.de|9
185.220.100.252|tor-exit-1.zbau.f3netze.de|9
217.170.197.83|nortor2.nortor.no|9
185.220.101.29|-|9
185.220.101.22|-|9
92.62.139.103|-|9
37.187.129.166|ns316491.ip-37-187-129.eu|9
104.244.75.97|-|9
195.206.105.217|zrh-exit.privateinternetaccess.com|9
185.100.85.61|tor-exit-node-nibbana.dson.org|9
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|9
198.98.50.112|tor.your-domain.tld|9
176.10.99.200|accessnow.org|9
134.209.155.250|-|9
188.92.75.248|-|9
80.82.70.118|group-ib.com|9
204.8.156.142|cs-tor.bu.edu|9
23.129.64.204|204.emeraldonion.org|9
87.120.36.157|no-rdns.mykone.info|9
115.89.126.224|-|9
134.209.155.245|-|9
95.128.43.164|exit-1.fr.tor.aquaray.com|9
62.102.148.67|-|9
217.61.20.209|host209-20-61-217.static.arubacloud.com|9
46.165.230.5|tor-exit.dhalgren.org|9
192.160.102.166|chaucer.relay.coldhak.com|9
185.220.101.13|-|9
85.248.227.165|-|9
193.110.157.151|tor.nohats.ca|9
162.247.73.192|mario-louis-sylvester-lap.tor-exit.calyxinstitute.org|9
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|9
80.82.77.33|sky.census.shodan.io|8
51.15.53.83|83-53-15-51.rev.cloud.scaleway.com|8
77.120.113.64|64.113.120.77.colo.static.dcvolia.com|8
162.247.74.201|kunstler.tor-exit.calyxinstitute.org|8
144.217.164.104|104.ip-144-217-164.net|8
114.216.152.190|-|8
178.73.215.171|178-73-215-171-static.glesys.net|8
188.214.104.146|api.squired.ro|8
91.250.242.12|-|8
206.189.132.246|-|8
39.82.165.124|-|8
122.195.200.148|-|8
216.218.134.12|-|8
37.220.36.240|-|8
162.247.74.204|billsf.tor-exit.calyxinstitute.org|8
51.77.193.218|218.ip-51-77-193.eu|8
23.129.64.156|156.emeraldonion.org|8
23.129.64.155|155.emeraldonion.org|8
23.129.64.152|152.emeraldonion.org|8
95.142.161.63|ekumen.nos-oignons.net|8
23.129.64.213|-|8
23.129.64.212|-|8
23.129.64.216|-|8
51.15.209.128|tor-exit-1.droideka.ovh|8
167.71.106.66|-|8
68.183.83.89|-|8
23.129.64.205|205.emeraldonion.org|8
185.220.101.67|-|8
185.104.121.6|ministryoftruth.brasshorncomms.uk|8
217.170.197.89|nortor3.nortor.no|8
178.17.170.196|-|8
54.36.108.162|ns3112521.ip-54-36-108.eu|8
185.100.85.190|-|8
185.220.101.25|-|8
183.136.239.74|-|8
158.69.192.200|200.ip-158-69-192.net|8
185.220.101.50|-|8
51.77.52.216|ns3138560.ip-51-77-52.eu|8
192.228.100.247|-|8
178.17.170.135|-|8
94.100.6.27|-|8
217.115.10.131|tor1.anonymizer.ccc.de|8
97.74.237.196|ip-97-74-237-196.ip.secureserver.net|8
167.71.56.222|-|8
62.102.148.69|-|8
185.233.100.23|elenagb.nos-oignons.net|8
23.129.64.191|191.emeraldonion.org|8
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|8
96.86.165.209|96-86-165-209-static.hfc.comcastbusiness.net|8
23.129.64.100|100.emeraldonion.org|8
195.231.69.40|safisego.com|8
23.129.64.162|162.emeraldonion.org|8
23.129.64.166|166.emeraldonion.org|8
167.71.96.195|-|8
87.118.92.43|ns.tor-node.felix.io|8
185.220.101.58|-|8
62.102.148.68|-|8
185.220.101.70|-|8
106.87.40.132|-|8
185.220.101.62|-|8
185.227.68.78|-|8
89.248.167.131|mason.census.shodan.io|8
134.209.155.239|-|8
192.160.102.164|snowfall.relay.coldhak.com|8
192.160.102.168|prawksi.relay.coldhak.com|8
192.160.102.169|manipogo.relay.coldhak.com|8
157.157.87.22|-|8
185.220.101.12|-|8
74.82.47.194|-|8
23.129.64.182|182.emeraldonion.org|8
144.217.165.133|133.ip-144-217-165.net|8
185.104.121.7|bbfc.brasshorncomms.uk|8
89.144.57.83|-|8
205.185.117.149|tor-exit.greektor.net|8
43.251.159.144|-|8
185.220.101.30|-|8
73.226.185.33|c-73-226-185-33.hsd1.nj.comcast.net|8
68.183.83.166|-|8
68.183.83.164|-|8
192.160.102.165|cowcat.relay.coldhak.com|8
202.75.216.136|-|8
192.42.116.14|this-is-a-tor-exit-node-hviv114.hviv.nl|8
23.129.64.193|193.emeraldonion.org|8
139.59.85.148|-|8
46.29.248.238|-|8
