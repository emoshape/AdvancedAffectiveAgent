# TheSmartToy
The Smart Toy - Python Open Source - Raspberry Pi

## Synopsis

The Smart Toy program links together EPU emotion device, AI and various IO devices to form a smart toy with emotions.

## Code Example

```python
    robot = Robot( input_method = 'voice' )
    robot.setLights( Bridge('<Philips bridge ip>') )

    while True:
        response = robot.listen()
        if response == 'bye':
            break
```

## Motivation

A short description of the motivation behind the creation and maintenance of the project. This should explain **why** the project exists.

## Installation

The following modules are used in script that need to be installed:
```python
import requests
from lxml import html
import pyttsx
import speech_recognition as sr
import wikipedia
from googleapiclient.discovery import build
import httplib2
from phue import Bridge
from PIL import Image, ImageDraw
```

## API Reference

`Emo` - class to work with EPU device

`Emo.__init__(host, port)` - perform connection to EPU devise

`Emo.getEmo()` - get current emotions of EPU. Returns a dictionary with emotion channels and value for each channel. Dictionary keys:

     'channelEXCITED'
     'channelCONFIDENT'
     'channelHAPPY' 
     'channelDESIRE'
     'channelTRUST' 
     'channelFEAR'  
     'channelSURPRISE'
     'channelINATTENTION'
     'channelSAD'     
     'channelREGRET'  
     'channelDISGUST' 
     'channelANGER'   

`Emo.getEmoStr()` - get current emotion and interpretes it into text string. For example 'fine', 'embarrassed', etc 

`Robot` - main class that links together emotions, AI, input, output and other function as a Smart Toy.

`Robot.__init__(input_method)` - initialize smart toy object. 
Input_method can be 'voice' or 'type'. When running on Raspbery Pi should be always 'voice'.
Also TTS and Emo object are initialized here.
Also robot and human names are asked and remembered here.

`Robot.say(message)` - say messages via TTS and also prints to stdout.

`Robot.sendAI(message)` - send message to AI bot, send answer to EPU (Emo) and reply with the answer.

`Robot.listen([param])` - listen what user types or says and starts some scenario depending on what was said.
If input message doesn't imply any scenario, it's forwarder to AI.

`Robot.setInputMethod(input_method)` - set robot input method. Input_method can be 'voice' or 'type'

`Robot.inputMethod()` - return robot input method.

`Robot.setEmo(emo)` - set robot Emo object.

`Robot.emo()` - return robot Emo object.

`Robot.setTts(tts)` - set robot TTS object. Now it can be only pytts.init()

`Robot.tts()` - return TTS object.

`Robot.setLights(lights)` - set lights. lights parameter for now is only phue.Bridge object.

`Robot.robotName()` - return robot name.

`Robot.humanName()` - return human name.

`Robot.getLastInputMsg()` - return last message sent to robot.

## Contributors

Let people know how they can dive into the project, include important links to things like issue trackers, irc, twitter accounts if applicable.

## License

GNU General Public License
