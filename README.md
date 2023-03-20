# ming-object-counter-graph


# pre-requisites
- One or more Axis cameras
- Linux host with Docker, Docker-compose and GIT installed

# Customization

## docker-compose.yaml
You may want to edit the following in docker-compose.yaml for production systems

```
  nodered:
    environment:
      - TZ=Europe/Stockholm
    ports:
      - '8060:1880'
  mqtt:
    ports:
      - '1860:1883'
  mongodb:
  influxdb:
# Remove # to expose influx db outisde  
#    ports:
#      - '8660:8086'  
```

## settings.js
You may want to edit settings.js to customize the Node-RED settings.
- httpAdminRoot: '/admin',   (Default flows view url http://address:8060/admin)
- ui: { path: "/" },         (Default dashboard url http://address:8060/)
- adminAuth:                 (Default disabled.  It is recommended that you enable admin credentials.  See [Securing Node-RED](https://nodered.org/docs/user-guide/runtime/securing-node-red#editor--admin-api-security))
- httpNodeAuth:              (Default disabled.  It is recommeded to enable credentials to dashboard view. See [Securing Dasboard](https://nodered.org/docs/user-guide/runtime/securing-node-red#http-node-security))
- credentialSecret           (Set your own key to encrypt sensative data on host)

# Deployment
```
git clone https://github.com/pandosme/axis-ming.git
cd axis-ming
git checkout path
npm install (see below)
docker-compose up -d
```
If node and npm is not installed you can install them from the container
```
sudo docker exec -it axis-ming-path bash
cd /data
npm install
exit
sudo docker-compose down
sudo docker-compose up -d
```

Node-RED needs to have the cameras credentials in order to tack background reference images.  Use a browser and go to http://address:8050/admin.  In the tab "Cameras", double-click one of the orange camera nodes.  Click the pen icon and set the cameas user and password.  Leave address empty.

Install [Path](https://api.aintegration.team/acap/path?source=axis-ming) in all your cameras.  Configure MQTT to go to the server IP address you installed the tool on.  No user/password required.

Go to http://server-address:8050
