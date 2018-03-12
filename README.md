# Mycroft-AIY

These instruction are adapted from https://github.com/shivasiddharth/custom-voice-hat, but designed getting Google AIY hardware to work with Mycroft (https://mycroft.ai) build on Raspberry Pi 3.

## Following steps to be completed on the RasPi with Picroft image.
1. git clone https://github.com/kevinelgan/mycroft-aiy.git

2. Turn on i2s support in /boot/config.txt with:
    sudo nano /boot/config.txt

    Uncomment the following lines:
    <br>#dtparam=i2s=on
    <br>#dtparam=i2c_arm=on
    <br>#dtparam=spi=on
    <br>#dtparam=audio=on

    Save & Exit
    Reboot

3. Update raspberry pi kernels (if updating from Jessie):
    <br>sudo apt-get update
    <br>sudo apt-get install raspberrypi-kernel

4. Reboot
    <br>sudo reboot

5. Make Audio configuration scripts executable
    <br>cd /home/pi/mycroft-aiy/audio-config/scripts/
    <br>sudo chmod +x ./custom-voice-hat.sh
    <br>sudo chmod +x ./install-i2s.sh

6. Run the Executable Configuration scripts
    <br>sudo ./custom-voice-hat.sh
    <br>Repeat until you receive .bak rename notification
    <br>sudo ./install-i2s.sh

7. Edit /etc/mycroft/mycroft.conf
    <br>replace "play_wav_cmdline": "aplay -Dhw:0,0 %1"
    <br>with    "play_wav_cmdline": "aplay %1",

8. Reboot
    <br>sudo reboot
