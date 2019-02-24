# Nucbox - home media and utility server

##Services:
- Plex: [here](/:32400)
- HTPC Manager: [here](/:8085)

##Initial configuration:
###Plex

If the claim token is not added during initial configuration you will need to use ssh tunneling to gain access and setup the server for first run. During first run you setup the server to make it available and configurable. However, this setup option will only be triggered if you access it over http://localhost:32400/web, it will not be triggered if you access it over http://ip_of_server:32400/web. If you are setting up PMS on a headless server, you can use a SSH tunnel to link http://localhost:32400/web (on your current computer) to http://localhost:32400/web (on the headless server running PMS):

`ssh username@ip_of_server -L 32400:ip_of_server:32400 -N`
