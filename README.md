# respondd Status for Servers

> A gluon compatible status script for respondd in python.


## Dependencies

 * lsb_release
 * ethtool
 * python3.3
 * python3-netifaces
 * batman-adv


## Setup

### Debian-Dependencies
```
apt-get install python3-netifaces ethtool lsb-release
```

### config.json
Startparameter for ext-respondd.
Copy `config.json.example` to `config.json` and change it to match your server configuration.
(`cp config.json.example config.json`)

 * `batman` (string) (Optional: default bat0)
 * `bridge` (string) (Optional: default br-client)
 * `mesh-wlan` (array of string) (Optional: Ad-Hoc batman-Mesh)
 * `mesh-vpn` (array of string) (Optional: fastd, GRE, L2TP batman-Mesh)
 * `fastd_socket` (string) (Optional: needed for uplink-flag)
 * `rate_limit` (integer) (Optional: limit incoming requests per minutes)
 * `rate_limit_burst` (integer) (Optional: allow burst requests)
 * `nodeinfo` (array) (Optional: overwrite the returned server data)
   The JSON content matches one block of the nodes.json, which is outputted by e.g. the [HopGlass-Server](https://github.com/hopglass/hopglass-server).

### ext-respondd.service
Register ext-respondd as a systemd service

```
cp ext-respondd.service.example /lib/systemd/system/ext-respondd.service
! modify the path inside of the ext-respondd.service !
systemctl enable ext-respondd
systemctl start ext-respondd
```

## Related projects

Collecting data from respondd:
* [yanic](https://github.com/FreifunkBremen/yanic) written in Go
* [HopGlass Server](https://github.com/hopglass/hopglass-server) written in Node.js

Respondd for servers:
* [ffho-respondd](https://github.com/FreifunkHochstift/ffho-respondd) from Freifunk Hochstift (fork of ext-respondd)
* [ffnord-alfred-announce](https://github.com/ffnord/ffnord-alfred-announce) from FreiFunkNord
* [py-respondd](https://github.com/descilla/py-respondd)
