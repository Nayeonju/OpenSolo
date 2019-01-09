# Open Solo Firmware Files #

There are numerous firmware files and packages for the different components of the Solo.

## IMX Firmware ##

The full IMX companion computer packages can be found in the the [/Firmware/OpenSolo](/Firmware/OpenSolo) directory.  These are large 75MB packages that contain a complete file system.  These files are produced by [solo-builder](/solo-builder).  There is a package for the copter and a pacakge for the controller.  These packages also contain all the other firmware, such as ArduCopter and the controller's STM32.

These packages can be installed directly using SSH and SCP. Connect your PC to the Solo's WiFi. If you never changed the Solo's wifi password, the default is sololink.  You will want to do the copter first, since you will lose connectivity when the controller update initiates.

#### Copter IMX ####

  1. SSH into the **copter** with IP 10.1.1.10, username root, password TjSDBkAu.
  2. `$ sololink_config --update-prepare sololink` cleans up and prepares the directories.
  3. Copy `3dr-solo.tar.gz` and `3dr-solo.tar.gz.md5` to the `/log/updates` directory on the copter.
  4. `$ sololink_config --update-apply sololink --reset` executes the update and reboots.

#### Controller IMX ###

  1. SSH into the **controller** with IP 10.1.1.1, username root, password TjSDBkAu
  2. `$ sololink_config --update-prepare sololink` cleans up and prepares the directories.
  3. Copy `3dr-controller.tar.gz` and `3dr-controller.tar.gz.md5` to the `/log/updates` directory on the controller.
  4. `$ sololink_config --update-apply sololink --reset` executes the update and reboots.


## Artoo STM32 Firmware ##

The controller's STM32 hardware controls the sticks, buttons, display, battery, haptic, and lights.  It is a separate piece of hardware in the controller from the IMX, which has its own firmware.  This firmware is included in the IMX Firmware package.  So you would only be using this separate firmware loading process if you're making changes specific to it.  More detail is available in the [artoo directory](/artoo).  Compiled firmware is available here in the the [/Firmware/Artoo STM32](/Firmware/Artoo%20STM32) directory.

The default filename is `artoo.bin`.  You can rename it, as long as it begins with `artoo_`.  For example, you can name the file `artoo_1234xyz.bin`.

This firmware can be installed directly using SCP or and SFTP application. Connect your PC to the Solo's WiFi. If you never changed the Solo's wifi password, the default is sololink.

  1. Connect via SCP or an SFTP application to the **controller** with IP 10.1.1.10, username root, password TjSDBkAu
  2. Copy `artoo.bin` to the `/firmware` directory on the controller.
  3. Reboot the controller.  When powering up, the display will go out and come back on during the update.


## ArduCopter Firmware ##

The Cube autopilot on the copter runs ArduPilot's ArduCopter firmware. This firmware file is again also included in the IMX packages, but different versions can be loaded separately. Compiled versions of ArduCopter specifically for the Solo are available here in [/Firmware/ArduCopter](/Firmware/ArduCopter).

This firmware can be installed directly using SCP or and SFTP application. Connect your PC to the Solo's WiFi. If you never changed the Solo's wifi password, the default is sololink.

  1. Connect via SCP or an SFTP application to the **copter** with IP 10.1.1.10, username root, password TjSDBkAu
  2. Copy the ArduCopter firmware file (*.px4 or *.apj) into the `/firmware` directory on the copter
  3. Rebooth the copter.  After powering up, you will hear the Cube click and reboot.  The process takes about 45 seconds.
