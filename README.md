# AUDIO_AMPLIFIER
This project involves the design and simulation of Class-A, Class-B, and Class-AB audio power amplifiers using BJT circuits in LTspice. The amplifiers were analyzed and compared based on voltage gain, output power, efficiency, frequency response, and waveform distortion. Special attention was given to crossover distortion in Class-B amplifiers and its reduction in Class-AB designs using a push-pull output stage. The project highlights the performance trade-offs between amplifier classes and demonstrates the principles of analog audio amplifier design.

# CLASS - A AUDIO AMPLIFIER

This project implements a two-stage RC-coupled Class-A audio amplifier using 2N3904 NPN transistors and was designed and simulated in LTspice. The aim was to amplify a low-level audio signal while maintaining Class-A operation,
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
<img width="1263" height="657" alt="image" src="https://github.com/user-attachments/assets/cd3067ad-2b95-423b-9f4d-72a94a8fdd59" />

Vout (across RLoad)
<img width="728" height="291" alt="image" src="https://github.com/user-attachments/assets/cff0531a-e8f3-4658-a2bf-a769d504fc98" />

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


# CLASS - B AUDIO AMPLIFIER

Its components :--

1. Q2 (2N2222): NPN transistor that amplifies the positive half-cycle of the input signal.
2. Q3 (2N2907): PNP transistor that amplifies the negative half-cycle of the input signal.
3. R10 (10 kΩ): Upper bias resistor that helps set the transistor operating point.
4. R8 (10 kΩ): Lower bias resistor that completes the bias network.
5. C4 (100 µF): Input coupling capacitor that passes AC signals and blocks DC.
6. C5 (470 µF): Output coupling capacitor that passes the amplified AC signal to the load.
7. R7 (8 Ω): Represents the speaker/load connected to the amplifier output.
8. V3 (12 V): DC power supply for the amplifier.
9. V4 (SINE(0 3 1k)): 1 kHz sinusoidal input signal

A Class-B amplifier is designed to improve efficiency by allowing each transistor to conduct for only half of the input signal cycle (180°).

In this circuit, the 2N2222 (NPN) transistor conducts during the positive half-cycle of the input signal, while the 2N2907 (PNP) transistor conducts during the negative half-cycle. Together, they reproduce the complete output waveform at the load.

Unlike a Class-A amplifier, where the transistor remains ON all the time, the transistors in a Class-B amplifier are OFF when no signal is present. This significantly reduces power dissipation and improves efficiency.

Calculations
Voltage Gain

Input peak voltage:

Vin	=3V

Output peak voltage (from simulation):

Vout ≈2.2V

Voltage gain:

Av = Vout / Vin
Av = 2.2 / 3 =0.73

The circuit acts mainly as a power amplifier (current buffer) rather than a voltage amplifier, so the voltage gain is slightly less than 1.

DC Power Consumed

Supply voltage:

VCC = 12V

Average supply current from LTspice:

IDC = 80.88mA
IDC = 0.08088A

DC power drawn from the supply:

PDC = VCC × IDC
	
PDC = 12×0.08088
PDC = 0.971W

Output Power

Load resistance:

RL = 8Ω

Output peak voltage:

Vp = 2.2V

Output RMS voltage:

V RMS = Vp / 1.414
      =1.56V

Power delivered to the load:

Pout =  (Vrms) ^ 2/RL

Pout = (1.56)^2 / 8

Pout = 0.304W

Efficiency (η) = Pout/Pdc * 100

η = .304 / .971 * 100
	​
η = 31.3%


This efficiency is much higher than the Class-A amplifier because the transistors conduct only during their respective half-cycles, reducing power dissipation.


But here we can see there is a small distortion in output waveform . That is called crossover distortion. 

This occurs because the NPN and PNP transistors require approximately 0.7 V of base-emitter voltage before they begin conducting. As the input signal passes through zero, both transistors remain OFF for a short interval, 
creating a dead zone where the output does not accurately follow the input.
This is a common drawback of Class-B amplifiers and reduces their linearity compared to Class-A amplifiers.

<img width="1278" height="695" alt="image" src="https://github.com/user-attachments/assets/1245980b-03b5-4d55-89c7-08938add8d79" />


# CLASS - AB AUDIO AMPLIFIER








