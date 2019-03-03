
# Nucbox - home media and utility server    
 ## Services: 
- Plex: [here](/plex)    
- HTPC Manager: [here](/htpcm)    
- Couchpotato: [here](/couchpotato)
- QBittorrent: [here](/qbittorrent)  
    
## Initial configuration: 
### Install Docker
`curl -fsSL https://get.docker.com -o get-docker.sh`
`sudo sh get-docker.sh`

### Install Docker Compose

`sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

`sudo chmod +x /usr/local/bin/docker-compose`

### (Optional) Mount a disk
In some setups you may want to mount an external disk to put all the media to. It's just a friendly reminder on how to do it, so that you save some time on googling

Find logical name of the disk you want to mount:

`sudo lshw -C disk`

Find UUID of your disk by logical name:

`sudo blkid`

Create a folder you will mount your disk to:

`sudo mkdir /media/hugedrive` 

Setup auto mount of the disk using fstab file

`sudo nano -Bw /etc/fstab`

fstab line example

`UUID=348A23358A22F2D2   /media/hugedrive        ntfs    defaults        0       2`

Save fstab and then run the following command to apply changes

`mount -a`

If everything went well you will see your disk mounted via this command

`df -h`

### Install Nucbox
`git clone https://github.com/bstrochkov/nucbox.git`

`cd nucbox`

`mv .env-default .env`

### Starting Nucbox

`docker-compose up -d`

### Configure Plex   
If the claim token is not added during initial configuration you will need to use ssh tunneling to gain access and setup the server for first run. During first run you setup the server to make it available and configurable. However, this setup option will only be triggered if you access it over http://localhost:32400/web, it will not be triggered if you access it over http://ip_of_server:32400/web. If you are setting up PMS on a headless server, you can use a SSH tunnel to link http://localhost:32400/web (on your current computer) to http://localhost:32400/web (on the headless server running PMS):    
    
`ssh username@ip_of_server -L 32400:ip_of_server:32400 -N`  
  
### Useful commands  
  
Copy volumes 
`scp -rp user@dest:/path sourcedirectory`
