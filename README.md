Zigbee2MQTT Convertor for Tuya Light (Lux Sensor)

I recently bought this 'Lux' sensor from AliExpress to connect to my home, and to automate light on&off - based on brightness of daylight outside.
  https://www.aliexpress.com/item/1005004389690629.html?spm=a2g0o.order_detail.order_detail_item.3.745ff19cROU3qS
  ![Screenshot 2023-01-06 at 16 50 37](https://user-images.githubusercontent.com/6130951/211058846-51d8c0f3-1566-4cf4-b27f-ae4860bae39d.png)

  
* Zigbee2MQTT (Frankly, imho, the best ZigBee Coordinator software ever!) - https://www.zigbee2mqtt.io/

Z2M can pair with the device (follow the Z2M pairing guide on how to do this), 
however doesn't recognise the model in it's extensive suite of conversion protocols.

I followed the guide and managed to hack together this convertor file.

Installation:
  1. Download TZE200_khx7nnka.js to your zigbee2mqtt config folder (usually /opt/zigbee2mqtt/data)
  ![Screenshot 2023-01-06 at 16 54 58](https://user-images.githubusercontent.com/6130951/211059650-34c67dd2-9984-49f1-8ea9-3808f856ffdf.png)
  2. Edit Z2M's configuration.yaml to include
  
  external_converters:
    - TZE200_khx7nnka.js
   
  in the options part (be wary of yaml format! use spaces or tabs consistently
    ![Screenshot 2023-01-06 at 16 56 44](https://user-images.githubusercontent.com/6130951/211059942-0dae2210-4869-45b6-aac1-e2e6ea31676a.png)

Restart the Zigbee2Mqtt service ('sudo systemctl restart zigbee2mqtt.service'), and the device should now work!

I use Z2M on a RaspberryPi4 with a Texas Instruments, Inc. CC2531 ZigBee dongle (with antenna, and many, many Aliexpress USB repeaters!)
