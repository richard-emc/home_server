<div align="center">
  <img src="./images/OMV_Image.png" alt="OMV Screenshot" width="144">
  <p>
    <strong>### My openmediavault home server :computer:</strong>
  </p>
</div>


Self hosted server running on a X86 system. The server runs Debian12/OMV and several other applications deployed using docker

## :computer:&nbsp; Infrastructure

[debian12](https://www.openmediavault.org/) Installed on raid1

[openmediavault](https://www.openmediavault.org/) installed on top of debian12

| Component    | Details |
|--------|---------------------------------------------|
| CPU    | Intel Core i5-4460                          |
| Cooler | Original                                    |
| RAM    | 8GB DDR3                                    |
| GPU    | Integrated                                  |
| PSU    | Pico PSU 160W                               |
| DISK1  | SSD 120GB(OS)                               |
| DISK2  | SSD 120GB(OS)                               |
| DISK3  | HDD 4TB(Data)                               |
| DISK4  | HDD 4TB(Data)                               |


## :straight_ruler:&nbsp; Directory Structure


+----------------------------------------------------------------
|                        Home Server                             |
|----------------------------------------------------------------|
|  Storage Layer                                                 |
|   ├── RAID1 (SSDs)    → Debian OS, OMV OS, system logs         |
|   └── Btrfs Mirror (HDDs) → Media, backups, photos, configs    |
|----------------------------------------------------------------|
|  Docker Compose Orchestration                                  |
|   ├── Docker          → Dockge                                 |
|   ├── Media Server    → Jellyfin, Sonarr, Radarr, Bazarr       |
|   ├── Photos Stack    → Immich                                 |
|   ├── Monitor         → beszel                                 |
|   ├── Home Assistant  → Home Assistant, mosquitto, zigbee2mqtt |
|   └── Utilities       → mealie, code Server                    |
+----------------------------------------------------------------+

/dev/md0   RAID1   →  /boot  
/dev/sdc   BTRFS   →  /Compose  
/dev/sdc   BTRFS   →  /Media  
/dev/sdc   BTRFS   →  /Backup  

home_server/
├── compose/                   # Individual Docker Compose files per stack  
│   ├── media_server.yml       # Jellyfin, Sonarr, Radarr, etc.  
│   ├── home_assistant.yml     # Home automation  
│   ├── photos.yml             # Immich (photo manager)  
│   └── utils.yml              # Utility services (nginx, backups, etc.)  
│
├── config/                    # Persistent configuration for each container  
│   ├── jellyfin/  
│   ├── sonarr/  
│   ├── radarr/  
│   ├── immich/  
│   └── home_assistant/  
│
├── data/                      # Local storage volumes  
│   ├── media/                 # Movies, series, music, photos  
│   └── backups/               # Automatic system and config backups  
│
├── scripts/                   # Helper scripts (setup, backup, monitoring)  
│
├── .env                       # Environment variables (ports, paths, secrets)  
└── README.md  


Each service is available on its own ports
| Service      | Port  |
| ------------ | ----- |
| transmission | 5656  |
| nzbget       | 6789  |
| filebot      | 7676  |
| sonarr       | 8989  |
| radarr       | 7878  |
| bazarr       | 6767  |
| jackett      | 9117  |
| plex         | 32400 |
| portainer    | 9000  |
| heimdall     | 8888  |
| netdata      | 19999 |
