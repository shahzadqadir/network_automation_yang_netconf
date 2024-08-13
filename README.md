## Model Based Network Automation using Yang Models, and Netconf

#### Netconf support platforms

- Cisco IOS XE (CSRv, ISR, ASR)
- Cisco IOS XR (ASR 9K)
- Cisco NX OS

#### Enable Netconf on Cisco IOS XE Routers

1. Configure SSH
```
hostname R1
ip domain name test.com
crypto key generate rsa
2048
```
2. Configure Local Username/Password
```
username admin priv 15 secret admin
```
3. Enable AAA and Default to Local, If you have TACACS - you can use that too!
```
aaa new-model
aaa authentication default login local
aaa authorization exec default login local
```
4. Enable netconf-yang
```
(config)# netconf-yang
```
5. Check if netconf is running
```
CSR1#show platform software yang-management process
confd            : Running 
nesd             : Running 
syncfd           : Running 
ncsshd           : Running 
dmiauthd         : Running 
nginx            : Running 
ndbmand          : Running 
pubd             : Running 
```
6. Try to do a SSH connection on Port 830 (default netconf port), it should bring back set of capabilities like below
```
ssh -p 830 admin@10.10.100.1
admin@10.10.100.1's password: 
chmod: cannot access '/tmp/tmppub/tracekey_cache//tmp/sw/rp/0/0/rp_daemons/mount/usr/binos/bin/netconf-subsys': No such file or directory
<?xml version="1.0" encoding="UTF-8"?>
<hello xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
<capabilities>
<capability>urn:ietf:params:netconf:base:1.0</capability>
<capability>urn:ietf:params:netconf:base:1.1</capability>
<capability>urn:ietf:params:netconf:capability:writable-running:1.0</capability>
<capability>urn:ietf:params:netconf:capability:xpath:1.0</capability>
<capability>urn:ietf:params:netconf:capability:validate:1.0</capability>
<capability>urn:ietf:params:netconf:capability:validate:1.1</capability>
<capability>urn:ietf:params:netconf:capability:rollback-on-error:1.0</capability>
<capability>urn:ietf:params:netconf:capability:notification:1.0</capability>
.... (output omitted)
```



