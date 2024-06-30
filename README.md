# Conplete media server setup: plex and arr stack

## First create .env file containing the following environment variables
```
# Your timezone, https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
TZ=America/Sao_Paulo # set to your timezone https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
# UNIX PUID and PGID, find with: id $USER
PUID=1000 # set to your user id
PGID=1000 # set to your group id
# The directory where configuration will be stored.
ROOT=/home/${whoami}/media-center-config
HDDSTORAGE='/media/MediaCenter/'
PLEX_CLAIM= # set your plex claim id https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/
PLEX_ADVERTISE_URL= # set to the url and port of your plex server

# Wireguard Settings
#Your public ip, auto for auto detect
SERVERURL=auto
#number of devices to generate configuration to connect to the wireguard vpn
PEERS=7
```

## Configure the permissions for the two mount points
```
sudo chown -R $USER:$USER /path/to/ROOT/directory
sudo chown -R $USER:$USER /path/to/HDDSTORAGE/directory
```

## If you are running plex on an raspberry pi
### First you need to clone the plex git repository below
```
git clone https://github.com/plexinc/pms-docker.git
```

### Then run the command below to use the gith docker container image for raspberry pi
```
docker build -t plexinc/pms-docker:latest . -f Dockerfile.armv7
```

## Start the containers
```
docker-compose up -d --remove-orphans
```
