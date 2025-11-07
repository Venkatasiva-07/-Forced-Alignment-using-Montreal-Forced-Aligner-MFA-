# Forced Alignment using Montreal Forced Aligner (MFA)

> A complete step-by-step guide for running forced alignment using the **Montreal Forced Aligner (MFA)**.  
> This repository demonstrates how to install MFA, prepare your dataset, run alignment, and inspect `.TextGrid` outputs.

---

## 🧩 Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation](#installation)
3. [Downloading MFA Models](#downloading-mfa-models)
4. [Preparing Your Dataset](#preparing-your-dataset)
5. [Running Alignment](#running-alignment)
6. [Example Workflow](#example-workflow)
7. [Troubleshooting](#troubleshooting)
8. [Screenshots / Demo](#screenshots--demo)

---

## 🧠 Prerequisites
- **OS:** Windows, macOS, or Linux  
- **Python:** 3.8 – 3.11  
- **Conda / Miniconda** installed  
- **Optional:** `ffmpeg` (to convert `.mp3` / `.m4a` to `.wav`)

---

## ⚙️ Installation

1. Open **Anaconda Prompt** or **Terminal**  
2. Activate base environment  
   ```bash
   conda activate base

3.Create new conda environment
  ```bash
  Create new conda environment
  conda activate mfa-test
4.Install MFA from conda-forge
  ```bash
  conda install -c conda-forge montreal-forced-aligner kalpy kaldi=*=cpu* -y
5.Check MFA version
 ```bash
 mfa --version
# Example output: 3.3.8
📥 Downloading MFA Models

List and download models inside your MFA environment:
```bash
# List available acoustic models
mfa model download acoustic

# Download a specific acoustic model
mfa model download acoustic english_us_arpa

# List and download dictionary models
mfa model download dictionary
mfa model download dictionary english_us_arpa

#🗃 Preparing Your Dataset

Expected folder structure:
dataset/
├── wavs/
│   ├── file1.wav
│   ├── file2.wav
│   └── ...
└── texts/
    ├── file1.txt
    ├── file2.txt
    └── ...

Rules

.wav audio (16 kHz mono preferred)

Transcript files must match filenames (file1.wav ↔ file1.txt)

Transcript text should be clean (no punctuation)

Example transcript (file1.txt):

IIITH THANK YOU

▶️ Running Alignment

Run MFA alignment:

mfa align dataset english_us_arpa english_us_arpa aligned_output/


Arguments:

dataset → path to dataset folder

english_us_arpa → dictionary + acoustic model

aligned_output → folder to store .TextGrid results

🧾 Example Workflow
# Activate environment
conda activate mfa-test

# Download models
mfa model download acoustic english_us_arpa
mfa model download dictionary english_us_arpa

# Run alignment
mfa align dataset english_us_arpa english_us_arpa aligned_output/


Expected output:

Aligning files...
file1.wav → file1.TextGrid
file2.wav → file2.TextGrid
Alignment complete. Results saved in aligned_output/

📸 Screenshots / Demo

Add .png or .gif files here:

Screenshot of Praat showing .TextGrid alignment

Example waveform with phoneme boundaries

🏫 References

Montreal Forced Aligner (GitHub)

Official Documentation

✨ Author: Venkata Siva
🎓 Prepared for IIIT Hyderabad Internship (Speech & AI/ML)
🗓️ Date: November 2025
