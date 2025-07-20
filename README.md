# OGX-LIVE
![OGX-Mini Boards](images/20250701_232110.jpg "OGX-LIVE Shell") 

Fully Integrated OGX-Mini and Xbox Live Communicator
The all-in-one solution for using modern controllers on Insignia

Combining the advanced controller emulation support of WiredOpposite's OGX-Mini with Ryzee119's HAWK communicator, you can now play online with the comfort and precision of modern controllers while berating your Warthog driver for going in the wrong direction.

![Configst](images/backgroundwide.png") 

[**Visit the web app here**](https://wiredopposite.github.io/OGX-Mini-WebApp/) to change your mappings and deadzone settings. To pair the OGX-Mini with the web app via USB, plug your controller in, then connect it to your PC, hold **Start + Left Bumper + Right Bumper** to enter web app mode. Click "Connect via USB" in the web app and select the OGX-Mini. You can also pair via Bluetooth, no extra steps are needed in that case. 

## Supported platforms
- Original Xbox
- Playstation 3
- Nintendo Switch (docked)
- XInput (use [**UsbdSecPatch**](https://github.com/InvoxiPlayGames/UsbdSecPatch) for Xbox 360, or select the patch in J-Runner while flashing your NAND)
- Playstation Classic
- DInput

## Changing platforms
By default the OGX-Mini will emulate an OG Xbox controller, you must hold a button combo for 3 seconds to change which platform you want to play on. Your chosen mode will persist after powering off the device. 

Start = Plus (Switch) = Options (Dualsense/DS4)

- XInput
    - Start + Dpad Up 
- Original Xbox
    - Start + Dpad Right
- Original Xbox Steel Battalion
    - Start + Dpad Right + Right Bumper
- Original Xbox DVD Remote
    - Start + Dpad Right + Left Bumper
- Switch
    - Start + Dpad Down
- PlayStation 3
    - Start + Dpad Left
- PlayStation Classic
    - Start + A (Cross for PlayStation and B for Switch gamepads)
- Web Application Mode
    - Start + Left Bumper + Right Bumper

After a new mode is stored, the RP2040 will reset itself so you don't need to unplug it.

## Supported devices
### Wired controllers
- Original Xbox Duke and S
- Xbox 360, One, Series, and Elite
- Dualshock 3 (PS3)
- Dualshock 4 (PS4)
- Dualsense (PS5)
- Nintendo Switch Pro
- Nintendo Switch wired
- Nintendo 64 Generic USB
- Playstation Classic
- Generic DInput
- Generic HID (mappings may need to be editted in the web app)

Note: There are some third party controllers that can change their VID/PID, these might not work correctly.

### Wireless adapters
- Xbox 360 PC adapter (Microsoft or clones)
- 8Bitdo v1 and v2 Bluetooth adapters (set to XInput mode)
- Most wireless adapters that present themselves as Switch/XInput/PlayStation controllers should work

### Wireless Bluetooth controllers (Pico W & ESP32)
**Note:** Bluetooth functionality is in early testing, some may have quirks.
- Xbox Series, One, and Elite 2
- Dualshock 3
- Dualshock 4
- Dualsense
- Switch Pro
- Steam
- Stadia
- And more

Please visit [**this page**](https://bluepad32.readthedocs.io/en/latest/supported_gamepads/) for a more comprehensive list of supported controllers and Bluetooth pairing instructions.

## Features new to v1.0.0
- Bluetooth functionality for the Pico W, Pico 2 W, and Pico+ESP32.
- Web application (connectable via USB or Bluetooth) for configuring deadzones and buttons mappings, supports up to 8 saved profiles.
- Pi Pico 2 and Pico 2 W (RP2350) support.
- Reduced latency by about 3-4 ms, graphs showing comparisons are coming.
- 4 channel functionality, connect 4 Picos and use one Xbox 360 wireless adapter to control all 4.
- Delayed USB mount until a controller is plugged in, useful for internal installation (non-Bluetooth boards only). 
- Generic HID controller support.
- Dualshock 3 emulation (minus gyros), rumble now works.
- Steel Battalion controller emulation with a wireless Xbox 360 chatpad.
- Xbox DVD dongle emulation. You must provide or dump your own dongle firmware, see the Tools directory.
- Analog button support on OG Xbox and PS3.
- RGB LED support for RP2040-Zero and Adafruit Feather boards.

## Planned additions
- More accurate report parser for unknown HID controllers
- Hardware design for internal OG Xbox install
- Hardware design for 4 channel RP2040-Zero adapter
- Wired Xbox 360 chatpad support
- Wired Xbox One chatpad support
- Switch (as input) rumble support
- OG Xbox communicator support (in some form)
- Generic bluetooth dongle support
- Button macros
- Rumble settings (intensity, enabled/disable, etc.)

Pre-Launch Sale. Estimated ship date: August 6th. 

## Communicator Use

Recommended configuration: 12 foot 3.5mm TTRS cable and 12 foot USB-A cable
Alternatively you could use a USB-C extension and then shorter cable runs for the headset and controller.
8-BitDo or equivalent wireless adapter is necessary for wireless function. 

The OGX-LIVE provides feature parity with the original communicator with the following differences:
- Dual independent processors for gamepad and audio processing to eliminate latency
- Support for a wide array of modern controllers and input devices. Full list available on the OGX-LIVE Github repository
- A 3.5mm TRRS jack is used to support more generic headsets. (Stereo headsets will output as mono.)
- The volume wheel is replaced with a button. Volume is indicated by LED brightness.
- The Xbox chat feature only outputs voice audio, so a single ear chat headset is recommended.

Tip: When searching online for compatible headsets use the term: "mono chat headset 3.5" to get the best results for single ear chat headsets

Usage:
**Press the button to increment the volume. Once maximum volume is reached, it will cycle back to zero.
**Hold the button for 1 second to mute and disable the microphone input (LED will flash at 1Hz).
**Hold the button 2 seconds to enter microphone gain adjustment mode (LED will flash at 4Hz).
**Volume and microphone gain adjustments will be saved internally. You can reset these to default by holding the button down for 8 seconds.

FAQ:
Why can't I hear the in-game audio? 
- The original Xbox's headset was designed to playback chat audio only, however, with the use of an external mixer you could mix the audio output from the Xbox with the chat audio from the Hawk for a full headphone gaming experience. 
What is the pinout of the headphone jack?
- OGX-LIVE's headphone jack is wired as per CTIA standard TRRS. There is another less common standard called OMTP. This will not work but adapters are available.
Microphone is really quiet?
- You can increase the microphone gain above default. Hold the Hawk button down for more than 2 seconds to enter gain adjustment mode. The LED will blink 4 times per second to show it is in the right mode then press the button to increase the gain. Hold for 1 second to exit. If this is still too quiet, you can modify the MAX_MICROPHONE_GAIN variable and recompile the code to bump it up even higher.
Speaker is really quiet?
- Adjust the volume by pressing the button until the LED is at its maximum brightness. Unfortunately, it is already compiled to the maximum allowable by OGX-LIVE. If it is still too quiet, your headset's impedance may be too low.
