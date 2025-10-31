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

## :straight_ruler:&nbsp; Random Tips and Tricks

harddrive
└── docker_homepage
    ├── homepage
    │   └── config
└── docker_ms
    ├── prowlarr
    │   └── config
    ├── jellyfin
    │   └── config
    ├── jellyseerr
    │   └── config
    ├── radarr
    │   └── config
    ├── sonarr
    │   └── config
    ├── qbitttorrent
    │   └── config
    ├── jdownloader-2
    │   └── config
└── docker_recepies
    ├── mealie
    │   └── config
└── docker_HA
    ├── homeassistant
    │   └── config
    ├── mosquitto
    │   └── config
    ├── zigbee2mqtt
    │   └── config    
└── Media
    └── downloads
    └── Movies
    └── TVseries    
    └── music    
    └── musicvideo

Each service is available on its own ports:

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
