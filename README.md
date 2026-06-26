# AUDIO_AMPLIFIER
This project involves the design and simulation of Class-A , and Class- B and Class-AB audio power amplifiers, using BJT circuits in LTspice. The amplifiers were analyzed and compared based on voltage gain, output power, efficiency, and waveform distortion. Special attention was given to crossover distortion in Class-B amplifiers and its reduction in Class-AB designs using a push-pull output stage. The project highlights the performance trade-offs between amplifier classes and demonstrates the principles of analog audio amplifier design.

# CLASS - A AUDIO AMPLIFIER

This project implements a Class A common-emitter audio amplifier using a BC546B NPN transistor. The amplifier is designed to amplify a small AC audio signal while maintaining excellent linearity. Unlike Class B amplifiers, the transistor remains in the active region throughout the entire input cycle (360° conduction), resulting in low distortion at the expense of lower power efficiency.


## Circuit Description
Components Used

1. V5 – 12 V DC Power Supply
2. V6 – AC Input Signal Source (300 mV, 1 kHz Sine Wave)
3. Q6 – BC546B NPN Transistor
4. R10 – 10 kΩ Base Bias Resistor
5. R9 – 3.3 kΩ Base Bias Resistor
6. R11 – 47 Ω Collector Resistor
7. R12 – 3 Ω Emitter Resistor
8. C7 – 100 µF Input Coupling Capacitor
9. C8 – 10 µF Output Coupling Capacitor
10. C9 – 100 µF Emitter Bypass Capacitor
11. RL2 – 50 Ω Load Resistor


OBSERVATIONS : -
1. Increasing the input signal beyond the amplifier's linear operating range drove the output transistor into saturation and cutoff, causing waveform clipping and distortion. 
 That is why my output voltage started clipping after 10mV peak suply.
2. The amplifier was successfully biased to operate in Class A, with the output transistor conducting throughout the entire input cycle (360° conduction).
3. Proper DC biasing was achieved by setting the collector voltage close to half of the supply voltage, enabling maximum symmetrical output swing.
4. The output waveform became a clean sinusoid after optimizing the bias network and operating conditions.
5.  Increasing the supply voltage from 15 V to 24 V increased the available output voltage swing and delayed the onset of clipping.
6. Increasing the load resistance from 100 Ω to 470 Ω reduced the load current, improving linear operation.


Class A circuit
<img width="698" height="213" alt="image" src="https://github.com/user-attachments/assets/1007109c-1cff-413a-ace9-0a21782c2854" />


Vout (across RLoad)  and Vin graph 
<img width="1262" height="353" alt="image" src="https://github.com/user-attachments/assets/506e42fd-9034-4f70-a52a-b07f3fca9576" />





## Calculations
1. Voltage Gain

The voltage gain is calculated as:

Av = Vout(rms)/ Vin(rms)
	= 2.40/ 0.212
	= 11.34​

In decibels,

Av(dB) = 20log(1.5377)

Av = 21.09 dB

2. Output Power
   
Pout = Vout(rms)^2 / Rload
	
Pout = (2.4)^2 / 50
	​

=0.11568 W
​

3. Input DC Power
PDC = VCC × IDC

    = 12×0.0122
​
    = 1.46 W
	​

5. Efficiency

η= Pout/ PDC * 100

​η= 0.115/1.46 * 100

η = 7.88 % 
	​

## OBSERVATION
The measured efficiency of 7.88% is characteristic of a resistor-loaded Class A amplifier.
The transistor conducts throughout the entire input cycle (360° conduction) and continuously draws current from the 12 V supply, even when little or no signal is present.
As a result, a large portion of the input DC power is dissipated as heat in the transistor and collector resistor rather than being delivered to the load.


## DISADVANTAGES
The efficiency is low because the Class A amplifier continuously draws current from the supply, even in the absence of an input signal.
Most of the supplied power is dissipated as heat in the transistor and collector resistor, while only a small portion is delivered to the load.




# CLASS - B AUDIO AMPLIFIER
This circuit is a Class B push-pull audio amplifier implemented using complementary bipolar junction transistors. 

It amplifies the current of an AC audio signal to drive a low-resistance load while blocking DC from both the input and output.

This is the circuit : ---
<img width="714" height="341" alt="image" src="https://github.com/user-attachments/assets/0a55b1d5-a76f-4206-bb2a-80729fcf7f90" />


This is the output voltage waveform : --
<img width="1267" height="336" alt="image" src="https://github.com/user-attachments/assets/dd6e75fc-fd46-4476-bce8-b58983334369" />




Components and Their Functions
1. V1 (12 V DC Supply):
 Provides the power required for the amplifier. The circuit operates from a single 12 V Supply.
2. V2 (Input Signal):
Represents the audio input as a 1 kHz sine wave with a peak amplitude of 3 V.
3. C1 (100 µF) – Input Coupling Capacitor:
Couples the AC input signal to the amplifier while blocking any DC component from the signal source. This ensures that the input source does not affect the transistor biasing.
4. R3 and R4 (10 kΩ each) – Biasing Network:
These resistors form a voltage divider that establishes a bias voltage of approximately 12 V (half the supply voltage) at the transistor bases. This midpoint bias allows the output to swing both above and below the quiescent voltage for symmetrical signal amplification.
5. Q4 (BC547C) – NPN Transistor:
Acts as the upper transistor of the push-pull stage. It conducts during the positive half-cycle of the input signal, supplying current to the load.
6. Q5 (BC557C) – PNP Transistor:
Acts as the lower transistor of the push-pull stage. It conducts during the negative half-cycle of the input signal, providing the return current path for the load.
7. C2 (100 µF) – Output Coupling Capacitor:
Blocks the DC bias present at the amplifier output while allowing only the amplified AC signal to reach the load. This prevents DC current from flowing through the load.
8. RL1 (47 Ω) – Load Resistance:
Represents the output load, such as a small speaker or equivalent resistive load, which receives the amplified audio signal.

