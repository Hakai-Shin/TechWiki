# Securing SSH in server

firewalld enables SSH in the default (public) zone by default. First needs to be removed from the default zone:
```
firewall-cmd --permanent --remove-service=ssh
```
Create the new zone:
```
firewall-cmd --permanent --new-zone=<zone_name>
```
Add the SSH service and the network to the zone.
```
firewall-cmd --permanent --zone=onnetnetwork --add-source=<ip_address>
firewall-cmd --permanent --zone=onnetnetwork --add-service=ssh
```
Then, reload the firewall to make the new configuration active.
```
firewall-cmd --reload
```
Confirm by checking actives zones
```
firewall-cmd --get-active-zones
```
