## Welcome to (pfSense/OPNsense) + Elastic Stack  

![pfelk dashboard](https://raw.githubusercontent.com/3ilson/pfelk/master/Images/dashboard-v6.0.gif)


This is a fork of https://github.com/3ilson/pfelk to enable support for GeoIP via docker (https://github.com/tkrs/maxmind-geoipupdate) and Elastic via https://github.com/sherifabdlnaby/elastdocker

You can view installation guide guide on [3ilson YouTube Channel](https://www.youtube.com/3ilson).


![Version badge](https://img.shields.io/badge/ELK-7.10.0-blue.svg)
[![Gitter](https://badges.gitter.im/pfelk/community.svg)](https://gitter.im/pfelk/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/a3ilson) 

### Prerequisites
- Ubuntu Server v18.04+ or Debian Server 9+ (stretch and buster are tested)
- pfSense v2.4.4+ or OPNsense 19.7.4+
- The following was tested with Java v11 LTS and Elastic Stack v7.10.0
- Minimum of 4GB of RAM but recommend 32GB

**pfelk** is a highly customizable **open-source** tool for ingesting and visualizing your firewall traffic with the full power of Elasticsearch, Logstash and Kibana.

### Key features:

1. **ingest** and **enrich** your pfSense/OPNsense **firewall traffic** logs by leveraging *Logstash*

2. **search** your indexed data in *near-real-time* with the full power of the *Elasticsearch*

3. **visualize** you network traffic with interactive dashboards, Maps, graphs in *Kibana*

Supported entries include:
 - pfSense/OPNSense setups
 - TCP/UDP/ICMP protocols
 - DHCP message types
 - IPv4/IPv6 mapping
 - pfSense CARP data
 - openVPN log parsing
 - Unbound DNS Resolver with dashboards
 - Suricata IDS with dashboards
 - Snort IDS with dashboards
 - Squid with dashboards
 - HAProxy with dashboard

**pfelk** aims to replace the vanilla pfSense/OPNsense web UI with extended search and visualization features. You can deploy this solution via **ansible-playbook**, **docker-compose**, **bash script**, or manually.

### Contents
* [How pfelk works?](https://github.com/klausagnoletti/pfelk#how-pfelk-works)
* [Installation](https://github.com/klausagnoletti/pfelk#installation)
  * [ansible](https://github.com/klausagnoletti/pfelk#ansible-playbook)
  * [docker](https://github.com/klausagnoletti/pfelk#docker-compose)
  * [manual installation/script](https://github.com/klausagnoletti/pfelk#manual-installationscript---preferred-manual-method)
* [Roadmap](https://github.com/klausagnoletti/pfelk#roadmap)
* [Comparison to similar solutions](https://github.com/klausagnoletti/pfelk#comparison-to-similar-solutions)
* [Contributing](https://github.com/klausagnoletti/pfelk#contributing)
* [License](https://github.com/klausagnoletti/pfelk#license)

### How pfelk works?
![How pfelk works](https://github.com/klausagnoletti/pfelk/raw/master/Images/pfELKOverview.PNG)
### Quick start

(Note: I don't use these so I have't forked. These links points upstream instead)
### Installation
#### ansible-playbook
 * Clone the [ansible-pfelk](https://github.com/3ilson/ansible-pfelk) repository
 * `$ ansible-playbook -i hosts --ask-become deploy-stack.yml`

#### docker-compose
 * Clone the [docker-pfelk](https://github.com/3ilson/docker-pfelk) repository
 * Setup MaxMind
 * `$ docker-compose up`

#### manual installation/script - preferred manual method
* Download installer script from [pfelk](https://raw.githubusercontent.com/klausagnoletti/pfelk/master/pfelk-install-6.0.sh) repository
##### Ubuntu
* `$ sudo wget https://raw.githubusercontent.com/klausagnoletti/pfelk/master/pfelk-install-6.0.sh`
* Make script executable 
* `$ sudo chmod +x pfelk-install-6.0.sh`
* Run installer script 
* `$ sudo ./pfelk-install-6.0.sh`
* Finish Configuring [here](https://github.com/klausagnoletti/pfelk/blob/master/install/configuration.md)
##### Debian
* `$ wget https://raw.githubusercontent.com/klausagnoletti/pfelk/master/pfelk-install-6.0.sh`
* Make script executable 
* `$ chmod +x pfelk-install-6.0.sh`
* Run installer script 
* `$ ./pfelk-install-6.0.sh`
* Finish Configuring [here](https://github.com/klausagnoletti/pfelk/blob/master/install/configuration.md)

#### manual installation
* [Ubuntu 18.04 / 20.04](https://github.com/klausagnoletti/pfelk/blob/master/install/ubuntu.md)
* [Debian 9-10.5](https://github.com/klausagnoletti/pfelk/blob/master/install/debian.md)

### Roadmap
This is the experimental public roadmap for the pfelk project.

[See the roadmap »](https://github.com/orgs/3ilson/projects)

### Comparison to similar solutions
[Comparisions »](https://github.com/3ilson/pfelk/wiki/Comparison)

### Contributing
Please reference to the [CONTRIBUTING file](https://github.com/klausagnoletti/pfelk/blob/master/CONTRIBUTING.md). Collectively we can enhance and improve this product. Issues, feature requests, PRs, and documentation contributions are encouraged and welcomed!

### License
This project is licensed under the terms of the Apache 2.0 open source license. Please refer to [LICENSE](https://github.com/klausagnoletti/pfelk/blob/master/license) for the full terms.
