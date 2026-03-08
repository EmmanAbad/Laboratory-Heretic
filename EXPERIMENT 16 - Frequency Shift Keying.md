# EXPERIMENT 16 - Frequency Shift Keying :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Frequency Shift Keying (FSK), also referred to as binary frequency shift keying (BFSK), is a digital modulation scheme that utilizes frequency modulation (FM) to transmit digital data within an allocated portion of the radio-frequency spectrum. This technique leverages the inherent noise immunity of FM over AM, as FSK receivers can use a limiter circuit to remove amplitude variations caused by noise without degrading the recovered message. During the modulation process, the FSK signal switches between two distinct frequencies based on the input digital data: a "space frequency," which typically corresponds to logic-0s and is lower than the nominal carrier frequency, and a "mark frequency," which corresponds to logic-1s and is higher than the nominal carrier. While the modulator itself does not output a signal at the carrier frequency, this nominal reference is used to define the shift between the two logic-dependent states.
</p>

<img width="342" height="232" alt="image" src="https://github.com/user-attachments/assets/639f66db-323f-4796-ae67-f54a7497cab7" />


---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Frequency Shift Keying (FSK) is a fundamental digital modulation scheme where the frequency of a continuous carrier wave is varied in accordance with a digital binary signal. This experiment explores the complete communication lifecycle of an FSK signal—from generation via a Voltage Controlled Oscillator (VCO) to its eventual reconstruction using filtering and comparator circuits.
</p>

---

### Objectives
* To grasp the core concepts of FSK as a method for digital data modulation.
* To produce an FSK signal by driving a VCO with a digital sequence.
* To examine FSK waveforms and their frequency characteristics using an oscilloscope.
* To implement demodulation through low-pass filtering and envelope detection.
* To restore the final digital output using a comparator circuit.
  
---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* three Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: FSK Signal Generation**
1. Initialize the oscilloscope with DC coupling on both channels and set the trigger to External (HF Reject).
2. Configure the VCO by setting the Range to LO, the Gain to midpoint, and the Frequency Adjust to approximately one-quarter.
3. Set the Sequence Generator DIP switches to 00 to produce the baseband digital data.
4. Wire the modules according to the FSK generation diagram, connecting the digital data to the VCO input.
5. Activate the trainer and use the oscilloscope to observe how the output frequency shifts in relation to the digital input.

<img width="444" height="262" alt="image" src="https://github.com/user-attachments/assets/3bf85b41-a0ca-4f36-a318-fd716f499e91" />


**Procedure – Part B: Demodulation via Filtering**
1. Integrate the Tunable Low-Pass Filter (LPF) into the existing circuit setup.
2. Adjust the VCO Frequency Control to position 2 and set the LPF Gain and Cut-off controls fully clockwise.
3. Connect the FSK output to the LPF input as shown in the demodulation block diagram.
4. Slowly decrease the LPF cut-off frequency to attenuate the higher frequency component of the signal.
5. Analyze the resulting "burst" waveform on the oscilloscope, comparing the filtered output to the original data.

<img width="481" height="239" alt="image" src="https://github.com/user-attachments/assets/8cbcebf4-54fd-4bc6-958d-cd78e528464b" />

<img width="402" height="326" alt="image" src="https://github.com/user-attachments/assets/f31128b7-7890-4f78-9cbe-777c71f1ee39" />


**Procedure – Part C: Digital Signal Restoration**
1. Incorporate the Comparator module into the circuit, receiving the signal from the envelope detector.
2. Set the Variable DC reference voltage to the midpoint to establish a switching threshold.
3. Monitor the comparator’s output on the oscilloscope alongside the original digital source.
4. Fine-tune the reference voltage until the output displays a stable, sharp digital square wave.

<img width="513" height="228" alt="image" src="https://github.com/user-attachments/assets/770c7691-6d5b-414c-b9ec-ad65359859bb" />

**Example Output**

<img width="557" height="288" alt="image" src="https://github.com/user-attachments/assets/f331b9be-ad8f-49b1-9ca9-820f6ac60b19" />
<img width="820" height="559" alt="image" src="https://github.com/user-attachments/assets/5663ccb3-33e7-40c0-bd28-138c1a595f69" />
<details><summary><b>[Reference]</b></summary><br>https://pysdr.org/content/digital_modulation.html#frequency-shift-keying-fsk<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;In this experiment, the process of generating an FSK signal through a Voltage Controlled Oscillator (VCO) demonstrated that digital data can be effectively transmitted by toggling between a high-frequency "Mark" and a lower-frequency "Space" state. The demodulation phase highlighted how a tunable low-pass filter can isolate these specific frequency components, essentially transforming the frequency-shifted signal into a series of amplitude bursts that represent the original data. Finally, the use of a comparator proved essential for signal restoration, as it utilized a reference threshold to convert the smoothed, analog-like transitions from the filter back into a sharp, clean digital square wave.
</p>

---

### Questions and Answers 
**Question 1 — What is the name for the VCO output frequency that corresponds with logic-1 in the digital data?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The frequency representing a logic-high state is formally known as the Mark Frequency.
</p>

**Question 2 — What is the name for the VCO output frequency that corresponds with logic-0 in the digital data?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The frequency representing a logic-low state is formally known as the Space Frequency.
</p>

**Question 3 — Which of the two frequencies is higher? Explain.**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The Mark Frequency is typically the higher of the two, as the higher control voltage from a logic-1 input increases the oscillation rate of the VCO.
</p>

**Question 4 — Which of the FSK signal’s two sinewaves does the filter select?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The filter is tuned to isolate the higher frequency (Mark) component, allowing it to pass while blocking the lower frequency.
</p>

**Question 5 — What does the filtered FSK signal look like?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;It appears as a series of sinusoidal bursts; the signal is prominent when the Mark frequency is active and nearly zero when the Space frequency is active.
</p>

**Question 6 — What component can be used to clean up the recovered digital signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;A Comparator is utilized to transform the smoothed analog pulses back into sharp digital transitions. that limit.
</p>

**Question 7 — How does the comparator convert slow-rising voltages into sharp transitions?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;By comparing the input to a fixed threshold; the moment the voltage crosses that limit, the output instantly snaps between rail voltages, eliminating gradual edges.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This experiment highlighted the role of frequency variation in carrying digital information. It successfully demonstrated that complex digital signals can be recovered using relatively simple analog components like filters and comparators. Key takeaways include the identification of Mark and Space frequencies and the necessity of signal conditioning (restoration) to ensure data integrity at the receiver.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The laboratory session successfully validated the process of Frequency Shift Keying. By utilizing a VCO for modulation and a combination of filtering and threshold detection for demodulation, the original digital sequence was accurately reconstructed. This reinforces the effectiveness of FSK in environments where frequency-based data transmission is more robust than amplitude-based methods.
</p>
