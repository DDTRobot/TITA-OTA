
### To install dependencies:
    sudo git clone https://github.com/DDTRobot/TITA-OTA
    sudo cp -r TITA-OTA/ /usr/
    sudo cp /usr/TITA-OTA/ota_lib/*.so /usr/lib
    sudo cp /usr/TITA-OTA/ota_lib/otafifth_demo /usr/bin
    sudo pip install pycryptodome
    sudo pip install crcmod
    sudo chmod 777 /usr/bin/otafifth_demo
    
### To run control board upgrade:
    otafifth_demo -f $BIN_PATH
    
### To run motor upgrade:
    sudo /usr/TITA-OTA/run.sh -t $MOTOR_TYPE -i $MOTOR_ID -s $CANBUS_ID -b $MOTOR_BIN_PATH


### To auto upgrade all motor and control board:
    cd motor-patch/
    sudo chmod 777 run.sh
    sudo ./run.sh

### To make motor_upgrade_deb.deb:
    chmod 0755 motor_upgrade_deb/DEBIAN/postinst
    chmod 0755 motor_upgrade_deb/DEBIAN/prerm
    fakeroot dpkg-deb -b motor_upgrade_deb

### To install motor_upgrade_deb.deb:
    sudo dpkg -i motor_upgrade_deb.deb
