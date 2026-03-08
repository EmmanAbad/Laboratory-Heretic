# EXPERIMENT 20 - Undersampling in SDR :page_facing_up: 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Software Defined Radio (SDR) represents a paradigm shift in electronic communications by moving away from hardware specific receivers that are often rendered obsolete by new innovations. Traditional systems for formats like AM, FM, or cellular signals require dedicated and rigid hardware. However, SDR utilizes a single wideband tuner that converts radio signals to digital data. By shifting the decoding process to software, the system achieves unprecedented flexibility. This allows it to support virtually any existing or future modulation scheme, such as FSK, ASK, or DSSS, simply by updating the running program rather than replacing physical components.
</p>

<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;To handle high frequency signals like those used in modern cell phones, SDR employs a technique known as undersampling to bypass the traditional Nyquist requirement. While the Nyquist Shannon sampling theorem generally suggests sampling at twice the highest frequency, which would require a daunting 4.8GHz rate for a 2.4GHz signal, this rule primarily targets baseband signals starting at DC. Because radio communications are bandwidth limited and lack low frequency components, Shannon’s Information Theorem allows for information capture at a rate relative to the signal’s bandwidth rather than its carrier frequency. Consequently, a 2.4GHz carrier with a 30kHz bandwidth can be effectively sampled at just 60kHz. This significantly reduces the computational load while retaining all essential data.
</p>

---

### Introduction 
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;This experiment explores the practical implementation of undersampling within Software Defined Radio (SDR) architectures. By utilizing a bandwidth-limited Double Sideband Suppressed Carrier (DSBSC) signal, the study demonstrates how high-frequency signals can be translated to baseband without traditional mixing. The process relies on the Nyquist criterion for bandpass signals, showing that sampling rates based on signal bandwidth, rather than the maximum carrier frequency, are sufficient for accurate data recovery.
</p>

---

### Objectives
* Configure and observe a bandwidth-limited Double Sideband Suppressed Carrier (DSBSC) signal.
* Demonstrate the direct down-conversion of high-frequency signals using the principle of undersampling.
* Examine the mathematical and physical relationship between sampling frequency, carrier frequency, and the resulting baseband output.
  
---

### Equipment
* Emana Telecoms-Trainer 101 (plus power-pack)
* Dual channel 20MHz oscilloscope
* two Emano Telecoms Trainer 101 oscilloscope leads
* assorted Emona Telecoms-Trainer 101 patch leads

---

**Procedure – Part A: Setting Up a Bandwidth-Limited Signal**
1. Construct the circuit according to the "Setting up a Bandwidth-limited Signal" block diagram provided in the manual.
2. Connect a 2 kHz sine wave message signal and a 100 kHz sine wave carrier signal to the inputs of the Multiplier module.
3. Utilize the Multiplier to generate a Double Sideband Suppressed Carrier (DSBSC) modulated waveform.
4. Route the Multiplier output to Channel 1 of the oscilloscope to visualize the modulated signal.
5. Analyze the waveform to identify characteristic phase reversals and measure the frequency components.
6. Record the total bandwidth of the generated signal for use in the next phase of the experiment.

<img width="340" height="276" alt="image" src="https://github.com/user-attachments/assets/d065a7f6-a72b-4b42-ae51-86b5643e2f01" />

**Procedure – Part B: DSSS with Speech Input**
1. Input the DSBSC signal from Part A into the Dual Analog Switch module to initiate the sampling process.
2. Set the sampling clock frequency using either the VCO module or the Master Signals module.
3. Direct the sampled output into the Baseband Low-Pass Filter (LPF) to isolate the original message.
4. Monitor the filtered output on Channel 2 of the oscilloscope to view the recovered signal.
5. Compare the reconstructed waveform against the original 2 kHz message signal to check for accuracy.
6. Vary the sampling frequency to observe how different undersampling rates impact the reconstruction quality.

