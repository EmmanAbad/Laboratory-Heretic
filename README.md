# Laboratory-Heretic
### Laboratory #3 (Experiment 15-20) :page_facing_up: 
### Introduction:
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Digital modulation is the process of mapping binary data onto an analog carrier wave for transmission across physical media. By altering the amplitude, frequency, or phase of a carrier, information can be sent efficiently over a distance. These experiments demonstrate the "lifecycle" of a digital signal, covering its generation, modulation, transmission through a simulated medium, and final restoration at the receiver.
</p>

---

### Objectives:
* Generate various digital modulation signals including ASK, FSK, BPSK, QPSK, and DSSS.
* Observe and analyze the functional relationship between binary input data and the resulting modulated waveforms.
* Execute signal demodulation using techniques such as envelope detection, filtering, and product detection.
* Restore distorted analog signals back into clean digital square waves using comparator circuits.
* Evaluate system performance against interference, synchronization requirements, and spectral efficiency.

---

### Explanations of Experiments:
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The laboratory series encompasses the end to end lifecycle of digital communication, transitioning from basic amplitude and frequency keying to advanced spread spectrum and software defined radio techniques. By utilizing the Emona Telecoms Trainer 101, the experiments demonstrate how binary data is mapped onto analog carriers through various modulation schemes like ASK, FSK, BPSK, and QPSK, as well as the specialized energy distribution of DSSS. Each session emphasizes the physical challenges of signal transmission, such as bandwidth limitations and noise, while proving that information can be accurately recovered through hardware processes like synchronous detection, filtering, and comparator based reconstruction. Ultimately, the work bridges the gap between traditional hardware receivers and flexible, code based SDR architectures by exploring undersampling and digital signal processing fundamentals.
</p>

---

<details>
<summary>EXPERIMENT 15 - Amplitude Shift Keying</summary> 

**INTRODUCTION**
* Amplitude Shift Keying, often referred to as On-Off Keying (OOK), is a basic digital modulation technique where the binary bitstream controls the carrier amplitude. In this scheme, the carrier is transmitted at full power for a logic high and is completely suppressed for a logic low. This experiment focuses on creating the ASK envelope and using an envelope detector to strip the carrier away for data recovery.

**EXPLANATION**
* The experiment highlights how digital information can be mapped onto an analog carrier for transmission. It provides a practical look at how hardware components like rectifiers and filters act as an envelope detector to recover the message. A key lesson is the necessity of using a comparator to fix signal degradation, as filtering inherently rounds the edges of the digital pulses.

