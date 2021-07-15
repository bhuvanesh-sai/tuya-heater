# tuya-heater

This project is developed using Tuya SDK, which enables you to quickly develop smart devices, branded APP, cloud development project, etc.

For more information, please check Tuya Developer Click and Connect Challenge https://pages.tuya.com/develop/ClickAndConnect_TuyaDeveloper?_source=e9684c7ca6b31e7221c8420f5af94631
 
 <h2>Installations:</h2>
 
 
```python
pip install pytuya  
```

```python
pip install Domoticz 
```

```python
pip install pycryptodome 
```
<br>


<h3>Demo:</h3>

```python
import sys
import pytuya
import socket

if(len(sys.argv)!=5):
 	 print("usage: " + sys.argv[0] + " <IP> <DevID> <Local key> <DPS value>")
	 exit(1)

ip        = sys.argv[1]    # The ip address to which you are connecting the bulb with
devid     = sys.argv[2]	   # The id of the device switch
localkey  = sys.argv[3]    # Local key can be found in tuya api device info
dps_value = sys.argv[4]    # dsp value

device    = pytuya.OutletDevice(devid,ip,localkey)

try:
	payload = device.generate_payload('set', {str(dps_value):True})
	device._send_receive(payload)
	
except (ConnectionResetError, socket.timeout, OSError)  as e:
	print("A problem occur please retry...")
	exit(1)
```

<br>

## Getting access to API
#### Step 1: CLIENT_ID and SECRET_KEY
- Register or Login on <a href="https://auth.tuya.com" target="_blanck">Tuya</a>.
1. Create a cloud development project <a href="https://iot.tuya.com/cloud" target="_blanck">Cloud -> Project</a>.
2. After successful creation, you will receive the **Client ID** and **Secret Key**.

![cloud project](https://user-images.githubusercontent.com/87131635/124926339-0a829180-e01b-11eb-887c-d79b2018f5a4.PNG)

#### Step 2: DEVICE_ID
1. Install **Tuya Smart** app or **Smart Life** app on your mobile phone.
2. Go to <a href="https://iot.tuya.com/cloud/appinfo/cappId/device" target="_blanck">Cloud -> Link Devices</a> page.
3. Selecting a tab **Link Devices by App Account**.
4. Click **Add App Account** and scan the QR code with **Tuya Smart** app or **Smart Life** app.
5. Now you can go to devices <a href="https://iot.tuya.com/cloud/appinfo/cappId/deviceList" target="_blanck">Cloud -> Device List</a> and copy **Device ID**.
    * Notes: Try to select a your region if devices are not displayed.

![client id, key](https://user-images.githubusercontent.com/87131635/124926387-18d0ad80-e01b-11eb-8b23-c41ccf96f799.PNG)

#### Step 3: Request access to API calls
Go to <a href="https://iot.tuya.com/cloud/appinfo/cappId/setting" target="_blanck">Cloud -> API Group</a> and enable **Authorization management**, **Device Management** and **Device Control**.

![cloud api](https://user-images.githubusercontent.com/87131635/124926553-4a497900-e01b-11eb-8a95-aa7ec9ba504e.PNG)


<br>
<h3>Info:</h3>
If you have any problems you can contact me or comment on this.


