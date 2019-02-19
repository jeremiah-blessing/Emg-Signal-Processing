# Emg_Signal_Processing
EMG  Signal processing - Amplification - Integrating with Arduino - Serial Communication - Simulation / Game engine integration.


Abstract:

Electromyography signals can be used for a plenty of biomedical applications and for improving the human-computer interaction. The purpose of this project is to detect the EMG signals and process them. We further aim at some of the physical applications extending to prosthetic hand control, advanced human-computer interaction.

Basics of EMG:

  EMG (Electromyography) is the study of muscle electric signals. Whenever a muscle is moved, an electrical impulse from the brain reaches the specific muscle and causes the polarization and depolarization of it, which eventually results in contraction that muscle. So, just like our nerves muscles do conduct electrical signals which are commonly known as action potentials. We aim at detecting this signal for a particular muscle and analyze them.

Overall circuit:

  The overall circuit consists of two surface electrodes, DC power supply of 9V, Potentiometer, INA118P, Filter circuit. The surface electrodes pick up the EMG signals. Two 9V batteries connected in series whose common junction forms the ground provides the dual power supply (+9V and-9V) required by the amplifiers. The potentiometer helps in fixing the gain resistance for the INA118P whose output is fed into a Band Pass Filter circuit whose output is rectified using a single diode and then it is supplied to the Arduino’s input. 

INA118P:

  The amplitude range of the EMG signal is 50μV-30mV prior to amplification. As this amplitude is too weak to be analyzed we amplify the signals obtained from the surface electrode by feeding them into an instrumentation amplifier. As the signals from the muscles are of alternating nature, typically a differential amplifier is used for amplification. Instrumentation amplifier is a type of a differential amplifier provided with input buffer amplifiers and is considered to be an ideal choice when it comes to bio medical applications. The gain resistance of the amplifier (Rg) is the one which determines the amplification factor.  Here Rg is maintained by the potentiometer. As the signal keeps varying from one person to another, hence Rg must be changed accordingly in order to obtain the operating voltage of ADC (Analog-Digital Converter).  The INA118P’s output is expected to be in the range of 2V.

Filter circuit:

  The filter circuit is used to eliminate the noise present in the amplified signal. Various factors such as motion artifact and crosstalk intervention can create these noise signals. Here we use an Active band pass filter to eliminate the noises without affecting the EMG signal.
The frequency of the signal lies in the range of 50-450 Hz, (predominantly 430-450Hz) while the rest are just noise. Hence we use a RC low pass filter, cutoff at 723Hz and the high pass at 7.237Hz by adjusting the resistances and capacitances accordingly. The best output without any signal loss for an input signal of 10-450Hz is obtained by setting the cutoff values as above. The purpose of using an Active band pass filter is to retain the signal without any losses and thereby the gain of the amplifier in this circuit is set to 2. Hence the output from the filter circuit is in the range of 4V.

Processing of EMG signals:

EMG signals can be processed by microcontrollers or microprocessor[in case of complex analysis]. The signals from the filter circuits have to be rectified to use it with the ADC chips[Analog to Digital Converter] as the ADC chips can only work with the DC voltage. The output from the ADC chips is then sent to microcontrollers to analyze the signals.  The signal from the microcontroller can also be sent to another processor through serial communication or I/O port for accurate and complex analysis. In our project we have used ADS1115 Analog to Digital Converter and ATmega328P microcontroller where both are soldered and readymade as Arduino board. The operating voltage of ADS1115 chip is 0 to 5V. The amplification, filter and rectification circuits are designed in such a way to get the output of the whole circuit in the range of 0 to 5V.The common method to analyze EMG signals is by Gaussian Distribution function. In our project we have analyzed only one hand movement, so instead of using Gaussian Distribution, we set a threshold value for the ADC output in the Arduino and used the trigger mechanism in the Arduino to use for our purpose. Other microcontrollers can also be used other than Arduino.

Applications of this Circuit:

  The output from the Arduino board can be used for diagnosing myopathic muscle conditions, prosthetics, gaming consoles, RC quadcopter etc. The circuit which we made can be used in Prosthetics and as Gaming Consoles.

PROSTHETICS:
  The output from the Arduino can be fed in to the Servo motors in the prosthetic limb to control the movement of the respective part. Instead of making a real prosthetic limb, we simulated this in a 3D program. In our project, we get the signal through the Serial Communication [serial.write(1) – C code line] when the output reaches the threshold value from the Arduino. We have integrated it with the Unity game Engine C# Script and added the Serial Communication in the script and which plays the animation whenever the muscle is contracted.

GAMING CONSOLE:
  The same procedure is used to obtain the output from the Arduino. We use a C# script to communicate with the Arduino. So whenever the muscle is contracted, another C# Script which is attached with the game character, triggers the Hit trigger which is the default animation of the character. The Hit trigger is the recorded animation which the character does whenever the muscle is contracted.


SOFTWARE USED:
1.	Maya – Modelling, Rigging, Animation
2.	Microsoft Visual Studio – C# Script
3.	Unity Game engine – Simulation
4.	Arduino IDE – To Program Arduino Board
5.	Serial Plotter –To calibrate the threshold value.





Reference : 
1.	https://www.delsys.com/products/software/emgworks/sqm/factors/
2.	http://www.soe.uoguelph.ca/webfiles/mleuniss/Biomechanics/EMG.html
3.	https://www.delsys.com/Attachments_pdf/WP_SEMGintro.pdf
4.	https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3821366/
5.	https://pdfs.semanticscholar.org/c348/f06416aa03154c40bb82d5b26cef40e5840d.pdf
6.	https://physionet.org/physiobank/database/emgdb/
7.	http://www.learningaboutelectronics.com/Articles/Active-op-amp-bandpass-filter-circuit.php
8.	https://en.wikipedia.org/wiki/Instrumentation_amplifier
9.	https://en.wikipedia.org/wiki/Electromyography
10.	http://www.arpnjournals.org/jeas/research_papers/rp_2016/jeas_0316_3811.pdf
11.	http://khairulanam.com/publication/
