========
A2-Mode papertty
========
This is a patched version of PapperTTY (https://github.com/joukos/PaperTTY) with A2-Mode and sync refresh to 
the second to allow nice clock displays. The original project semes to be unmaintaind so I made an unmaintained fork
for anybody who finds this usefull. Feel free to add the changes to your fork. Greatest possible thanks to the original authors.

Changes
=======
- enable a2 mode
- 8mhz
- update at full second

Install
========
- apt install libjpeg-dev zlib1g-dev
- python -m venv venv
- source venv/bin/activate
- pip install vncdotool click spidev rpi.gpio

Start VNC
=========
::

  #!/bin/bash
  # make vnc password with: x11vnc -storepasswd
  source ~/.bashrc
  export DISPLAY=:1
  Xvfb $DISPLAY -nocursor -screen 0 816x1184x24 &
  sleep 10
  # setup password with:
  # x11vnc -storepasswd 
  x11vnc -cursor none -display $DISPLAY -forever -loop -noxdamage -repeat -rfbauth ~/.vnc/passwd -rfbport 5900 -shared &
  chromium --window-position=0,0 --window-size=817,1184 /home/pi/index.html &

