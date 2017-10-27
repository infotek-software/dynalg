# dynalg
Dynamic Application Level Gateway based on HAProxy loadbalancer

*2017/10/28 this is private research here, currently collecting ideas*
## scope
assuming a group of haproxies all listening on frontend port 443. haproxies do ssl offloading for m2m-clients talking to servers running in haproxy backends.
 
client -443/WSS->haproxy->80xx/WS
````
hap-feature: Initial 'GET /<url-path>' request with WSS 'upgrade' header available for analysis. 
+hap-feature: backend selection as a result of request analysis
+hap-feature: hap buildin analysis can be extended with LUA
+lua-feature: REST client 

=it should be possible to write analysis LUA plugin that reads the backend to be selected from a REST server by sending <url-path> or parts of it as parameters.

````
