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

Wall of shame (2018-12-05)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
51.254.47.198|ns3016508.ip-51-254-47.eu|9
145.249.104.196|-|9
171.25.193.20|tor-exit0-readme.dfri.se|9
171.25.193.25|tor-exit5-readme.dfri.se|9
197.231.221.211|exit1.ipredator.se|9
111.40.120.33|-|9
171.25.193.77|tor-exit1-readme.dfri.se|9
45.119.83.195|-|9
188.0.133.241|block.kaztranscom.kz|9
192.160.102.170|ogopogo.relay.coldhak.com|9
205.185.121.241|mail05.chinaregistry.net|9
80.82.67.246|-|9
167.114.235.137|137.ip-167-114-235.eu|8
209.141.33.72|-|8
80.82.77.33|sky.census.shodan.io|8
209.141.53.94|earth.rickparrish.ca|8
158.69.192.239|239.ip-158-69-192.net|8
119.97.170.34|34.170.97.119.broad.wh.hb.dynamic.163data.com.cn|8
199.19.226.226|-|8
13.93.75.219|-|8
31.14.139.27|host27-139-14-31.serverdedicati.aruba.it|8
104.248.23.238|-|8
89.234.157.254|marylou.nos-oignons.net|8
159.203.171.199|-|8
71.6.199.23|ubuntu1619923.aspadmin.com|8
178.73.215.171|178-73-215-171-static.glesys.net|8
58.218.213.156|-|8
65.19.167.131|-|8
5.188.10.76|-|8
35.0.127.52|tor-exit.eecs.umich.edu|8
116.31.116.2|-|8
18.85.22.239|wholesomeserver.media.mit.edu|8
64.113.32.29|tor.t-3.net|8
209.141.50.57|voxility-filtered|8
171.25.193.78|tor-exit4-readme.dfri.se|8
222.87.49.93|-|8
194.61.24.110|-|8
185.220.101.46|-|8
80.82.77.139|dojo.census.shodan.io|8
205.185.120.192|-|8
192.144.202.126|-|8
209.141.62.36|mx26.yongqianggd.com|8
66.70.217.179|tor.cusse.org|8
219.135.194.73|73.194.135.219.broad.gz.gd.dynamic.163data.com.cn|8
180.101.45.68|-|8
35.236.79.13|13.79.236.35.bc.googleusercontent.com|8
185.244.25.152|AWS-Panel|8
199.249.230.73|-|8
106.12.81.245|-|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
221.7.13.54|-|8
206.189.149.126|-|8
