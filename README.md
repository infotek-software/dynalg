# dynalg
Dynamic Application Level Gateway based on HAProxy loadbalancer

*2017/10/28 this is just research here, currently collecting ideas*
## scope
-assume a group of haproxy LBs in HTTP Mode HT-loadbalanced by a TCP Mode Loadbalancer sitting in front of them. All HAPs listening on frontend port 443. haproxies do ssl offloading for m2m-clients talking websocket protocol to servers running in haproxy backends.

-assume there are three backends: be1,be2,be3

-assume that the request URL contains an id that uniquely identidies the device

*Stakeholders req*: If a device, identidied by its id, connects, HAP should query REST server for backend to select.

## Gathering some infos
- HAP-feature: Initial 'GET /'url-path>' request with WSS 'upgrade' header is available for analysis. 
- +hap-feature: backend selection as a result of request analysis
- +hap-feature: hap buildin analysis can be extended with LUA
- +lua-feature: REST client 

## Approach
it should be possible to write an analysis LUA plugin that reads the backend to be selected from a REST server by sending 'url-path' or parts of it as parameters.

## Prepare PoC
Ubuntu 16.04 LTS, 

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
$ sudo apt-get update && apt-get upgrade
$ sudo apt-get -y install haproxy
````

HAP installation can be found in 
````
/etc/default/haproxy
/etc/haproxy
/etc/init.d
/etc/logrotate.d/haproxy
/run/haproxy
/usr/sbin
/usr/share/lintian/overrides/haproxy
/var/lib/haproxy
````