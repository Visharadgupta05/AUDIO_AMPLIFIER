# AUDIO_AMPLIFIER
This project involves the design and simulation of Class-A, Class-B, and Class-AB audio power amplifiers using BJT circuits in LTspice. The amplifiers were analyzed and compared based on voltage gain, output power, efficiency, frequency response, and waveform distortion. Special attention was given to crossover distortion in Class-B amplifiers and its reduction in Class-AB designs using a push-pull output stage. The project highlights the performance trade-offs between amplifier classes and demonstrates the principles of analog audio amplifier design.

# CLASS - A AUDIO AMPLIFIER

Here are its components : --
1. V1 (12 V DC Supply): Provides the power required for the amplifier to operate.
2. V2 (Audio Input Signal): Generates a small 1 kHz sinusoidal signal that is amplified by the circuit.
3. Q1 (2N3904 Transistor): Acts as the main amplifying device. Small changes at the base produce larger changes at the collector.
4. R5 (47 kΩ) and R6 (10 kΩ): Form a voltage-divider bias network that sets the transistor's operating point in the active region for Class-A operation.
5. R1 (1 kΩ Emitter Resistor): Stabilizes the transistor current and improves thermal stability by preventing large current variations.
6. C3 (100 µF Emitter Bypass Capacitor): Bypasses R1 for AC signals, reducing negative feedback and increasing voltage gain.
7. R4 (4.7 kΩ Collector Resistor): Converts collector current variations into output voltage variations, producing amplification.
8. C1 (100 µF Input Coupling Capacitor): Couples the AC input signal to the transistor while isolating the bias network from the signal source.
9. C2 (10 µF Output Coupling Capacitor): Blocks the DC collector voltage and allows only the amplified AC signal to reach the load.
10. R2 (10 kΩ Load Resistor): Represents the output load and receives the amplified signal.


Initially, the amplifier produced a distorted output due to improper biasing. To improve linearity, the bias network was modified by changing R5 from 100 kΩ to 47 kΩ and R6 from 22 kΩ to 10 kΩ. The emitter resistor was increased from 470 Ω to 1 kΩ to improve stability, while the collector resistor was reduced from 10 kΩ to 4.7 kΩ to obtain a better collector operating point. These changes established a suitable quiescent bias point, allowing the transistor to remain in the active region throughout the signal cycle
This was the initial circuit : -- 
<img width="2047" height="1143" alt="image" src="https://github.com/user-attachments/assets/1632f185-6550-42cf-96f3-fc454181a782" />

This is the final circuit
<img width="1271" height="697" alt="image" src="https://github.com/user-attachments/assets/c5dd66fb-ed06-4d61-88f7-17d1eedee120" />



## Calculations

Input voltage:

Vin = 10 mV = 0.01 V

Output voltage (from simulation):

Vout ≈ 1.6 V

Voltage Gain:

Av = Vout / Vin

Av = 1.6 / 0.01

Av ≈ 160

Therefore, the Class-A amplifier achieved a voltage gain of approximately **160 V/V**.

---

## Efficiency Calculation

From DC operating-point analysis:

VCC = 12 V

ICC = 1.611 mA

DC power consumed:

PDC = VCC × ICC

PDC = 12 × 1.611 mA

PDC = 19.33 mW

Output RMS voltage:

Vrms = 1.13 V

Load resistance:

RL = 10 kΩ

Output power:

Pout = Vrms² / RL

Pout = (1.13)² / 10000

Pout = 0.128 mW

Efficiency:

η = (Pout / PDC) × 100

η = (0.128 / 19.33) × 100

η = 0.66%

Therefore, the amplifier achieved an efficiency of approximately **0.66%**.

The efficiency of the amplifier is low because the transistor remains ON throughout the entire signal cycle and continuously consumes power from the supply. Most of this power is dissipated as heat, while only a small portion is delivered to the load. This is a common characteristic of Class-A amplifiers and is the trade-off for their high linearity and low distortion.


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

