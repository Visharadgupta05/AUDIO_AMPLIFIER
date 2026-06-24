# AUDIO_AMPLIFIER
This project involves the design and simulation of Class-A , Class B and Class-AB audio power amplifiers of small input signals, using BJT circuits in LTspice. The amplifiers were analyzed and compared based on voltage gain, output power, efficiency, frequency response, and waveform distortion. Special attention was given to crossover distortion in Class-B amplifiers and its reduction in Class-AB designs using a push-pull output stage. The project highlights the performance trade-offs between amplifier classes and demonstrates the principles of analog audio amplifier design.

# CLASS - A AUDIO AMPLIFIER

This part implements a two-stage RC-coupled Class-A audio amplifier using 2N3904 NPN transistors and was designed and simulated in LTspice. The aim was to amplify a low-level audio signal while maintaining Class-A operation,
where the transistor conducts throughout the entire input cycle.

The amplifier uses two common-emitter stages connected through coupling capacitors. The first stage amplifies the weak input signal, while the second stage provides additional voltage gain. Capacitors are used to block DC between stages and allow only the AC audio signal to pass.

## Circuit Description
Stage 1: Common-Emitter Amplifier
1. Q6 (2N3904) acts as the first amplification stage.
2. R16 and R14 form a voltage-divider network to bias the transistor.
3. R15 is the collector resistor.
4. R12 is the emitter resistor used for thermal stability.
5. C10 bypasses the emitter resistor for AC signals, increasing gain.
6. C8 couples the input audio signal to the transistor base while blocking DC.
   
Stage 2: Common-Emitter Amplifier
1. The amplified output of Stage 1 is coupled to Stage 2 through C9.
2. Q7 (2N3904) provides additional amplification.
3. R13, R18, and R19 establish the operating point and stabilize the transistor.
4. The transistor remains in the active region, ensuring Class-A operation.
   
Output Stage
1. C11 (1000 µF) acts as the output coupling capacitor.
2. It blocks DC from reaching the load while allowing the amplified AC signal to pass.
3. The output is taken across the load resistor.

Class A circuit
<img width="728" height="291" alt="image" src="https://github.com/user-attachments/assets/cff0531a-e8f3-4658-a2bf-a769d504fc98" />


Vout (across RLoad)
<img width="1263" height="657" alt="image" src="https://github.com/user-attachments/assets/cd3067ad-2b95-423b-9f4d-72a94a8fdd59" />

IDC (flowing through 12 V DC supply)
<img width="1270" height="678" alt="image" src="https://github.com/user-attachments/assets/cb157e9a-16a4-4f71-a6c2-1be610d0bbbe" />



## Calculations
## Voltage Gain Calculation

Voltage gain is given by:

Av = Vout/ Vin
	​
Substituting measured values:

Av = 1.05 /0.005
	​
Av = 210

Therefore:

Voltage Gain ≈ 210 V/V

Gain in decibels:

Av(dB)=20log(210)

Av(dB)≈46.4dB

DC Power Consumption

From LTspice:

IDC = 4.68mA

Supply voltage:

VCC = 12V

Therefore:

PDC = VCC × IDC	​

PDC = 12×4.68mA

PDC = 56.2mW
Output Power

Output RMS voltage:

Vrms = Vpeak/root(2)
	
Vrms = 1.05/1.414
	  =0.742V

Output power delivered to load:

Pout = (Vrms)^2 / Rload
	
Pout = (0.742)^2 / 1000

Pout ≈ 0.55mW

## Efficiency Calculation

Efficiency is given by:

η = Pout/Pdc * 100

η = 0.55mW / 56.2mW * 100

η≈0.98%


## DISADVANTAGES
The main limitation of the designed Class-A audio amplifier is its low efficiency, as the transistors remain conducting throughout the entire input cycle, resulting in continuous power consumption even when no signal is present. A significant portion of the supplied power is dissipated as heat rather than being delivered to the load. The amplifier is also intended for small-signal operation and therefore cannot directly drive low-impedance loads such as 8 Ω speakers without an additional power output stage. Furthermore, the use of large coupling and bypass capacitors increases circuit size, making the design less suitable for high-power or portable audio applications




# CLASS - B AUDIO AMPLIFIER
A Class B amplifier uses two transistors operating in a push-pull configuration. One transistor amplifies the positive half-cycle of the input signal, while the other amplifies the negative half-cycle. Each transistor conducts for approximately 180° of the input cycle, reducing the power wasted compared to a Class A amplifier.

In this design, the first transistor stage provides voltage amplification, while the complementary NPN-PNP transistor pair acts as the output stage. The output coupling capacitor blocks DC and allows only the amplified AC signal to reach the load.

Components Used
2N3904 (NPN transistor)
2N3906 (PNP transistor)
Resistors for biasing
Coupling capacitors (100 µF, 1000 µF)
12 V DC supply
1 kHz sinusoidal input signal
Load resistor

Image of the circuit : --
<img width="938" height="351" alt="image" src="https://github.com/user-attachments/assets/7980cc3a-27ca-4bf6-a284-4142340d531f" />

Output voltage waveform across Rload :--
<img width="1261" height="439" alt="image" src="https://github.com/user-attachments/assets/c9140367-a5a0-47a2-9a6d-ef9e9b781909" />

## CALCULATIONS :--
Voltage Gain
Av = Vout(pk)/ Vin(pk)
	
Av = 1.45 / 0.01
	​
Av = 145
	​
or in dB:

Av(dB) = 20log(145)

Av(dB)≈43.2dB

From the waveform:

IDC = 1.6114 mA

and

VCC = 12V

So the DC power drawn from the supply is:

PDC = VCC * IDC
	​

PDC = 12×1.6114×10 ^(−3)

PDC = 19.34 mW


From the waveform:

Vout(pk) ≈1.45V

Therefore

Vrms = Vout(pk) / root(2)
	​
Vrms = 1.45/1.414 = 1.025 V

Load:

RL = 1kΩ

Output power:

Pout = RL * (Vrms)^2	​

Pout =1000 * (1.025)^2
	​
Pout ≈ 1.05 mW


Efficiency
η = Pout/PDC * 10

η≈5.4%

## Why the efficiency is so low?
The efficiency of the simulated Class B amplifier is low because it is designed as a small-signal amplifier with a high-resistance load. 
Most of the power is consumed by the biasing and voltage amplification stages, while only a small fraction is delivered to the load. 
Higher efficiencies are achieved in Class B power amplifiers driving low-resistance loads such as speakers.

## Crossover Distortion in Class B Amplifier

A Class B amplifier uses two transistors in a push-pull configuration.
One transistor amplifies the positive half of the input signal, while the other amplifies the negative half. Ideally, the output should be a smooth reproduction of the input waveform.

However, a silicon transistor requires approximately 0.7 V between its base and emitter before it starts conducting. 
Around the zero-crossing region of the input signal, neither transistor conducts because the input voltage is smaller than this threshold.
As a result, a small portion of the waveform near zero volts is not amplified, creating a notch or dead zone in the output waveform.

The Class B amplifier achieved approximately 5.4% efficiency,
representing a significant improvement over the Class A amplifier (~1% efficiency),
demonstrating the trade-off between efficiency and crossover distortion in audio amplifier designs


To overcome this problem, Class AB amplifiers are used


# CLASS - AB AUDIO AMPLIFIER








