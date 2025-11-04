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

```bash
dev/sdc  
├── Compose/                   #  
│   └── dockge/                # dockge Docker Management  
│       └── data/              #  
│       └── compose.yml        #   
│   └── home_assistant         # Home automation  
│       └── homeassistant/     #   
│           └── config/        #   
│       └── mqttt/             # Mosquitto Broker  
│           └── config/        #   
│       └── zigbee2mqttt/      #   
│           └── config/        #   
│       └── compose.yml        #  
│   └── Immich                 # Immich Photo manager  
│       └── postgress/         # Databe for Immich  
│           └── config/        #    
│       └── compose.yml        #  
│   └── internet_monitor       # Monitor internet and home system  
│       └── beszel_data_agent/ #  
│           └── config/        #   
│       └── beszel_data/       #   
│           └── config/        #   
│       └── beszel_socket/     #   
│           └── config/        #   
│       └── compose.yml        #  
│   └── media_server           # Monitor internet and home system  
│       └── jellyfin/          # Media Player   
│           └── config/        #   
│       └── jellyseer/         # Media Request  
│           └── config/        #   
│       └── prowlar/           # Torrent Indexer Anget  
│           └── config/        #  
│       └── qbittorrent/       # Torrent Download Agent  
│           └── config/        #  
│       └── radarr/            # Manage Movies  
│           └── config/        #   
│       └── sonarr/            # Manage TV Series  
│           └── config/        #   
│       └── compose.yml        #  
│   └── utilities              # dockers that are out of scope  
│       └── code-server/       # Open Vs Code server  
│           └── config/        #  
│       └── mealie/            # Manage Recepies  
│           └── config/        #   
│       └── compose.yml        #  
│  
│  
├── Media/                     # Media Folder   
│   └── HDs/                   # Copy of home External HDs  
│   └── immich/                # Media Folder for Immich  
│   └── media_server/          # Media Folder  
│       └── dowloads/          # qbittorrent download folder  
│       └── filmes/            # movies folder for Jellyfin  
│       └── series/            # TV Series folder for Jellyfin  
│  
├── Backup/                    # Local storage volumes    
│   ├── media/                 # Movies, series, music, photos    
│   └── backups/               # Automatic system and config backups   
│  
├── scripts/                   # Helper scripts (setup, backup, monitoring)   
│  
├── .env                       # Environment variables (ports, paths, secrets)    
└── README.md   
```

Each service is available on its own ports
| Service       | Port  |
| ------------  | ----- |
| Home assistant| 8123  |
| zigbee2mqtt   | 8080  |
| immich server | 2283  |
| beszel        | 8090  |
| sonarr        | 8989  |
| radarr        | 7878  |
| radarr        | 9696  |
| jellyfin      | 8096  |
| jellyseerr    | 5055  |
| qbittorrent   | 8081  |
| mealie        | 9925  |
| code-server   | 8443  |

