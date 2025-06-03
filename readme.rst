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

