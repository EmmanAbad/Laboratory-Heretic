# EXPERIMENT 15 - Amplitude Shift Keying :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Modern telecommunications utilize multiplexing techniques like TDM and FDM to efficiently share limited channel resources among multiple users. Amplitude Shift Keying (ASK) is a specific digital modulation method where the carrier wave's amplitude is switched between a maximum state and a suppressed state based on the binary input. Because the carrier is effectively "switched" on for a logic high (1) and off for a logic low (0), the process is commonly known as On-Off Keying (OOK). This technique allows discrete digital information to be represented by the envelope of a continuous analog signal.
</p>

<img width="384" height="220" alt="image" src="https://github.com/user-attachments/assets/8b3ec219-133e-4f26-bb6a-8bcac389f0e4" />

---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Digital communication relies on the ability to translate binary data into analog signals for transmission across physical media. This experiment explores Amplitude Shift Keying (ASK), a fundamental modulation technique where the digital bitstream directly controls the amplitude of a high-frequency carrier wave to facilitate data transfer.
</p>

---

### Objectives
* Generate an ASK-modulated signal by interfacing digital data with an analog carrier.
* Analyze the functional relationship between the binary input and the resulting modulated waveform.
* Execute signal demodulation using an envelope detector and a comparator for digital restoration.
* Validate the operational mechanics of On-Off Keying (OOK) in a practical circuit.

---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* three Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: Generation of an ASK Signal**
1. Connect the Master Signals 2 kHz digital output to the Sequence Generator clock input.
2. Feed a 2 kHz sine wave into the Dual Analog Switch to be controlled by the digital sequence.
3. Use the oscilloscope to compare the digital data against the resulting ASK signal.
4. Replace the 2 kHz carrier with a 100 kHz signal from the VCO.
5. Adjust the vertical position to align the digital signal with the carrier envelope.

<img width="534" height="285" alt="image" src="https://github.com/user-attachments/assets/8ba069d5-3f0a-470d-bb9c-cb8c19900d9b" />

<img width="516" height="254" alt="image" src="https://github.com/user-attachments/assets/5eeee66e-3f49-4e1c-9c85-2909a8b2746c" />

**Procedure – Part B: Demodulation Using an Envelope Detector**
1. Configure the Tuneable LPF with gain and cut-off controls set fully clockwise.
2. Insert the Rectifier and Low-pass Filter into the signal path to form an envelope detector.
3. Compare the recovered waveform with the original digital signal on the oscilloscope.

<img width="455" height="214" alt="image" src="https://github.com/user-attachments/assets/d50e428c-5aa4-47cd-ae44-78076ed291c6" />

**Procedure – Part C: Restoration Using a Comparator**
1. Connect the filter output to the input of the Comparator module.
2. Set the Variable DCV to its midpoint to serve as the reference voltage.
3.  Tune the reference voltage until the comparator output perfectly replicates the original digital timing.

<img width="432" height="219" alt="image" src="https://github.com/user-attachments/assets/8f5ee704-3698-4010-8dcc-26d763e32e8e" />

**Example Output**
<img width="823" height="449" alt="image" src="https://github.com/user-attachments/assets/28ceed73-a188-45e3-af72-01f81e8e183d" />
<img width="810" height="281" alt="image" src="https://github.com/user-attachments/assets/9287d862-cd8c-4966-8e4b-ff016a4b71b3" />
<img width="827" height="449" alt="image" src="https://github.com/user-attachments/assets/102f1e9d-a2a0-48a7-acf4-344c3f1008b4" />
<details><summary><b>[Reference]</b></summary><br>https://pysdr.org/content/digital_modulation.html#amplitude-shift-keying-ask<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The sequence of procedures demonstrates the transition of a digital signal through an analog medium and its subsequent return to a digital state. In Part A, you learn the fundamental mechanics of On-Off Keying (OOK) by observing how a digital sequence physically gates a carrier wave, ensuring transmission only occurs during logic high states. Part B reveals the practical limitations of analog hardware, as the envelope detector successfully strips the carrier but introduces signal rounding due to the loss of high-frequency harmonics in the low-pass filter. Finally, Part C teaches the necessity of decision-making components in digital systems; the comparator acts as a restorative stage that uses a voltage threshold to convert those rounded, distorted transitions back into the sharp, precise square waves required for accurate data reception.
</p>

---

### Questions and Answers 
**Question 1 — What is the relationship between the digital signal and the presence of the carrier in the ASK signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The carrier is active during logic 1 and completely suppressed during logic 0.
</p>

**Question 2 — What is the ASK signal’s voltage when the digital signal is logic 0?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The amplitude drops to approximately 0 V, representing an absent carrier.
</p>

**Question 3 — What feature of the ASK signal indicates that it is an AM signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The carrier's envelope mimics the digital data's shape, showing the amplitude is modulated by the input.
</p>

**Question 4 — Why is the recovered digital signal not an exact copy of the original signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The low-pass filter removes high-frequency harmonics required for sharp square-wave corners, causing rounded transitions.
</p>

**Question 5 — What component can be used to clean up the recovered digital signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;A comparator circuit is used for restoration.
</p>

**Question 6 — How does the comparator convert the slow-rising voltages into sharp transitions?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;It triggers a high or low output based on a threshold voltage, instantly switching states when the input crosses that limit.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The experiment highlights how digital information can be successfully mapped onto an analog carrier for transmission. It provides a practical look at how hardware components like rectifiers and filters act as an "envelope detector" to strip away the carrier, while also teaching the necessity of comparators in overcoming the signal degradation inherent in analog filtering.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;In conclusion, the successful generation and recovery of an ASK signal validate the efficiency of On-Off Keying for digital communication. The process demonstrates that while modulation and filtering can distort signal integrity, specialized restoration circuits like comparators can accurately reconstruct the original data, ensuring reliable digital reception.
</p>
