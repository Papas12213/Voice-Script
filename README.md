# VoiceScript 
 A pen plotter that physically writes down whatever you say to it. It's like speech to text, but now its actually writing.
 
 [ video ]

 # Try it yourself
 If you have a machine that can process G-code, connect it to your computer. While I use a custom-made 3D printed pen holder, it is not neccesary. You can just zip tie a pen onto the head like I originally did. Then run the file [`talk_to_plot.py`](./talk_to_plot.py) on your terminal or IDE. From there, simply follow the instructions and click enter to start. Since my plotter does not have a z-axis, the code does not include Z commands, which could cause issues on certain machines (This will be updated later to accomodate all types of machines)

 Dont have a plotter but want to see it in action for yourself? Here's me saying multiple different phrases:

 [ video ]

 # Features
 - Using [SpeechRecognition](https://pypi.org/project/SpeechRecognition/) and [Hershey Fonts](https://pypi.org/project/Hershey-Fonts/), my code converts speech into mappable G-code. This G-code is then automatically sent to a plotter, allowing spoken words to be written down on a piece of paper.

 - The pen is held up by a 3D-printed pen holder made in Fusion 360. The holder uses the pens own weight to keep the pen stable, allowing for smooth and non-blotchy text.

 - Since my plotter does not have a z-axis, the pen will drag across the paper, causing streaks that ruin the writing. I have worked aroumd this by providing stop points for the user to lift up the pen and prevent these long lines from happening.

 -  The user can easily change the size of the font by changing the [FONT_SIZE](https://github.com/Papas12213/speech-to-notes-plotter/blob/9c4db8eda4f29700cc667a0df30038a5cd3fbb04/talk_to_plot.py#L11), allowing for more words to be written. The only limitations are the dimensions of the machine.

 - The user has the ability to use whatever font they want (given that it is available in Hershey Fonts). I recommend using cursive as it has the least amount of lifting.

 - While I wrote the code based on my current plotter using only the X and Y axis, the code should work for any machine that can take G-code (CNCs, 3D printers, laser cutters, etc)

# Requirements 
<small style="color: gray; font-style: italic;"> Disclaimer: The code was written especially for my plotter. While it will still work on other machines, the code is based on my plotter's dimensions, axes, and baud rate, so certain movements may be very short. Luckily, these are all decided with variables that can be changed to accommodate your machine.</small>

- The entire code is written in Python. I currently use Python 3.13, but any version of Python 3 will work. You will also need to install the following libraries: Pyserial (imported as serial), HersheyFonts, PyAudio, and SpeechRecognition.

- An internet connection. Your words are turned into digital text by [SpeechRecognition](https://pypi.org/project/SpeechRecognition/) and there are multiples different APIs available for it. I use Google's Web Speech API because of its high accuracy, but this requires an internet connection. Alternatively, you could use PocketSphinx (CMU Sphinx) which allows you to run the code offline, but it has a lower accuracy.

- A machine that can run G-code, perferably one with with only a X and Y axis, but any will work. Additionally, a wired connection is perferred, but a bluetooth connection is included and works as well.

- A microphone is needed for your voice to be recorded and converted into text.

# How it Works