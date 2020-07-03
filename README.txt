This is Assignment5 project for the Kadenze Machine Learning for digital arts.
The purpose of this project is to manage a wah wah pedal for a sampled guitar riff via android smart phone.
I have used OSCHook app to get data from the sensors of the smartphone and send them to the input helper and wekinator.
The data received in wekinator is processed and sent to the patcher that manages the sound. Wah wah effect is obtained changing Cutoff frequency, Gain and Q of a bandpass filter.
The way to get things working is the following:
1.- Open OSCHook app in the smartphone
2.- Configure port parameters in the app. The computer must be int the same wifi network than the smartphone. You must introduce the IP of your computer and the port where the data is going to be received (default is 12000).
3.- After you press start, data is continuosly sent to the computer in the form of OSC messages.
4.- Open the maxmsp patcher included in this repository.
5.- Press startwindow to begin. This patcher receives the messages from OSCHook and selects only (this can be modified) raw acceleration, linear acceleration, rotation and orientation (13 inputs). 
6.- These 13 inputs are sent to the input helper included. Although I sent 13 for this project I am only going to use the orientation data (azimuth, pitch an roll). These 3 npts are sent to the wekinator project unmodified. The reason is that I was thinking to work with the acceleration data and I needed to smooth the incoming signals. Finallly I found so many problems with the acceleration that I decided to work only with the orientation data (not so noisy).
7.- The wekinator project has 2 class clasifier and 4 numerical outputs. I only use Cutoff, gain and Q outputs.
8.- The patcher includes some communication subpatchers that can be modified to be adapted to different situations.
9.- The patcher includes the limits of the three parameters that can be fixed with the mouse. Numbers from wekinator are scaled to these limits.
10.- When everything is ready press run in wekinator and move your smartphone. Rotating around the small edge form horizontal to vertical Cutoff frequency is changed (somithing like a real pedal). Rotating around the long edge form horizontal to vertical changes Rotating around the perpendicular axis of the smartphone changes the Q.

I did this project with the smartphone because I didn´t have anything better that could serve as an input I could manipulate easily. Relly I would have liked to use this patcher with gesture detection so I can manipulate the sound with my webcam. I hope that before I finished the course I can achieve this goal.
