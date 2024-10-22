Mic Array
=========

Utils for [ReSpeaker Microphone Array](https://www.seeedstudio.com/ReSpeaker-Mic-Array-Far-field-w--7-PDM-Microphones--p-2719.html). It includes DOA (Direction of Arrival), VAD (Voice Activity Detection), KWS (Keyword Spotting or Keyword Search) and etc.

+ `pixel_ring.py` - control the pixel ring
+ `mic_array.py` - read 8 channels raw audio from the Mic Array and estimate sound's DOA (Direction of Arrival)
+ `vad_doa.py` - do VAD (Voice Activity Detection) and then estimate DOA
+ `kws_doa.py` - search keyword and then estimate DOA

## Get started
1. Run `pixel_ring.py` to control the pixel ring of the Mic Array through USB HID

   ```
   sudo pip install pyusb
   sudo python pixel_ring.py
   ```
   If you don't want to access USB device with `sudo`, add a udev `.rules` file to `/etc/udev/rules.d`:
   ```
   echo 'SUBSYSTEM=="usb", MODE="0666"' | sudo tee -a /etc/udev/rules.d/60-usb.rules
   sudo udevadm control -R  # then re-plug the usb device
   ```

2. Read 8 channels audio from the Mic Array and estimate sound's DOA
   ```
   sudo apt-get install python-numpy    # or pip install numpy
   python mic_array.py
   ```

3. Do VAD and then estimate DOA
   ```
   sudo pip install webrtcvad
   python vad_doa.py
   ```
   
## For Raspberry Pi
Google released [Google Assistant Library](https://github.com/googlesamples/assistant-sdk-python/tree/master/google-assistant-library) for Raspberry Pi to provide hotword detection ("Ok Google" or "Hey Google"), audio recording, assistant response playback and etc. We can add LED lights indicator based on the library to make a device very similar with Google Home.

1. Follow [the guide](https://github.com/googlesamples/assistant-sdk-python/tree/master/google-assistant-library) to install Google Assistant Library.
2. Run `python google_assistant_for_raspberry_pi.py`
