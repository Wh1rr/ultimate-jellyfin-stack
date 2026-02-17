# The Ultimate Jellyfin Stack!

Welcome to my Jellyfin stack repository! This repository showcases my Docker Compose setup for managing various media-related services using Docker containers. The compose file is meant to be changed to each users liking as I know not everyone has the same requirements. Hope you enjoy!

## Overview

This Plex Stack includes the following services:

- **[Jellyfin](https://github.com/linuxserver/docker-jellyfin):** Media server for streaming movies and TV shows.
- **[Radarr](https://github.com/linuxserver/docker-radarr):** Movie management and automation.
- **[Sonarr](https://github.com/linuxserver/docker-sonarr):** TV show management and automation.
- **[Readarr](https://github.com/linuxserver/docker-readarr):** Used to grab books and audiobooks.
- **[Lidarr](https://github.com/linuxserver/docker-lidarr):** Used to grab music.
- **[Kapowarr](https://github.com/Casvt/Kapowarr):** Used to grab comics.
- **[Prowlarr](https://github.com/linuxserver/docker-prowlarr):** Indexer manager for Radarr and Sonarr.
- **[Seerr](https://github.com/seerr-team/seerr):** Request management and monitoring for Jellyfin.
- **[Gluetun](https://github.com/qdm12/gluetun):** VPN container with WireGuard support for secure browsing.
- **[Qbittorrent](https://github.com/linuxserver/docker-qbittorrent):** BitTorrent client with VPN support.
- **[Tdarr](https://github.com/HaveAGitGat/Tdarr):** Pre-transcodes your media to decrease file sizes
- **[Bazarr](https://github.com/linuxserver/docker-bazarr):** Subtitle management for movies and TV shows.
- **[Autobrr](https://github.com/autobrr/autobrr):** Used to grab torrents immediately as they are released.
- **[Flaresolverr](https://github.com/AlexFozor/FlareSolverr/tree/drission-page):** Used as a proxy server to bypass Cloudflare and DDoS-GUARD protection.
- **[Dozzle](https://github.com/amir20/dozzle):** Used to view the logs of any container.
- **[Wizarr](https://github.com/wizarrrr/wizarr):** Used to create links that can be sent to users so they can be invited to your media server.
- **[Homarr](https://github.com/homarr-labs/homarr):** Used as a dashboard for docker containers with integrations for the *arr, torrent, and Jellyfin apps.
- **[Decluttarr](https://github.com/ManiMatter/decluttarr):** Used to maintain/clean your *arr app queues and downloads.
- **[Jellystat](https://github.com/CyferShepard/Jellystat):** Used to monitor the usage of each user or content on your jellyfin server.
- **[Janitorr](https://github.com/Schaka/janitorr):** Removes untagged media when it reaches a certain age, contains functionality for "Leaving Soon" content too.
- **[Profilarr](https://github.com/Dictionarry-Hub/profilarr):** Used as a quality profile management tool that configures your radarr/sonarr installations
- **[Homarr](https://github.com/homarr-labs/homarr):** A homepage creation service which can connect directly to other services in this stack
- **[Dispatacharr](https://github.com/Dispatcharr/Dispatcharr):** A IPTV tuner with many tools on managing channels, EPGs, logos etc.
- **[Unpackerr](https://github.com/Unpackerr/unpackerr):** A tool which handles all your torrents which come as archive files
- **[Cross seed](https://github.com/cross-seed/cross-seed):** A service which takes your finished torrents and seeds them across your other trackers (check tracker TOS)

![containers](https://github.com/user-attachments/assets/855014b1-2716-4370-975d-a02564df881e)

## Dependencies

1. Linux
2. Docker / Docker Compose
3. OPTIONAL: Komodo - Docker GUI

## Example of Environment variables in Portainer
Keep in mind some variable names have changed since this screenshot was taken
![jellyfin-stack](https://github.com/user-attachments/assets/1b984a6f-df7f-46c9-9dd1-54c62b6854a6)

  
File location examples:
- {MEDIA_SHARE} = ~/Jellyfin/share
- {BASE_PATH} = ~/Jellyfin/home

To allow hardlinking to work (which you will definitely want!) you will have to use the same root folder in all of your container path. In this example we use "/share", so in the container it will look like "/share/downloads/tv"

An example folder structure:  
![image](https://github.com/DonMcD/ultimate-plex-stack/assets/90471623/2003ac26-a929-4ff6-ad67-e35fc51fb51a)
  
- Feel free to expand your folders to also include "books" or "music" as you need for your setup

## Networking
If you do want to create your networks externally, update the networks configuration with the following:
Thanks @aquickalias :)

```
networks:
  proxy:
  jellyfin_default:
  starr:
  jellystat:
  gluetun_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.100.0.0/16
```
  
## Starr apps
Setting up the starr apps might be a bit confusing the first time, but to keep it simple:
1. Prowlarr manages the indexes for *some* starr apps (radarr and sonarr)
2. The following starr apps make use of the download client (qBittorent) to download their respective content type:
   1. Radarr - Movies
   2. Sonarr - TV Shows
   3. Lidarr - Music
   4. Readarr - Books
   5. Kapowarr - Comics
3. Jellyseer is a platform which combines the request system in radarr and sonarr to make a nice UI/UX to find and auto download the content.
  
Anytime you reference your media folder in a container you want the path to look like /share/media/tv instead of /tv like a lot of the default guides say, if you do end up mapping the path as /tv hardlinking will not work

## Recommendations

1. Get familiar with reverse proxies
2. Install komodo to manage and monitor containers
3. Use Cloudflare tunnels

## Support + Additions

If you need help or just want something added, please feel free to create an [issue](https://github.com/Wh1rr/ultimate-jellyfin-stack/issues).
If you want to get a head start and get your changes in ASAP, feel free to open a [PR](https://github.com/Wh1rr/ultimate-jellyfin-stack/pulls). Which I'll review when possible.
