# Iota-Eggs
Lay secure IOTA IRI containers on renowned orchestration systems such as Kubernetes, Openshift, Docker Swarm and more, easily, within a few commands.

# Whats so special?
Builds on `IRI` container to be deployable on orchestration systems such as `Kubernetes`, `Openshift` and other orchestration systems with ease, leaveraging environmental variables.

# How to use?

## Building the Iota-Eggs image
- Clone Iota-Eggs repository  `$ git clone https://github.com/ahab94/Iota-Eggs.git`
- Get inside the directory `$ cd Iota-Eggs` 
- Build the image using `$ sudo docker build . -t iota-eggs:latest`  


## Examples of spawning simple containers

```BASH
sudo docker run -e DNS_RESOLUTION_FALSE=yes -e MAX_PEERS=9 -it iota-eggs:latest 
```  

```BASH
sudo docker run -e REMOTE_LIMIT_API="addNeighbors, removeNeighbors" -e MAX_PEERS=9 -it iota-eggs:latest 
```

# Environment variables to Command Line Options mappings


Environment var | Option | Shortened version | Description | Example Input
 --- | --- | --- | --- | --- 
 PORT | `--port` | `-p` | This is a *mandatory* option that defines the port to be used to send API commands to your node | `-p 14800`
 NEIGHBORS | `--neighbors` | `-n` | Neighbors that you are connected with will be added via this option. | `-n "udp://148.148.148.148:14265 udp://[2001:db8:a0b:12f0::1]:14265"`
 CONFIG | `--config` | `-c` | Config INI file that can be used instead of CLI options. See more below | `-c iri.ini`
 UDP_RECEIVER_PORT | `--udp-receiver-port` | `-u` | UDP receiver port | `-u 14800`
 TCP_RECEIVER_PORT | `--tcp-receiver-port` | `-t` | TCP receiver port | `-t 14800`
 TESTNET | `--testnet` | | Makes it possible to run IRI with the IOTA testnet | `--testnet`
 REMOTE | `--remote` | | Remotely access your node and send API commands | `--remote`
 REMOTE_AUTH | `--remote-auth` | | Require authentication password for accessing remotely. Requires a correct `username:hashedpassword` combination | `--remote-auth iotatoken:LL9EZFNCHZCMLJLVUBCKJSWKFEXNYRHHMYS9XQLUZRDEKUUDOCMBMRBWJEMEDDXSDPHIGQULENCRVEYMO`
 REMOTE_LIMIT_API | `--remote-limit-api` | | Exclude certain API calls from being able to be accessed remotely | `--remote-limit-api "attachToTangle, addNeighbors"`
 SEND_LIMIT | `--send-limit`| | Limit the outbound bandwidth consumption. Limit is set to mbit/s | `--send-limit 1.0`
 MAX_PEERS | `--max-peers` | | Limit the number of max accepted peers. Default is set to 0 (mutual tethering) | `--max-peers 8`
 DNS_RESOLUTION_FALSE | `--dns-resolution-false` | | Ignores DNS resolution refreshing  | `--dns-resolution-false`
 
 ---
