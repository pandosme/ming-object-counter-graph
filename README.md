# ming-object-counter-graph

A docker container solution for visualizing object counters in Grafan.  
MING = Mosquitto + InfluxDB + Node-RED + Grafana  



# pre-requisites
1. Linux machine with Docker, Docker-compose and GIT installed
2. One or more Axis cameras
3. Object Counter installed and running the cameras.  Select one of the following
     * AOA Trip-wire counter
     * [Object Counter ACAP](https://acap.juhlin.me/package/ObjectCounter)
	 * [Motion Counter ACAP](https://acap.juhlin.me/package/MotionPath)
4. Camera MQTT client
    * This demo uses [SIMQTT](https://acap.juhlin.me/package/simqtt) but you can use/adjust for the camera MQTT client

# Deployment
View demonstration video on YouTube

1. Connect a terminal to you Linux machine (e.g. Putty)
```
git clone https://github.com/pandosme/ming-object-counter-graph
cd https://github.com/pandosme/ming-object-counter-graph
docker-compose up -d
```
2. Setup the counter in the camera(s)
3. Setup the camera MQTT client to connect to your Linix machin address on port 1860
4. Go to http://server-address:8060 to configure the Node-RED flow that injects data into InfluxDB  
5. Go to http://server-address:3000 to configure the Node-RED flow that injects data into InfluxDB  

