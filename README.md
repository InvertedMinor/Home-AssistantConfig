# Home-AssistantConfig

<b>Builiding Blocks</b>

<table style="width:500px">
    <col width="50px" />
    <col width="50px" />
    <col width="200px" />
    <col width="200px" />
  <tr>
    <th>Device</th>
    <th>Purpose</th>
    <th>Hardware</th>
    <th>Software</th>
  </tr>
  <tr>
    <td>RPI-4</td>
    <td>Hassio Engine</td>
    <td>Raspberry Pi 4, M.2 SATA SSD expansion board, 128 GB SSD</td>
    <td>See Hassio</td>
  </tr>
  <tr>
    <td>Z-Wave</td>
    <td>Input-Output</td>
    <td>Z-Stick Gen5 https://bit.ly/30cAuwc</td>
    <td>See Hassio</td>
  </tr>
  <tr>
    <td>WiFi</td>
    <td>Input-Output</td>
    <td>Unify https://bit.ly/37X7OtD</td>
    <td>See Hassio</td>
  </tr>
  <tr>
    <td>RF</td>
    <td>Input-Output</td>
    <td>RFLink https://bit.ly/30o9IRP</td>
    <td>See Hassio</td>
  </tr>
  <tr>
    <td>Zigbee</td>
    <td>Input-Output</td>
    <td>Zigbee2MQTT https://bit.ly/3806hmS</td>
    <td>See Hassio</td>
  </tr>  
  <tr>
    <td>DSMR</td>
    <td>Energy & Water monitor</td>
    <td>P1 Smart Meter Monitor https://www.ztatz.nl</td>
    <td>See Hassio</td>
  </tr>  
  <tr>
    <td>Roller & Venetian blinds #1</td>
    <td>Open & Close at sunset/sunrise</td>
    <td>DIY: Standard rollerbinds fitted with 12V DC motor, Wemos D1 mini, L298N.</td>
    <td>WiFi: ESPHome, Bases: https://bit.ly/36NWvnp</td>
  </tr>
  <tr>
    <td>Venetian blinds #2</td>
    <td>Open & Close at sunset/sunrise</td>
    <td>Geiger motor: https://bit.ly/2RcREpt, FIBARO FGRM222 Roller Shutter Controller: https://bit.ly/2QMmNkp</td>
    <td>Z-Wave: See Hassio Automation</td>
  </tr>
  <tr>
    <td>Sun Screens</td>
    <td>Manual, Close at high windspeed</td>
    <td>Somfy</td>
    <td>RF: RFlink integration: https://bit.ly/3832FQL</td>
  </tr>  
  <tr>
    <td>Switches #1</td>
    <td>On & Off at sunset/sunrise</td>
    <td>Sonoff basic</td>
    <td>Wifi: Tasmota: https://bit.ly/2FFV4eP, https://bit.ly/38337hV</td>
  </tr>
  <tr>
    <td>Switches #2</td>
    <td>On & Off at sunset/sunrise</td>
    <td>Neo Coolcam Power Plug https://bit.ly/2t9QXVT</td>
    <td>Z-Wave See Hassio Automation</td>
  </tr>  
  <tr>
    <td>Switches #3</td>
    <td>On & Off at sunset/sunrise</td>
    <td>DIY PVTO: http://ptvo.info </td>
    <td>Zigbee: See Hassio Automation</td>
  </tr>
  <tr>
    <td>Switches #4</td>
    <td>On & Off at sunset/sunrise</td>
    <td>Ikea Tradfri Remote </td>
    <td>Zigbee: See Hassio Automation</td>
  </tr>  
  <tr>
    <td>Lights #1</td>
    <td>On & Off at sunset/sunrise</td>
    <td>FIBARO FGS213 & FGS223 https://bit.ly/3a2D4tf</td>
    <td>Z-Wave: See Hassio Automation</td>
  </tr>
  <tr>
    <td>Lights #2</td>
    <td>On & Off at sunset/sunrise</td>
    <td>Ikea Tradfri Led</td>
    <td>Zigbee: See Hassio Automation</td>
  </tr>
  <tr>
    <td>Temperatures</td>
    <td>Measure</td>
    <td>Baldr https://bit.ly/39YSQFn</td>
    <td>RF: See Hassio Automation</td>
  </tr> 
  <tr>
    <td>Motion</td>
    <td>Measure</td>
    <td>YobangSecurity EV152 PIR  </td>
    <td>RF: See Hassio Automation</td>
  </tr>
  <tr>
    <td>Landroid</td>
    <td>Cutting Grass</td>
    <td>WG794</td>
    <td>https://github.com/virtualzone/landroid-bridge</td>
  </tr>   
</table>

<b>Hassio install Raspberry Pi 4 SSD</b>

Follow this great guide: https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/

<pre><code>
sudo apt-get install apparmor-utils apt-transport-https avahi-daemon ca-certificates curl dbus jq network-manager socat software-properties-common <br>
curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh" >> hassio_install.sh
sudo bash hassio_install.sh -m raspberrypi4<br>
</code></pre>

If you have tries other ways and no longer have a clean RPI, make sure to remove all Hassio stuff first. I did the following to clean my own mesh:
<pre><code>
sudo systemctl stop hassio-supervisor.service<br>
sudo systemctl disable hassio-supervisor.service<br>
sudo systemctl disable hassio-apparmor.service<br>
sudo systemctl daemon-reload<br>
</code></pre>
<pre><code>
sudo su<br>
cd /etc/systemd/system<br>
rm hassio-*<br>
</code></pre>
<pre><code>
docker stop $(docker ps -q)<br>
docker rm $(docker ps -qa)<br>
docker rmi -f $(docker images -q)<br>
docker system prune<br>
</code></pre>

Had to a few “rinse, repeats” of the three commands above until “docker stop $(docker ps -q)” came up blank.
<code>
sudo rm -rf /usr/share/hassio/
</code>

<code>
sudo rm /etc/systemd/system/home-assistant@YOUR_USER.service
</code>
Now you shoud be able to start installing Hassio as described above