<details><summary><b>[View EXPERIMENT 15 - Amplitude Shift Keying Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2015%20-%20Amplitude%20Shift%20Keying.md<br></details>

</details>

---

<details>
<summary>EXPERIMENT 16 - Frequency Key Shifting</summary> 

**INTRODUCTION**
* Frequency Shift Keying is a modulation method where the frequency of a carrier wave is varied in accordance with digital binary signals. The system toggles between a "Mark" frequency for logic 1 and a "Space" frequency for logic 0. This experiment explores the FM-based nature of FSK, which provides better noise immunity than amplitude-based methods because the receiver can ignore amplitude fluctuations.
  
**EXPLANATION**
* This laboratory session demonstrated the role of frequency variation in carrying digital information. It successfully showed that complex digital signals can be recovered using relatively simple components like filters and threshold detectors. A major takeaway was the importance of signal conditioning to ensure data integrity, especially in identifying the distinct frequency shifts at the receiver.

<details><summary><b>[View EXPERIMENT 16 - Frequency Key Shifting Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2016%20-%20Frequency%20Shift%20Keying.md<br></details>

</details>

---

<details>
<summary>EXPERIMENT 17 - Binary Phase Shift Keying</summary> 

**INTRODUCTION**
* Binary Phase Shift Keying is a sophisticated modulation scheme where the phase of a constant-amplitude carrier is shifted by 180 degrees to represent binary data. Unlike ASK or FSK, BPSK maintains a constant frequency and amplitude, making it highly robust against noise. The experiment examines the circuitry required to modulate and then demodulate these signals using product detection.

**EXPLANATION**
* The experiment highlights the efficiency of phase-based communication. It shows that while the carrier frequency and amplitude remain static, the information encoded in the phase shifts provides a resilient way to transmit data. Seeing the rounded output of the low-pass filter taught a practical lesson on how bandwidth limitations affect signal integrity and how a comparator can restore that accuracy.

<details><summary><b>[View EXPERIMENT 17 - Binary Phase Shift Keying Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2017%20-%20Binary%20Phase%20Shift%20Keying.md<br></details>

</details>

---

<details>
<summary>EXPERIMENT 18 - Quadrature Phase Shift Keying</summary> 

**INTRODUCTION**
* Quadrature Phase Shift Keying is an advanced variation of BPSK that transmits two bits per symbol by utilizing four distinct phase states. By employing orthogonal carriers (90 degrees apart), QPSK can transmit at twice the rate of BPSK within the same radio-frequency bandwidth. This experiment explores serial-to-parallel conversion and the summation of orthogonal carriers.

**EXPLANATION**
* This session illustrated the transition from serial data to a multi-phase modulated signal. The primary takeaway is that QPSK achieves higher data density through orthogonality, allowing two independent signals to occupy the same frequency space. It also highlighted that precise phase synchronization at the receiver is the most critical factor for successfully separating overlapping signals.

<details><summary><b>[View EXPERIMENT 18 - Quadrature Phase Shift Keying Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2018%20-%20Quadrature%20Phase%20Shift%20Keying.md<br></details>

</details>

---

<details>
<summary>EXPERIMENT 19 - DSSS Modulation and Demodulation</summary> 

**INTRODUCTION**
* Direct Sequence Spread Spectrum is a secure modulation technique that replaces a standard carrier with a high-speed pseudo-noise (PN) sequence. This spreads the message energy across a wide frequency spectrum, making the signal look like low-level noise to unauthorized users and providing resistance to jamming. The experiment focuses on the correlation between identical PN codes for data recovery.

**EXPLANATION**
* The most critical takeaway was the absolute necessity of perfect synchronization. Without an exact matching PN sequence at the receiver, the data remains indistinguishable from background noise. The experiment also provided a practical understanding of how spreading the signal energy makes it resilient against interference, as the despreading process collapses the message while further spreading any jamming signals.

<details><summary><b>[View EXPERIMENT 19 - DSSS Modulation and Demodulation Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2019%20-%20DSSS%20Modulation%20and%20Demodulation.md<br></details>

</details>

---

<details>
<summary>EXPERIMENT 20 - Undersampling in SDR</summary> 

**INTRODUCTION**
* Software Defined Radio (SDR) shifts the decoding process from rigid hardware to flexible software. To handle high-frequency signals without requiring extreme sampling rates, SDR uses "undersampling" or bandpass sampling. This experiment investigates how intentionally causing aliasing can shift a high-frequency carrier down to baseband, allowing for efficient digital processing.

**EXPLANATION**
* The experiment highlights a shift in traditional sampling perspectives. While standard sampling requires rates exceeding twice the highest frequency, SDR leverages the fact that radio signals are bandwidth-limited. Seeing a 2 kHz signal emerge from a 100 kHz carrier using a lower sampling rate clarified how aliasing can be used as a productive tool rather than just a source of distortion.

<details><summary><b>[View EXPERIMENT 20 - Undersampling in SDR Details]</b></summary><br>https://github.com/EmmanAbad/Laboratory-Heretic/blob/main/EXPERIMENT%2020%20-%20Undersampling%20in%20SDR.md<br></details>

</details>

---

### Learnings: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The laboratory sessions provided a practical understanding of how hardware constraints affect digital integrity. A key takeaway is that while modulation and filtering often cause signal rounding and distortion, specialized components like comparators are essential for restoring the sharp transitions required for accurate data reception. Furthermore, the experiments emphasized the critical role of synchronization, especially in DSSS and QPSK, where precise timing and phase alignment are necessary to successfully recover the original message from noise or multiplexed streams.
</p>

---

### Conclusions:
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The successful execution of these experiments validates the theoretical advantages of modern digital modulation. From the simplicity of ASK to the robustness of DSSS and the efficiency of QPSK, the study confirms that digital communication is a balance of managing electromagnetic geometric relationships and hardware limitations. These methodologies remain foundational to the design of resilient wireless networks and secure telecommunication links.
</p>
