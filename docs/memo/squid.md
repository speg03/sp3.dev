# Squid

## Squid for Windows

WindowsのローカルでSquidを動かす。

refs: [Squid for Windows](http://squid.diladele.com/)

## Access ports limitations

ローカルで動かすだけなので、ポートの制限を外す。

```
# Deny requests to certain unsafe ports
#http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
#http_access deny CONNECT !SSL_ports
```

## Hosts

hostsファイルをサーバーの名前解決に使用する。デフォルトで設定されているはずが有効になっていない模様。

```
# Hosts
hosts_file C:/Windows/System32/drivers/etc/hosts
```

## DNS

Squidからの名前解決に使用するDNSサーバー。

```
# DNS
dns_nameservers 192.168.0.127 192.168.10.127
```

## Parent proxy

```
# Parent proxy with authentication

## この宛先へのリクエストは親プロキシを通さない
acl dst.localnet dst 10.0.0.0/8
acl dst.localnet dst 172.16.0.0/12
acl dst.localnet dst 192.168.0.0/16
acl dst.localdomain dstdomain .example.com
acl dst.localdomain dstdomain .internal

## 親プロキシ（認証つき）
cache_peer proxy.example.com parent 3128 0 name=proxy.parent no-query proxy-only login=username:password
cache_peer_access proxy.parent deny dst.localnet
cache_peer_access proxy.parent deny dst.localdomain

## 上記の宛先のみ直接アクセスを許可して、それ以外は直接アクセスさせない（必ず親プロキシを経由）
always_direct allow dst.localnet
always_direct allow dst.localdomain
never_direct allow all
```

## Logging

`logfile_rotate`の数だけファイルローテーションする。

```
# Logging with readable date
logformat squid %tl %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
logfile_rotate 30
```

以下を実行することでローテーションされる。`-n`はWindowsサービス名。

```
squid.exe -k rotate -n squidsrv
```

## Full configurations

```
#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
#http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
#http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#

# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
#cache_dir ufs /var/cache/squid 100 16 256

# Leave coredumps in the first cache dir
coredump_dir /var/cache/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320

#
# Custom Configurations
#

# Hosts
hosts_file C:/Windows/System32/drivers/etc/hosts

# DNS
dns_nameservers 192.168.0.127 192.168.10.127

# Parent proxy with authentication

## この宛先へのリクエストは親プロキシを通さない
acl dst.localnet dst 10.0.0.0/8
acl dst.localnet dst 172.16.0.0/12
acl dst.localnet dst 192.168.0.0/16
acl dst.localdomain dstdomain .example.com
acl dst.localdomain dstdomain .internal

## 親プロキシ（認証つき）
cache_peer proxy.example.com parent 3128 0 name=proxy.parent no-query proxy-only login=username:password
cache_peer_access proxy.parent deny dst.localnet
cache_peer_access proxy.parent deny dst.localdomain

## 上記の宛先のみ直接アクセスを許可して、それ以外は直接アクセスさせない（必ず親プロキシを経由）
always_direct allow dst.localnet
always_direct allow dst.localdomain
never_direct allow all

# Proxy hostname
visible_hostname proxy.internal

# Logging with readable date
logformat squid %tl %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
logfile_rotate 30
```
