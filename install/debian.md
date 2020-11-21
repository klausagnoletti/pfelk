## Custom Installation Guide (pfSense/OPNsense) + Elastic Stack 

## Table of Contents

- [Preparation](#preparation)
- [Installation](#installation)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)

# Preparation

### 0a. Disabling Swap
Swapping should be disabled for performance and stability.
```
sudo swapoff -a
```

### 0b. Configuration Date/Time Zone
The box running this configuration will reports firewall logs based on its clock.  The command below will set the timezone to Eastern Standard Time (EST).  To view available timezones type `sudo timedatectl list-timezones`
```
sudo timedatectl set-timezone EST
```

### 1. MaxMind container
```
<Insert description of how to set up container>
```

### 2. Install Elastic docker
```
<Insert description of how to set up container>
<config files should be modified>
```

# Configuration

### 3. Configure Kibana
```
sudo nano /etc/kibana/kibana.yml
```

### 4. Modify host file (/etc/kibana/kibana.yml) (Already done via docker-compose)
- server.port: 5601
- server.host: "0.0.0.0"


```

### 3. (Required) Download the following configuration files
Prerequisite: clone repo
```
copy /pfelk/master/etc/logstash/conf.d/01-inputs.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/02-types.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/03-filter.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/05-firewall.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/10-apps.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/30-geoip.conf to ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/50-outputs.conf -to ~/logstash/pipeline/
```

### 15a. (Optional) Download the following configuration files
```
copy /pfelk/master/etc/logstash/conf.d/35-rules-desc.conf ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/36-ports-desc.conf ~/logstash/pipeline/
copy /pfelk/master/etc/logstash/conf.d/45-cleanup.conf ~/logstash/pipeline/
```

### 16. Download the grok pattern
```
sudo wget https://raw.githubusercontent.com/3ilson/pfelk/master/etc/logstash/conf.d/patterns/pfelk.grok -P /etc/logstash/conf.d/patterns/
```

### 17a. (Optional) Download the Database(s)
```
sudo wget https://raw.githubusercontent.com/3ilson/pfelk/master/etc/logstash/conf.d/databases/rule-names.csv -P /etc/logstash/conf.d/databases/
sudo wget https://raw.githubusercontent.com/3ilson/pfelk/master/etc/logstash/conf.d/databases/service-names-port-numbers.csv -P /etc/logstash/conf.d/databases/
```

### 17b. (Optional) Configure Firewall Rule Database
To configure pfSense/OPNsense to update the firewall rule database, follow [this reference](https://github.com/3ilson/pfelk/wiki/References:-Rule-Descriptions).

### 18b. (Optional) Amend 02-types.conf with unique observer.name field (line 8).  
Amend "OPNsense" as desired.  This will be useful if monitoring multiple instances. Reference the [Wiki page](https://github.com/3ilson/pfelk/wiki/References:-Multiple-Instances) for further assistance.
```
      add_field => [ "[observer][name]", "OPNsense" ]
```
### 18ab (Optional) Amend 05-firewall.conf as desired, to map/reference the interface.name, interface.alias and network.name fields. 
Amend `interface.name`, `interface.alias` and `network.name` fields via [Wiki page](https://github.com/3ilson/pfelk/wiki/References:-Customized-Interface-Names)

# Troubleshooting
### 19. Create Logging Directory 
```
sudo mkdir -p /etc/pfELK/logs
```

### 20. Download `error-data.sh`
```
sudo wget https://raw.githubusercontent.com/3ilson/pfelk/master/error-data.sh -P /etc/pfELK/
```

### 21. Make `error-data.sh` Executable
```
sudo chmod +x /etc/pfELK/error-data.sh
```

### 22. Complete Configuration --> [Configuration](configuration.md)
