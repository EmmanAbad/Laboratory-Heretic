# EXPERIMENT 17 - Binary Phase Shift Keying :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Binary Phase Shift Keying (BPSK) is a digital modulation technique that transmits data by altering the phase angle of a carrier wave rather than its amplitude or frequency. In this method, a logic transition in the digital input causes the carrier to undergo a 180° phase shift, effectively inverting its polarity. For example, a logic 1 might start at a positive peak while a logic 0 starts at a negative peak. Mathematically, BPSK functions similarly to Double-Sideband Suppressed Carrier (DSBSC) modulation with a bipolar digital message. Because the carrier amplitude remains constant, BPSK offers superior resistance to noise and better error performance compared to techniques like ASK or FSK.
</p>

<img width="340" height="198" alt="image" src="https://github.com/user-attachments/assets/af552ceb-b6d4-4dc8-955f-a3023d54fc55" />

---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Binary Phase Shift Keying (BPSK) is a sophisticated digital modulation scheme where the phase of a constant-amplitude carrier signal is shifted to represent binary data. By transitioning the carrier phase by 180° for every bit change, BPSK achieves higher noise immunity than amplitude-based methods. This experiment explores the circuitry required to modulate, detect, and clean these signals using a product detector and comparator.
</p>

---

### Objectives
* Generate a Binary Phase Shift Keying (BPSK) modulated signal.
* Identify the 180° phase reversals that occur during digital data transitions.
* Demodulate a BPSK signal using a product detector.
* Recover and restore the digital signal using a comparator circuit.
* Understand the relationship between BPSK modulation and Double-Sideband Suppressed Carrier (DSBSC) modulation.
  
---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* three Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: BPSK Signal Generation**
1. Initialize the Emona Trainer and configure the oscilloscope with an External (EXT) trigger and DC input coupling.
2. Set the Sequence Generator DIP switches to 00 and sync its clock to the Master Signals 8 kHz output.
3. Connect the Sequence Generator output to the Multiplier's X input and the 100 kHz sine wave to the Y input.
4. Use the Dual Mode on the oscilloscope to view the digital data signal and the BPSK waveform simultaneously.
5. Apply Sweep Magnification to observe the 180° phase inversion occurring at each digital transition point.

<img width="478" height="304" alt="image" src="https://github.com/user-attachments/assets/1ad69cf1-920e-47c0-8754-f54d42fec165" />

**Procedure – Part B: Demodulation via Product Detector**
1. Set the Tunable Low-pass Filter's cut-off frequency to its maximum clockwise position and the gain to the midpoint.
2. Integrate a second Multiplier and the Low-pass Filter into the circuit to construct a product detector.
3. Multiply the incoming BPSK signal with the reference carrier to initiate the demodulation process.
4. Pass the resulting signal through the Low-pass Filter to remove high-frequency components and isolate the baseband data.
5. Observe the recovered waveform and compare its rounded edges to the original sharp digital signal.

<img width="458" height="213" alt="image" src="https://github.com/user-attachments/assets/f55e751a-daf0-432a-8101-4d13109ea76f" />

**Procedure – Part C: Digital Signal Restoration**
1. Route the output of the Low-pass Filter directly into the input of the Comparator module.
2. Connect the Variable DC Voltage module to the Reference (REF) input of the comparator.
3. Adjust the DC control to set a threshold voltage that allows the comparator to trigger correctly.
4. Monitor the comparator output to see the conversion of the rounded analog signal back into a clean square wave.
5. Fine-tune the reference voltage until the restored digital signal closely matches the original data stream.

<img width="476" height="226" alt="image" src="https://github.com/user-attachments/assets/a9cbe209-cf45-4078-a96e-4ea78533c9d9" />

**Example Output**

<img width="550" height="173" alt="image" src="https://github.com/user-attachments/assets/88abea36-929d-4f19-a8b6-0aae4935cd75" />
<img width="960" height="96" alt="image" src="https://github.com/user-attachments/assets/fc5153ad-c22f-4640-9d85-4b1c93261b3d" />
<details><summary><b>[Reference]</b></summary><br>https://pysdr.org/content/digital_modulation.html#phase-shift-keying-psk<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The procedural workflow of this experiment illustrates the "lifecycle" of a digital signal in a telecommunications system. By moving from generation to modulation, then through a simulated "receiver" (the product detector), and finally to a restoration stage, the procedure clarifies that communication requires managing distortions introduced by hardware limits. The step-by-step transition from a pure sine wave to a phase-inverted wave and back to a clean square wave reinforces how each component—from the multiplier to the comparator—is vital for maintaining data fidelity.
</p>

---

### Questions and Answers 
**Question 1 — What happens to the BPSK signal when the data stream experiences a logic transition?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Upon a logic transition, the BPSK signal undergoes a total phase reversal of 180°, which causes the sinusoidal carrier waveform to invert its polarity.
</p>

**Question 2 — What characteristic of the BPSK signal suggests that it behaves like a DSBSC signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The BPSK signal behaves like DSBSC because its envelope follows the digital data pattern and crosses zero at the exact moments the polarity changes.
</p>

**Question 3 — Why is the recovered digital signal not an exact replica of the original signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The recovery process involves a low-pass filter that removes high-frequency harmonics of the square wave, resulting in rounded edges and minor distortion.
</p>

**Question 4 — What component can be used to clean up the recovered digital signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;A comparator circuit or a Schmitt trigger is utilized to interpret the rounded analog signal and restore it into a clean, binary square wave.
</p>

**Question 5 — Why does adjusting the DC reference voltage affect the shape of the output digital signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The DC voltage sets the switching threshold; because the recovered signal has gradual transitions, changing the threshold shifts the timing of the comparator's output, altering the pulse width.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This experiment highlights the practical efficiency of phase-based communication. I learned that while the carrier frequency and amplitude remain static, the information encoded in the 180° phase shifts provides a robust way to transmit data. Seeing the rounded output of the low-pass filter was a practical lesson in how bandwidth limitations and filtering affect signal integrity. Furthermore, the use of a comparator demonstrated how hardware can compensate for these physical constraints to restore digital accuracy.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;In conclusion, BPSK is a highly effective digital modulation technique that utilizes carrier phase inversion to represent binary states. The experiment successfully demonstrated that while demodulation via a product detector initially yields a distorted signal due to necessary filtering, a comparator circuit can effectively reconstruct the original digital sequence. This confirms BPSK's reliability and its foundational role in modern digital telecommunications systems due to its robustness against noise.
</p>
