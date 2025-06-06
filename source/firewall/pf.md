# PF

Packet Filter is used in the FreeBSD setup script.

## Basic Rules
```
set skip on lo0
scrub in all

antispoof for lo0
table <fail2ban> persist

pass out quick all
pass quick on lo0 all

block in all
block in quick from <fail2ban>
pass in quick inet proto icmp all
pass in quick inet6 proto icmp6 all

pass in quick inet proto tcp from any to any port 22 keep state
pass in quick inet proto tcp from any to any port 80 keep state
pass in quick inet proto tcp from any to any port 443 keep state
pass in quick inet proto tcp from any to any port 5060 keep state
pass in quick inet proto udp from any to any port 5060 keep state
pass in quick inet proto tcp from any to any port 5080 keep state
pass in quick inet proto udp from any to any port 5080 keep state
pass in quick inet proto udp from any to any port 16384:32768 keep state
```

## Disable
```
pfctl -d
```

## Enable
```
pfctl -e
```

## Show Rules
```
pfctl -s rules
```
