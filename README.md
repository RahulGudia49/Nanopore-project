# Nanopore Synthetic Noise GUI

A MATLAB App Designer GUI for generating synthetic nanopore-like noise signals and comparing them with experimental data using FFT-based power spectrum matching.

This tool was developed for solid-state nanopore signal analysis, but the optimization-based spectrum matching approach can also be applied to other experimental noise signals.

---

## Features

- Generate synthetic nanopore-like signals
- Include white noise and 1/f noise using the model:
  
$$
S(f) = N_1 + \frac{N_2}{f}
$$

- Add nanopore event-like current blockades
- Load experimental data files
- Compare synthetic and experimental power spectra
- Optimize synthetic parameters to match the experimental spectrum
- Display best error and offset factor
- Export synthetic signals
- Export optimized parameters
- Export spectrum data
- Save generated plots

---

## Supported File Types

The GUI currently supports:

- `.bin`
- `.csv`
- `.xlsx`
- `.xls`
- `.abf`

For `.abf` files, the user must have an ABF reader such as `abfload.m` added to the MATLAB path.

---

## How It Works

The app generates a synthetic time-domain signal and compares it with experimental data.

The power spectrum is calculated using the FFT:

$$
S(f) = |FFT(x(t))|^2
$$

The normalized spectrum is calculated as:

$$
S_n(f) = \frac{S(f)}{S(0)}
$$

The error between the experimental and synthetic spectra is calculated as:

$$
\epsilon = \sum_f \left(S_n^{exp}(f) - S_n^{synth}(f)\right)^2
$$

The optimization routine adjusts the synthetic parameters to minimize this error.

---

## Parameters

| Parameter | Meaning |
|---|---|
| Fs | Sampling frequency of the synthetic signal |
| T | Duration of the synthetic signal in seconds |
| N1 | White noise strength |
| N2 | 1/f noise strength |
| Beta | Event amplitude or baseline-related parameter |
| lambda | Event decay/rate parameter |
| Nev | Number of nanopore-like events |
| Fs_e | Sampling frequency of the experimental signal |
| StartTime | Starting time of the experimental segment |
| Scale factor | Factor used to convert or scale experimental data |

---

## GUI Tabs

### 1. Synthetic Signal

This tab is used to generate the synthetic signal.

Inputs:

- Fs
- T
- N1
- N2
- Beta
- lambda
- Nev

Button:

- Generate Synthetic Signal

---

### 2. Experimental Data

This tab is used to upload and configure experimental data.

Inputs:

- File type
- Experimental sampling frequency `Fs_e`
- Start time
- Scale factor

Button:

- Load Experimental Data

---

### 3. Spectrum Matching

This tab compares the synthetic and experimental spectra.

Controls:

- Compare Spectra
- Optimize Parameters
- Plot type selection
- Axis type selection
- Best error display
- Offset factor display

---

### 4. Export

This tab saves output data.

Export options:

- Synthetic signal
- Optimized parameters
- Spectrum data
- Plot image

---


```bash
git clone https://github.com/your-username/Nanopore-Synthetic-Noise-GUI.git
