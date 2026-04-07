# Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python

__Aim__:

To generate an FDM signal by multiplexing multiple baseband message signals on different carrier frequencies, transmit (sum) them, optionally add channel noise, then recover each message by bandpass filtering and coherent demodulation in Python (Google Colab). Observe time & frequency domain signals and measure recovery quality.


__Apparatus Required__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)


__Theory__:

FDM places different message signals in separate, non-overlapping frequency bands by modulating each message onto a distinct carrier frequency. The multiplexed signal is the sum of all modulated channels. At the receiver, bandpass filters (or tuned filters) isolate each channel; then each isolated carrier is demodulated (coherently multiplied by a synchronized carrier) and low-pass filtered to recover the original baseband.

__Procedure__:

1 — Imports and parameters

2 — Create message signals and carriers

3 — Modulate each message (standard AM DSB-SC) and form FDM signal

4 — Frequency domain (spectrum) of FDM signal

5 — (Optional) Add AWGN noise to FDM signal

6 — Receiver: isolate each channel with bandpass filter

7 — Demodulate each isolated channel (coherent) and low-pass filter to recover baseband

__Program__:

```
clc;
clear;
close;

Ac = 7.4;
Am = 3.7;

Fm1 = 166;
Fm2 = 140;

Fc1 = 1660;
Fc2 = 1400;

Fs = 16600;

t = 0:1/Fs:0.01;

// Message signals
m1 = Am*sin(2*%pi*Fm1*t);
m2 = Am*sin(2*%pi*Fm2*t);

subplot(5,1,1)
plot(t,m1)
title("Message Signal 1")

subplot(5,1,2)
plot(t,m2)
title("Message Signal 2")

// Modulated signals
s1 = (Ac + m1).*sin(2*%pi*Fc1*t);
s2 = (Ac + m2).*sin(2*%pi*Fc2*t);

subplot(5,1,3)
plot(t,s1)
title("Modulated Signal 1")

subplot(5,1,4)
plot(t,s2)
title("Modulated Signal 2")

// FDM signal
fdm = s1 + s2;

subplot(5,1,5)
plot(t,fdm)
title("FDM Signal")

xgrid();
```
__Output graph__:

<img width="1080" height="844" alt="image" src="https://github.com/user-attachments/assets/f422e231-0263-48d3-89d6-d501b0e3d111" />

<img width="1080" height="834" alt="image" src="https://github.com/user-attachments/assets/52a2bb3d-4f0a-47b5-89ba-6703617cad3f" />

<img width="1080" height="851" alt="image" src="https://github.com/user-attachments/assets/75c5e086-cfe9-4b84-a5a5-5ef50aea8f94" />


__Calculation__:

<img width="1080" height="1237" alt="image" src="https://github.com/user-attachments/assets/3c1f7256-4885-4d42-bfe2-24d270787f9f" />

__Result__:

Six different message signals were generated and modulated using FDM. All modulated signals were added to form a multiplexed FDM signal. Each message was successfully recovered using coherent demodulation followed by low-pass filtering. The plots confirmed accurate multiplexing and demultiplexing.
