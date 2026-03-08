# EXPERIMENT 19 - DSSS Modulation/Demodulation :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Direct Sequence Spread Spectrum (DSSS) is a variation of Double Sideband Suppressed Carrier (DSBSC) modulation that replaces a standard sinusoidal carrier with a pseudo-noise (PN) sequence pulse train. Because a pulse train consists of a fundamental frequency and an infinite series of harmonics, DSSS effectively modulates the message across a theoretically infinite number of sinusoidal carriers. This process distributes the message energy across a wide frequency spectrum, making the signal exceptionally resilient to interference or jamming. To compromise the data, an interloper would need to disrupt a significant portion of these numerous sidebands simultaneously.
</p>

<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;To successfully recover the original message, the receiver must utilize a product detector equipped with a local carrier that identically matches the transmitter PN sequence in both frequency and phase. If these sequences are not perfectly synchronized, the resulting output appears only as low level noise rather than a coherent signal. This requirement provides an inherent layer of security. Because the sequence length, measured in chips, determines the total number of possible code combinations, longer sequences make it mathematically nearly impossible for unauthorized parties to intercept or guess the correct sequence through trial and error.
</p>

---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This experiment explores the fundamental principles of Direct Sequence Spread Spectrum (DSSS). As a core pillar of modern wireless communication, DSSS is designed to enhance signal security and robustness by distributing a message's energy across a frequency band much wider than its original bandwidth. This laboratory exercise bridges the gap between basic modulation theory and complex signal protection by demonstrating how high-speed digital carriers, specifically Pseudo-Noise (PN) sequences, can make a signal appear noise-like to unauthorized users while remaining perfectly clear to a synchronized receiver. By simulating real-world conditions like signal jamming and sequence mismatch, the exercise reveals why this technology is indispensable for applications ranging from satellite communications to secure military links.
</p>

---

### Objectives
* Generate a functional DSSS signal using a multiplier and PN sequence.
* Analyze how a Pseudo-Noise (PN) sequence expands the bandwidth of a message.
* Compare the characteristics of DSSS modulation to DSBSC modulation.
* Demonstrate signal recovery using a synchronized product detector.
* Evaluate the system's performance against incorrect synchronization and deliberate jamming.
  
---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* three Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: BPSK Signal Generation**
1. Configure the oscilloscope to trigger from Channel 1 with HF Reject enabled.
2. Set the Sequence Generator switches to "00" and provide a 100 kHz clock.
3. Input a 2 kHz sinewave into Multiplier Input A and the PN sequence into Input B.
4. Adjust the timebase to view two cycles of the 2 kHz message.
5. Use DUAL mode to compare the message signal with the DSSS output.
6. Observe the phase reversals in the DSSS waveform relative to the message envelope.

<img width="309" height="282" alt="image" src="https://github.com/user-attachments/assets/faf02c8c-efba-4304-8d3a-69d3df0bcc88" />

**Procedure – Part B: DSSS with Speech Input**
1. Replace the 2 kHz sinewave input with the output from the Speech Module.
2. Adjust the oscilloscope timebase to 2 ms/div for better audio signal visualization.
3. Produce sound into the microphone to generate a dynamic message.
4. Observe how the high-frequency PN sequence spreads the complex speech patterns.
   
**Procedure – Part C: Interference Rejection (Jamming)**
1. Integrate a Phase Shifter module into the circuit, connected to the local carrier signal.
2. Pass the signal through a Product Detector followed by a Tunable Low-Pass Filter (LPF).
3. Manipulate the Phase Adjust control while monitoring the filtered output on the oscilloscope.
4. Identify the specific phase alignments that allow for the successful recovery of a single BPSK component.

<img width="493" height="531" alt="image" src="https://github.com/user-attachments/assets/e4695316-75e7-4b7a-b5e9-38870fe468db" />

**Procedure – Part D: Message Recovery (Demodulation)**
1. Use an Adder module to combine the DSSS signal with a VCO output signal.
2. Set the VCO to act as a narrowband jammer and increase its amplitude.
3. Monitor the distorted "jammed" waveform on the oscilloscope.
4. Pass the jammed signal through the product detector and LPF.
5. Observe how the despreading process recovers the message despite the interference.
6. Verify the system's robustness by varying the jammer's frequency and power.

<img width="485" height="232" alt="image" src="https://github.com/user-attachments/assets/bd372278-7889-498c-8bce-f22965e27857" />

**Example Output**
<img width="3143" height="884" alt="image" src="https://github.com/user-attachments/assets/afea55f5-9691-41c8-888c-0fd606e092bc" />
<img width="2935" height="1531" alt="image" src="https://github.com/user-attachments/assets/7316fde6-0444-4b4f-bdbc-28a06ba291b7" />
<details><summary><b>[Reference]</b></summary><br>https://www.mdpi.com/2313-7673/9/2/103<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The procedural flow of this experiment highlights the transition from basic signal theory to complex system resilience. By starting with a simple sine wave, one can clearly visualize the phase reversals that define the modulation. Moving into speech and jamming scenarios demonstrates the real-world utility of the hardware. This proves that the mathematical concept of correlation translates into a physical ability to reject noise. The step-by-step verification, from generation to despreading, reinforces that the effectiveness of DSSS lies entirely in the synchronized timing of the PN sequence.
</p>

---

### Questions and Answers 
**Question 1 — What feature of the Multiplier output indicates that it behaves like a DSBSC signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The output displays distinct phase reversals that occur at the transitions of the PN sequence. Meanwhile, the overall amplitude envelope mirrors the message signal, which is a behavior identical to DSBSC modulation.
</p>

**Question 2 — Why does the DSSS signal appear large on the oscilloscope even though it is expected to appear noise-like?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;In a laboratory environment, the signal is observed directly at the source without the transmission losses found in real systems. In practice, spreading power over a wide bandwidth drops the power spectral density below the noise floor.
</p>

**Question 3 — Why is there no output from the DSSS modulator when there is no speech input?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The multiplier performs a mathematical product. If the message input is zero during silence, the multiplication of zero and the PN sequence results in no output signal.
</p>

**Question 4 — What does the output of the Low-pass Filter look like when the correct PN sequence is used?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The filtered output successfully reconstructs the original message waveform. It appears as a clear 2 kHz sinewave or recognizable speech depending on the input.
</p>

**Question 5 — Why does using an incorrect PN sequence produce noise at the output?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Without a matching code, the despreading process fails to correlate. Instead, it spreads the energy further, leaving the LPF with only random components that look and sound like noise.
</p>

**Question 6 — Why does the jamming signal not prevent recovery of the original message?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The receiver's PN sequence collapses the message back to its original bandwidth while spreading the jammer energy wide. The LPF then blocks the spread-out interference while passing the recovered narrow message.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;I learned that DSSS functions by using a high-speed digital code to smear a signal across a wide frequency range. The most critical takeaway was the necessity of perfect synchronization. Without the exact matching PN sequence at the receiver, the data remains indistinguishable from background noise. I also gained a practical understanding of how this technology provides security and robustness in modern communication.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This experiment successfully validated the theoretical advantages of spread spectrum technology. By observing the modulation and demodulation process, the experiment proved that DSSS provides superior signal security and interference immunity. These characteristics confirm why DSSS is an essential component in the design of resilient wireless networks and secure communication links.
</p>