| Components due to DC | Components due to fs | Components due to 2fs | Components due to 3fs |
| :--- | :--- | :--- | :--- |
| 98k & 102k | Diff: 48k & 52k | Diff: 198k & 202k | Diff: 348k & 352k |
| 98k & 102k | Sum: 248k & 252k | Sum: 398k & 402k | Sum: 548k & 552k |

<img width="524" height="349" alt="image" src="https://github.com/user-attachments/assets/66b0c15b-50b0-4615-88bb-d5f3845922a6" />

**Procedure – Part C: Synchronisation**
1. Locate the VCO module on the trainer and toggle its Range control to the LO position.
2. Adjust the VCO module's Frequency Adjust knob so it is positioned roughly in the middle of its travel.
3. Configure the oscilloscope's Mode control to display only Channel 1.
4. Connect the oscilloscope's Channel 1 input directly to the Digital output of the VCO module.
5. Calibrate the VCO module's Digital output to exactly 8.333 kHz by adjusting the signal's period to 120 $\mu$s using the formula $P = \frac{1}{f}$.
6. Move the Channel 1 input back to the Master Signals module's 2 kHz SINE output and readjust the scope to view two or three cycles of the original and recovered messages.

**Example Output**

<img width="572" height="538" alt="image" src="https://github.com/user-attachments/assets/d0022298-acc3-4e35-8416-e5b5867e5887" />
<details><summary><b>[Reference]</b></summary><br>https://www.edn.com/sampling-and-aliasing/#google_vignette<br></details>

**Learning**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The procedural steps reveal that the transition from a high-frequency modulated signal to a reconstructed baseband signal is heavily dependent on the filtering stage. While the sampling process creates the necessary aliases, the Baseband LPF acts as the critical component for isolating the intended message. This workflow emphasizes that successful SDR communication is not just about the sampling rate, but about the precise coordination between the sampling clock and the subsequent filtering hardware.
</p>

---

### Questions and Answers 
**Question 1 — For the given inputs to the Multiplier module, what are the frequencies of the two sine waves that form the DSBSC signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The DSBSC signal is composed of the sum and difference frequencies of the carrier ($f_c$) and message ($f_m$). With a 100 kHz carrier and a 2 kHz message, the Upper Sideband (USB) is 102 kHz ($100 + 2$) and the Lower Sideband (LSB) is 98 kHz ($100 - 2$).
</p>

**Question 2 — What is the bandwidth of the DSBSC signal?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The bandwidth is calculated as the difference between the upper and lower sidebands, which equals twice the message frequency ($2 \times f_m$). For this experiment, the bandwidth is 4 kHz.
</p>

**Question 3 — What is the significance of the signal at the output of the Baseband LPF?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The output represents the successfully recovered 2 kHz message. It proves that a high-frequency signal can be shifted to baseband via undersampling, as the filter removes unwanted high-frequency aliases and keeps the desired low-frequency component.
</p>

**Given a sampling frequency ($f_s$) of X, why is the signal still recovered?**
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;Recovery is possible because the Nyquist criterion for bandpass signals only requires $f_s$ to be greater than twice the signal bandwidth ($2 \times BW$), rather than twice the maximum frequency. This allows the information to be preserved in the signal aliases.
</p>

---

### Learnings
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The experiment highlights a shift in traditional sampling perspectives. While baseband sampling requires rates exceeding twice the highest frequency, SDR applications leverage bandpass sampling to reduce hardware demands. Seeing the 2 kHz signal emerge from a 100 kHz carrier using a lower sampling rate clarifies how aliasing can be used as a tool rather than being treated as a distortion.
</p>

---

### Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;The study successfully confirms that undersampling is a viable method for frequency down-conversion. By satisfying the bandwidth-related Nyquist condition, the system reconstructed the original data without the need for complex analog mixers. This confirms the efficiency of SDR architectures in modern telecommunications.
</p>
