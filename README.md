# AUDIO_AMPLIFIER
This project involves the design and simulation of Class-A , Class B and Class-AB audio power amplifiers, using BJT circuits in LTspice. The amplifiers were analyzed and compared based on voltage gain, output power, efficiency, frequency response, and waveform distortion. Special attention was given to crossover distortion in Class-B amplifiers and its reduction in Class-AB designs using a push-pull output stage. The project highlights the performance trade-offs between amplifier classes and demonstrates the principles of analog audio amplifier design.

# CLASS - A AUDIO AMPLIFIER

Designed and simulated a single-ended Class A power amplifier using BJTs in LTspice. The output transistor was biased to conduct throughout the full input cycle (360° conduction), providing highly linear amplification with minimal distortion. The project analyzed voltage gain, output power, quiescent current, and efficiency while demonstrating the trade-off between superior signal fidelity and lower efficiency.


## Circuit Description
Stage-wise Description

1. Input Coupling (C8): Blocks DC from the signal source and passes the AC input.
2. Bias Network (R16, R14): Establishes the DC operating point for Q6.
3. Voltage Amplifier (Q6): Provides the initial voltage amplification.
4. Emitter Network (R12, C10): Stabilizes the bias and increases AC gain through emitter bypassing.
5. Interstage Coupling (C9): Transfers the amplified AC signal to the output stage while blocking DC.
6. Output Stage (Q7): Operates in Class A mode and provides power amplification.
7. Bias Network (R17, R18): Sets the quiescent operating point of Q7 for linear operation.
8. Collector Load (R13): Determines the collector current and output voltage swing.
9. Output Coupling Capacitor (C11): Removes the DC component before delivering the amplified signal to the load.
10. Load (RLoad): Represents the external load across which the amplified output is obtained.


OBSERVATIONS : -
1. Increasing the input signal beyond the amplifier's linear operating range drove the output transistor into saturation and cutoff, causing waveform clipping and distortion. 
 That is why my output voltage started clipping after 10mV peak suply.
2. The amplifier was successfully biased to operate in Class A, with the output transistor conducting throughout the entire input cycle (360° conduction).
3. Proper DC biasing was achieved by setting the collector voltage close to half of the supply voltage, enabling maximum symmetrical output swing.
4. The output waveform became a clean sinusoid after optimizing the bias network and operating conditions.
5.  Increasing the supply voltage from 15 V to 24 V increased the available output voltage swing and delayed the onset of clipping.
6. Increasing the load resistance from 100 Ω to 470 Ω reduced the load current, improving linear operation.


Class A circuit
<img width="824" height="418" alt="image" src="https://github.com/user-attachments/assets/61454d68-42fe-4d83-9520-a74a9bf01586" />


Vout (across RLoad) and current across Rload
<img width="1274" height="646" alt="image" src="https://github.com/user-attachments/assets/578c2a81-b1a7-40c2-8917-1121ec2542cd" />



## Calculations
1. Voltage Gain

The voltage gain is calculated as:

Av = Vout(rms)/ Vin(rms)
	​
	
Av = 4.321 / 0.00707

Av = 611.31V/V
	​

Voltage gain in decibels:

Av(dB) = 20log(611.31)

Av = 55.72dB
	​

2. Input Power

The DC input power supplied to the amplifier is

Pin ​= VCC × IDC
	​
Pin = 24×0.03205

Pin = 0.769W
	​

3. Output Power

The AC output power delivered to the load is

Pout = (Vout(rms))^2 / Rload

Pout = (4.321)^2 / 470	​

Pout = 0.0397W = 39.7mW
	​

4. Efficiency

The efficiency of the amplifier is

η = Pout/Pin * 100
	​
η = 0.0397 / 0.769 * 100
	​
η=5.16%



## NOTE
The negative sign reported for I(V7) in LTspice indicates the voltage source is supplying power to the circuit. 
For power and efficiency calculations, the magnitude of the supply current is used.

## RESULTS :--

<img width="368" height="128" alt="image" src="https://github.com/user-attachments/assets/7b4f04d8-e9c6-41b4-ab95-139ce156d7b0" />



## DISADVANTAGES
The efficiency is low because the Class A amplifier continuously draws current from the supply, even in the absence of an input signal.
Most of the supplied power is dissipated as heat in the transistor and collector resistor, while only a small portion is delivered to the load.




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

























