# P2PConnector-Wifi-direct-and-Wifi-based-
## Implementation Resource
https://developer.android.com/guide/topics/connectivity/wifip2p
## Purpose :
This repository contains a package/folder which you can just include in your any project which require p2p communication
## What we can achive? Objective?
Following are the objectives 
  - Can be used to create P2P Games.
  - Can be used to create P2P files sharing app.
  - Can be used to create P2P local message app.
  - Can be used to create a simple socket communication between applications running on diffrent mobile phones.

## Architecture 
![image](https://user-images.githubusercontent.com/66442918/152133894-381df3f3-7c03-4be9-9fc9-68b85b031124.png)

## End-points (How you are going to get the desired methods like sending message to server or recieving and vice versa)
Since this contains following main files.
  - ConnectedDevicesManager
      - It have following methods.
          - getTheListOfAllAvailableDevices(peerListListener) // List < DeviceInfoHolder>
          - getCurrentlyConnectedDevice() // returns WifiP2pDevice device object.
          - getManager() //returns WifiP2pManager.
          - getChannel() //returns WifiP2pManager.Channel
  - ipManager
    - it has following methods.
        - getAllAvailableIps() // returns  List< String >
        - 
  - Server
    - it has following methods.
        - getOutPutStreamManager() // returns object of OutPutStreamManager
            -  By using this we can have access to following methods.
                - WriteFromServerToClient(MessageFromServerToClient messageFromServerToClient) // for writing message from server to clients.
                - WriteFromClientToServer(MessageFromClientToServer messageFromClientToServer) // for writing message form client to server.
        - getInputStreamManager() // returns object of InputStreamManager
            - By using this we can have access to following methdos
        - StartServerAndListenForClients(String ip,int port) // starts listening for clients.
        - 
  - Client

  
## How to import it?
Downalod the repositroy and kee it into your java folder.

![image](https://user-images.githubusercontent.com/66442918/152134408-a36781d5-c026-4c77-958d-f3ada0c6f7e5.png)

## How to use it?
