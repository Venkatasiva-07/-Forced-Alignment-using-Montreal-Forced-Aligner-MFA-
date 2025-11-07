# -Forced-Alignment-using-Montreal-Forced-Aligner-MFA-
 forced alignment pipeline using the Montreal Forced  Aligner (MFA) tool


# Forced Alignment using Montreal Forced Aligner (MFA)

# Montreal Forced Aligner (MFA) Alignment Guide

This repository provides step-by-step instructions to install the **Montreal Forced Aligner (MFA)**, prepare your dataset, and run audio-text alignments. It includes example commands and expected outputs to help you get started quickly with speech alignment projects.



## TABLE OF CONTENTS
1.Prerequisites

2.Installation

3.Downloading MFA Models

4.Preparing Your Dataset

5.Running Alignment

6.Example Commands
## Prerequisites
Operating System: Windows, macOS, or Linux

Python: 3.8–3.11

Miniconda/Anaconda installed

Optional:

ffmpeg if you have audio in formats other than .wav.
## Installation
1.Open terminal or Command Prompt

2.Activate base conda environment

   C:\Users\YourName> miniconda3\Scripts\activate

3.Create a new conda environment

   (base) C:\Users\YourName> conda create -n mfa-test python=3.11


4.Activate the environment

   (base) C:\Users\YourName> conda activate mfa-test
   (mfa-test) C:\Users\YourName>


5.Install Montreal Forced Aligner from conda-forge

  (mfa-test) C:\Users\YourName> conda install -c conda-forge    montreal-forced-aligner


6.Check MFA version

  (mfa-test) C:\Users\YourName> mfa version
  
 Example output:
3.3.8
## Downloading MFA Models
1.List available acoustic models

(mfa-test) C:\Users\YourName> mfa model download acoustic


2.Download a specific acoustic model

(mfa-test) C:\Users\YourName> mfa model download acoustic english_us_arpa


3.List available dictionary models

(mfa-test) C:\Users\YourName> mfa model download dictionary


4.Download a specific dictionary

(mfa-test) C:\Users\YourName> mfa model download dictionary english_us_arpa


5.Check installed models

(mfa-test) C:\Users\YourName> mfa model list acoustic

Example output:
['english_us_arpa']

(mfa-test) C:\Users\YourName> mfa model list dictionary

Example output:
['english_us_arpa']

## Preparing Your Dataset
MFA expects a dataset organized like this:

dataset/
├── wavs/
│   ├── file1.wav
│   ├── file2.wav
│   └── ...
└── texts/
    ├── file1.txt
    ├── file2.txt
    └── ...

Rules:

Audio files must be .wav (16 kHz recommended).

Each .txt file must have the exact same filename as its corresponding .wav.

Transcriptions should be plain text, no punctuation (optional: lowercase for consistency).

Example:

wavs/file1.wav ↔ texts/file1.txt containing:

IIITH THANK YOU 
## Running Alignment
1.Basic alignment command

(mfa-test) C:\Users\YourName> mfa align dataset/ english_us_arpa english_us_arpa aligned_output/


dataset/ – path to your dataset

english_us_arpa – acoustic model

english_us_arpa – dictionary

aligned_output/ – output directory

2.Check the results

The output folder will contain:

.TextGrid files for each audio file – compatible with Praat

Log files indicating alignment progress
# Example Workflow
Activate environment

   conda activate mfa-test

 Download models

mfa model download acoustic english_us_arpa

mfa model download dictionary english_us_arpa

Run alignment

mfa align dataset/ english_us_arpa english_us_arpa aligned_output/
## Expected output:
Aligning files...

file1.wav -> file1.TextGrid

file2.wav -> file2.TextGrid

Alignment complete. Results saved in aligned_output/

## Demo

Insert gif or link to demo


## Screenshots



