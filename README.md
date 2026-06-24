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
<img width="770" height="258" alt="image" src="https://github.com/user-attachments/assets/f7346924-9fa2-46f8-8c1e-5460e483d51b" />

### Voltage Gain Calculation

### Voltage Gain Calculation

The input signal applied to the amplifier was:

[
V_{in} = 10mV = 0.01V
]

From transient simulation, the output voltage across the load resistor (R_2) was approximately:

[
V_{out} \approx 1.6V_{peak}
]

The voltage gain is therefore:

[
A_v = \frac{V_{out}}{V_{in}}
]

[
A_v = \frac{1.6}{0.01}
]

[
A_v \approx 160
]

Thus, the designed Class-A amplifier achieved a voltage gain of approximately **160 V/V**.

---

### Efficiency Calculation

From the DC operating point analysis:

[
V_{CC}=12V
]

[
I_{CC}=1.611mA
]

The DC power consumed from the supply is:

[
P_{DC}=V_{CC}\times I_{CC}
]

[
P_{DC}=12\times1.611mA
]

[
P_{DC}=19.33mW
]

The measured output voltage amplitude across the load resistor was approximately:

[
V_{out(peak)}=1.6V
]

Hence,

[
V_{out(rms)}=\frac{V_{out(peak)}}{\sqrt{2}}
]

[
V_{out(rms)}=\frac{1.6}{1.414}
]

[
V_{out(rms)}\approx1.13V
]

For the load resistance:

[
R_L=10k\Omega
]

The AC output power delivered to the load is:

[
P_{out}=\frac{V_{out(rms)}^2}{R_L}
]

[
P_{out}=\frac{(1.13)^2}{10000}
]

[
P_{out}\approx0.128mW
]

Therefore, the efficiency is:

[
\eta=\frac{P_{out}}{P_{DC}}\times100
]

[
\eta=\frac{0.128}{19.33}\times100
]

[
\eta\approx0.66%
]

The efficiency is low because the transistor remains biased in the active region throughout the entire input cycle and continuously draws power from the supply even when no signal is present. This is a characteristic drawback of Class-A amplifiers, although it provides excellent linearity and very low distortion.
