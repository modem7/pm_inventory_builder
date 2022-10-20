# pm_inventory_builder
Builds an Ansible inventory from the Proxmox API, grouping VMs by tags

![Docker Pulls](https://img.shields.io/docker/pulls/modem7/pm_inventory_builder) 
![Docker Image Size (tag)](https://img.shields.io/docker/image-size/modem7/pm_inventory_builder/latest) 
[![Build Status](https://drone.modem7.com/api/badges/modem7/pm_inventory_builder/status.svg)](https://drone.modem7.com/modem7/pm_inventory_builder)
[![GitHub latest commit](https://badgen.net/github/last-commit/modem7/pm_inventory_builder)](https://GitHub.com/modem7/pm_inventory_builder/commit/)

---

## Usage

```
$ pm_inventory_builder -help
Usage of pm_inventory_builder:
  -allow-insecure-tls
        Allow insecure TLS communication with Proxmox
  -ansible-user string
        SSH user on which Ansible should attempt to connect
  -apiPassword string
        Proxmox Password. Can also be set (and is recommended as such) via the PROXMOX_API_PASSWORD environment variable
  -apiUser string
        Proxmox User. Can also be set via the PROXMOX_API_USERNAME environment variable
  -tokenId string
        Proxmox Token ID - if this is set, username/password parameters are ignored. Can also be set via the PROXMOX_TOKEN_ID environment variable
  -tokenSecret string
        Proxmox Token Secret. Can also be set (and is recommended as such) via the PROXMOX_TOKEN_SECRET environment variable
  -url string
        Proxmox API URL (default "https://localhost:8006")
```

---

## Docker

### Variables
| Variable | Default |
| :----: | --- |
| PM_IP | 192.168.1.100 |
| PM_PORT | 8006 |
| PM_USER | ubuntu |
| PM_TOKENID | myUser@pve!myToken |
| PM_TOKENSECRET | 44a2085e-f9ae-41c7-a595-d66ece971203 |

### Running
#### Environment Variables
Either:
- Create or copy the [env.list](https://github.com/modem7/pm_inventory_builder/blob/master/env.list) file. Modify as required.
- Run `docker run --rm -v "$(pwd)":/data --env-file env.list modem7/pm_inventory_builder:latest`

Or 

Run the following in your console (modifying the values as required):
```bash
export PM_IP='192.168.1.100'
export PM_PORT='8006'
export PM_USER='ubuntu'
export PM_TOKENID='myUser@pve!myToken'
export PM_TOKENSECRET='44a2085e-f9ae-41c7-a595-d66ece971203'

docker run --rm -v "$(pwd)":/data -e PM_IP -e PM_PORT -e PM_USER -e PM_TOKENID -e PM_TOKENSECRET modem7/pm_inventory_builder:latest
```

Once you have run this, you will have a new file created in your directory called `my_proxmox_inventory.yaml` with your inventory data.
