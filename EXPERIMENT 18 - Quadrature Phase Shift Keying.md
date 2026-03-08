# EXPERIMENT 18 - Quadrature Phase Shift Keying :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Quadrature Phase Shift Keying (QPSK) is a variation of Binary Phase Shift Keying (BPSK) that utilizes Double Sideband Suppressed Carrier (DSBSC) modulation to transmit digital data. While BPSK transmits one bit at a time, QPSK doubles this capacity by transmitting two bits per symbol. Although converting individual bits into bit-pairs effectively halves the data's bit rate, it offers a critical spectral advantage. Because QPSK requires only half the radio-frequency bandwidth of BPSK to transmit data reliably, it allows for more efficient use of the frequency spectrum and accommodates more users within the same channel.
</p>

<img width="488" height="320" alt="image" src="https://github.com/user-attachments/assets/114b413a-3c10-4777-9e5e-b937d58097bf" />

<img width="454" height="313" alt="image" src="https://github.com/user-attachments/assets/1c9329d7-47ea-401c-a75a-10e3cd76b9ee" />

---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Quadrature Phase Shift Keying (QPSK), a sophisticated digital modulation technique. QPSK is a cornerstone of modern telecommunications, doubling spectral efficiency by transmitting two bits per symbol through four distinct phase states of a single carrier frequency.
</p>

---

### Objectives
* Understand the fundamental principles of QPSK as a digital modulation technique.
* Observe the division of a serial data stream into parallel bit streams.
* Generate and combine two BPSK signals to create a single QPSK-modulated waveform.
* Analyze QPSK waveform characteristics using an oscilloscope.
* Explore phase discrimination techniques for signal recovery.
* Study the phase relationships between local and transmitted carrier signals.
  
---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* three Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: BPSK Signal Generation**
1. Initialize the Sequence Generator to create a serial digital data stream.
2. Route the serial data into the Serial-to-Parallel (S/P) Converter to split the stream into odd and even bit paths.
3. Connect these two parallel streams into separate Multiplier modules.
4. Apply a 100 kHz sine wave from the Master Signals module to both multipliers as a carrier.
5. Verify the production of two distinct BPSK-modulated signals ($PSK_1$ and $PSK_2$) via the oscilloscope.

<img width="456" height="266" alt="image" src="https://github.com/user-attachments/assets/58f62ccd-348e-4486-b754-f8090b568c0f" />

<img width="437" height="373" alt="image" src="https://github.com/user-attachments/assets/09e46fb1-6558-43bb-8105-1c8dfd1563a2" />

**Procedure – Part B: Formation of the QPSK Signal**
1. Feed the outputs of both multipliers ($PSK_1$ and $PSK_2$) into the Adder module.
2. Adjust the Adder Gain until the combined output reaches a stable 4 V peak-to-peak level.
3. Monitor the combined output on the oscilloscope to observe the resulting QPSK waveform.
4. Compare the phase transitions of the QPSK signal against the original individual BPSK components.
   
<img width="470" height="370" alt="image" src="https://github.com/user-attachments/assets/90bd5c0d-3eaf-462d-8bf7-e69691fc73a4" />

<img width="480" height="260" alt="image" src="https://github.com/user-attachments/assets/4a42ce9a-9f28-4ae5-81b0-5eed45ea0736" />

**Procedure – Part C: Phase Discrimination & Recovery**
1. Integrate a Phase Shifter module into the circuit, connected to the local carrier signal.
2. Pass the signal through a Product Detector followed by a Tunable Low-Pass Filter (LPF).
3. Manipulate the Phase Adjust control while monitoring the filtered output on the oscilloscope.
4. Identify the specific phase alignments that allow for the successful recovery of a single BPSK component.

<img width="413" height="240" alt="image" src="https://github.com/user-attachments/assets/fd486cb1-0c73-45da-a210-72363115b5a9" />

<img width="485" height="265" alt="image" src="https://github.com/user-attachments/assets/96788f27-57da-441c-b436-8ad02cfeb1d9" />

**Example Output**
<img width="1316" height="296" alt="image" src="https://github.com/user-attachments/assets/80cf9165-d7f9-46e5-94ac-d6b4a80fe58c" />
<details><summary><b>[Reference]</b></summary><br>https://pysdr.org/content/digital_modulation.html#quadrature-amplitude-modulation-qam<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The procedural flow of this experiment provides a practical roadmap for understanding signal multiplexing in the time and phase domains. By physically connecting modules to split data (Part A), combine waveforms (Part B), and then selectively filter them (Part C), the user learns that digital communication is not just about sending bits, but about managing the geometric relationships of electromagnetic waves. The hands-on adjustment of phase shifts demonstrates that "tuning" in digital systems is a precise mathematical alignment required to successfully disentangle multiplexed data streams.
</p>

---

### Questions and Answers 
**Question 1 — What is the relationship between the bit rate of the two digital signals and the bit rate of the Sequence Generator output?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The parallel streams operate at exactly half the bit rate of the original source because the S/P converter alternates bits between the two channels.
</p>

**Question 2 — What feature of the Multiplier output indicates that it is a BPSK signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The signal shows a constant amplitude, but a 180° phase reversal is clearly visible whenever the input digital data switches between high and low states.
</p>

**Question 3 — What type of signal is present at the Multiplier output?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The output is a BPSK-modulated carrier, which is mathematically identical to a Double Sideband Suppressed Carrier (DSBSC) signal.
</p>

**Question 4 — According to theory, what type of digital transmission is present at the Adder output?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The output is a QPSK-modulated signal created by the summation of two orthogonal BPSK carriers.
</p>

**Question 5 — Why does the waveform appear as a single sinewave even though it consists of two BPSK signals?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Since both BPSK signals utilize the same carrier frequency and are orthogonal (90° apart), they merge into a single sinusoidal wave that shifts between four phase states.
</p>

**Question 6 — What causes the 3-level and 4-level signals observed at the LPF output during phase adjustment?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;These multi-level patterns occur when the local carrier is misaligned, causing the demodulator to capture portions of both the In-phase and Quadrature components simultaneously.
</p>

**Question 7 — How many Phase Adjust positions produce a bipolar signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;There are two specific positions where the phase alignment is correct for recovering one of the two original BPSK components.
</p>

**Question 8 — What is the phase relationship between the local carrier and the carriers used to generate $PSK_1$ and $PSK_2$?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The local carrier must be perfectly phase-aligned with the specific transmitted carrier ($PSK_1$ or $PSK_2$) intended for recovery; notably, the two transmitted carriers are 90° apart.
</p>

**Question 9 — Why is the demodulator considered only half of a complete QPSK receiver?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This setup only recovers one data stream; a full receiver requires two parallel demodulation paths (In-phase and Quadrature) to extract both bit streams at once.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The experiment successfully illustrated the transition from serial data to a multi-phase modulated signal. Key takeaways include the realization that QPSK achieves higher data density by using orthogonality, allowing two independent BPSK signals to occupy the same frequency space without interference. Furthermore, the role of precise phase synchronization in the receiver was highlighted as the critical factor for separating these overlapping signals.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;In conclusion, QPSK modulation is an efficient method for doubling data throughput by mapping bit pairs to four specific carrier phases. Through the use of Serial-to-Parallel conversion and orthogonal carrier summation, the experiment proved that complex digital data can be transmitted and recovered reliably, provided the receiver utilizes accurate phase discrimination.
</p>