## WORKING
The input audio signal is first passed through the input coupling capacitor (C1), which removes any DC component.
The resistor divider (R3 and R4) biases the bases of the complementary transistor pair at approximately half the supply voltage. 
When the input signal becomes positive, the NPN transistor (Q4) conducts and delivers current to the output.
During the negative half-cycle, the PNP transistor (Q5) conducts and provides the return current path.
Thus, each transistor conducts for approximately 180° of the input waveform


## CALCULATIONS :-

Voltage Gain
Av = Vout(rms)/Vin(rms)
	
Av = 1.49/2.12

Av = 0.7049 ≈ 0.705
	​

In decibels,

Av (dB) = 20log	(0.7049)

Av(dB) = −3.04 dB
	​
	
2. Output Power
Pout =  Vout(rms)^2	​/ Rload
	
Pout  =0.04755 W = 47.55 mW
	​

3. Input DC Power
PDC = VCC * IDC
	​
12 × 0.014 W

PDC = 0.165 W
	​

4. Efficiency
η = Pout / PDC * 100​

Pout = 0.0475 / 0.165 * 100
​
= 

η = 28.43 %


## OBSERVATION
There is an observation that the output voltage graph is zero distorion  for some time .This distortion is known as crossover distortion.
In this amplifier, the NPN transistor amplifies the positive half of the signal, while the PNP transistor amplifies the negative half.
Since each transistor requires about 0.7 V between its base and emitter before it starts conducting, there is a small range around zero volts where both transistors remain OFF.
During this interval, the output cannot accurately follow the input, creating a small flat region or notch in the waveform. 





# CLASS - AB AUDIO AMPLIFIER
This implements a Class AB push-pull audio amplifier using complementary transistors (BC547C and BC557C) with two silicon diodes (1N4148) for biasing.
The diodes provide a small forward bias between the transistor bases, allowing both transistors to conduct slightly even when there is no input signal.
This eliminates the crossover distortion present in Class B amplifiers while maintaining significantly higher efficiency than Class A amplifiers.

Components Used
1. V3 – 12 V DC Power Supply
2. V7 – AC Input Signal Source (3 V Peak, 1 kHz Sine Wave)
3. Q1 – BC547C NPN Transistor
4. Q2 – BC557C PNP Transistor
5. D1, D2 – 1N4148 Silicon Diodes (Biasing Diodes)
6. R1 – 10 kΩ Bias Resistor
7. R2 – 10 kΩ Bias Resistor
8. C3 – 100 µF Input Coupling Capacitor
9. C4 – 100 µF Output Coupling Capacitor
10. RL3 – 47 Ω Load Resistor


## WORKING

The input audio signal is first passed through the input coupling capacitor (C3), which blocks any DC component and allows only the AC signal to reach the amplifier.

The two 1N4148 diodes (D1 and D2) create a small voltage difference between the bases of the BC547C (NPN) and BC557C (PNP) transistors. This keeps both transistors slightly turned on even when there is no input signal.

During the positive half-cycle of the input signal, the NPN transistor (Q1) conducts more and supplies current to the load. During the negative half-cycle, the PNP transistor (Q2) conducts more and drives the load in the opposite direction.

Since both transistors are already slightly conducting near the zero-crossing point, the transition from one transistor to the other is smooth.


## CLASS AB IMAGES 

CIRCUIT :-- 
<img width="1474" height="514" alt="image" src="https://github.com/user-attachments/assets/29dfca8f-ff09-4e5c-a900-0282dbb056d6" />
 
OUTPUT VS INPUT GRAPH :-- 
<img width="1261" height="311" alt="image" src="https://github.com/user-attachments/assets/c51df34c-a39a-4e1f-813c-fd02db9535fd" />



## CALCULATIONS :-- 

Voltage Gain
Av = Vout(rms)/Vin(rms)
	
Av = 1.89/2.12

Av = 0.896
	​

In decibels,

Av (dB) = 20log	(0.896)

Av(dB) = −0.95 dB
	​
	
2. Output Power
Pout =  Vout(rms)^2	​/ Rload
	
Pout  =0.0768 W 
	​

3. Input DC Power
PDC = VCC * IDC
	​
12 × 0.018 W

PDC = 0.218 W
	​

4. Efficiency
η = Pout / PDC * 100​

​η = 0.0768/0.218 * 100

η = 35.18 %


## OBSERVATIONS

1. The output waveform is smooth and nearly sinusoidal, indicating that crossover distortion has been significantly reduced.
2. The 1N4148 biasing diodes keep both transistors slightly conducting around the zero-crossing point, ensuring a smooth transition between the NPN and PNP transistors.
3. The amplifier provides current gain with a voltage gain close to unity, characteristic of a push-pull emitter follower.
4. Compared to the Class B amplifier, the Class AB amplifier exhibits lower crossover distortion and higher efficiency.
5. Compared to the Class A amplifier, it offers significantly higher efficiency while maintaining good linearity











