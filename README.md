# docker-ttt
GMOD TTT server image, https://hub.docker.com/r/jusito/

## Changed topics

Docker Run example  
server.cfg  
scripts which are using jusito's git repository - to use mine ! If you want to install it on your own change it or live with my settings  
  

## What I want to add in the future  
DockerCompose file
server start stop action
sec-check if colleciton is working with collID
sec-check if server is up - start errors write into dockerLog cmd  

## run example

--> htbc  
```
docker run -d -p 27015:27015/tcp -p 27015:27015/udp -e WORKSHOP_COLLECTION_ID=123456 -e INSTALL_CSS=true "jusito/docker-ttt" +host_workshop_collection 123456 +map ttt_rooftops_2016_v1 -maxplayers
```  
  
```
docker run -d -p 27015:27015/tcp -p 27015:27015/udp -e WORKSHOP_COLLECTION_ID=<yourCollIdFromSteam> -e INSTALL_CSS=true "jusito/docker-ttt" -usercon +rcon_password "<password>"+host_workshop_collection <yourCollIdFromSteam> +map <mapName> -maxplayers <number>
```  

tcp port for rcon, if you want to use it start with -usercon +rcon_password "yourPW"  

udp port for game traffic  

## access console
docker exec -it CONTAINER ./home/steam/gmodserver console  

## environment variables
If set every workshop item at the collection is added as forced, that means its automatically downloaded on connecting. Don't add collections with maps here just like weapons aso.  
WORKSHOP_COLLECTION_ID=  

This variables are used to write the value to the server.cfg:  
SERVER_NAME=""  
SERVER_PASSWORD=""  
SERVER_VOICE_ENABLE="1"  

If set to "true" the game is installed and mounted, most of the time you want to add the css content.  
INSTALL_CSS=false  
INSTALL_HL2=false  
INSTALL_HLDM=false  
INSTALL_TF2=false  

## server config
http://ttt.badking.net/config-and-commands/convars  
https://wiki.garrysmod.de/server.cfg  
  
Path in container is:
docker cp "your server.cfg path" CONTAINER:/home/steam/serverfiles/garrysmod/cfg/server.cfg

