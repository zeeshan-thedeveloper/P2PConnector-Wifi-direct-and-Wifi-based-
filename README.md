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
 
## How to import it?
Downalod the repositroy and kee it into your java folder.

![image](https://user-images.githubusercontent.com/66442918/152134408-a36781d5-c026-4c77-958d-f3ada0c6f7e5.png)


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
  - Server
    - it has following methods.
        - getOutPutStreamManager() // returns object of OutPutStreamManager
            -  By using this we can have access to following methods.
                - WriteFromServerToClient(MessageFromServerToClient messageFromServerToClient) // for writing message from server to clients.
        - getInputStreamManager() // returns object of InputStreamManager
            - By using this we can have access to following methdods
                - getResponseReceivedAtServer() // return response in string. this is response which a server get from client.
        - StartServerAndListenForClients(String ip,int port) // starts listening for clients.
        - 
  - Client
    - it has following methods.
        - connectToTheServer(String ip, int port) // for connecting the server.
        - getOutPutStreamManager() // returns object of OutPutStreamManager
            -  By using this we can have access to following methods.
                - WriteFromClientToServer(MessageFromClientToServer messageFromClientToServer) // for writing message form client to server.
        - getInputStreamManager() // returns object of InputStreamManager
            - By using this we can have access to following methdods
                - getResponseReceivedAtClient() // returns response in string. this is the response which a client get from server.
       
  
  

## How to use it?

### If we want to start a server and wait for clients to join then 
         MainActivity.server.StartServerAndListenForClients(IP_STRING,PORT_NUMBER);
### If we want to join a server from client side then
         MainActivity.client.connectToTheServer(IP_STRING, PORT_NUMBER);
### If you want to write from server to client then
         MainActivity.server.getOutPutStreamManager().WriteFromServerToClient(new MessageFromServerToClient(ANY_JSON_FORMATED_STRING));
         Note: not necessarly you need to pass a json but only string can be passes aswell.
### If you want to write from cleint to server then
         MainActivity.client.getOutPutStreamManager().WriteFromClientToServer(new MessageFromClientToServer(ANY_JSON_FORMATED_STRING));
         Note: not necessarly you need to pass a json but only string can be passes aswell. 
### If you want to get the response sent by server in client area then 
         String response = MainActivity.client.getInputStreamManager().getResponseReceivedAtClient();
         Note : run this code in a thread.
### If you want to get the response sent by client in server area then 
        String response  =  MainActivity.server.getInputStreamManager().getResponseReceivedAtServer()
        Note : run this code in a thread.

### Some usefull code snippets.
       - Getting list of devices.
       WifiP2pManager.PeerListListener peerListListener = new WifiP2pManager.PeerListListener() {
            @Override
            public void onPeersAvailable(WifiP2pDeviceList wifiP2pDeviceList) {
                    listOfDevices.clear();
                    for (WifiP2pDevice device : wifiP2pDeviceList.getDeviceList()){
                        listOfDevices.add(new DeviceInfoHolder(device));
                    }
                    //Set to list view
                    Toast.makeText(mainActivity, "Number of devices available :"+listOfDevices.size(), Toast.LENGTH_SHORT).show();
                    customAdapter_forListOfDevices = new CustomAdapter_ForListOfDevices(mainActivity,R.layout.device_list_item,listOfDevices);
                    list_view_of_devices.setAdapter(customAdapter_forListOfDevices);
            }
        };
        mainActivity.connectedDevicesManager.getTheListOfAllAvailableDevices(peerListListener);
      - 



