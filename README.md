# Radarr-AirDCPP-docker
Docker builds for Radarr-AirDCPP

Example docker-compose config (replace Dockerfile with Dockerfile.<architecture>):

```
version: '3'
services:
  rdr_custom:
    build:
      context: .
      dockerfile: Dockerfile
    image: result/latest
    volumes:
      - <host_config_dir>:/config
      - /mnt:/mnt
```
