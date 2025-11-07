Forced Alignment using Montreal Forced Aligner (MFA)
A complete, beginner-friendly pipeline to perform forced alignment between audio and text using the Montreal Forced Aligner (MFA). This guide walks you through installation, dataset preparation, model download, alignment, and result visualization — all explained in simple words, no code blocks, just clear steps.

TABLE OF CONTENTS

Prerequisites
Installation
Downloading MFA Models
Preparing Your Dataset
Running Alignment
Example Commands & Expected Output
Viewing Results in Praat
Common Issues & Fixes
Demo & Screenshots

Prerequisites

Operating System: Windows, macOS, or Linux
Python version: 3.8 to 3.11
Miniconda or Anaconda already installed on your computer
Optional: ffmpeg (only if your audio is in MP3, M4A, etc. — MFA needs .wav files)

Installation


Open Command Prompt (Windows) or Terminal (Mac/Linux)


Type the following commands one by one and press Enter after each:
miniconda3\Scripts\activate
conda create -n mfa-test python=3.11
conda activate mfa-test
conda install -c conda-forge montreal-forced-aligner
mfa version
You should see something like: 3.3.8 (or newer) — that means MFA is installed successfully!


Downloading MFA Models
MFA needs two things to understand English speech:

An acoustic model (how actually pronounce sounds)
A dictionary (how words are broken into sounds)

Run these commands:
mfa model download acoustic english_us_arpa
mfa model download dictionary english_us_arpa
To confirm they downloaded correctly:
mfa model list acoustic
→ You should see: english_us_arpa
mfa model list dictionary
→ You should see: english_us_arpa
That’s it — models are ready!
Preparing Your Dataset
Your folder must look exactly like this:
dataset/
├── wavs/
│   ├── speech1.wav
│   ├── speech2.wav
│   └── speech3.wav
└── texts/
├── speech1.txt
├── speech2.txt
└── speech3.txt
Important rules:

Audio files must be .wav (16 kHz is best)
File names must match exactly (except the extension)
Inside each .txt file, write only the spoken words, preferably in UPPERCASE and no punctuation

Example content of speech1.txt:
IIITH THANK YOU VERY MUCH
Running Alignment
In your terminal, after activating the environment (conda activate mfa-test), type:
mfa align dataset/ english_us_arpa english_us_arpa aligned_output/ --clean
Explanation of the command:

dataset/ → folder that contains wavs/ and texts/
english_us_arpa → acoustic model
english_us_arpa → dictionary
aligned_output/ → where results will be saved
--clean → deletes temporary files automatically

Wait a few seconds/minutes (depends on number of files).
Example Commands & Expected Output
Full example session:
conda activate mfa-test
mfa model download acoustic english_us_arpa
mfa model download dictionary english_us_arpa
mfa align dataset/ english_us_arpa english_us_arpa aligned_output/ --clean
You will see progress like:
Aligning files...
100%|██████████| 25/25 [00:18<00:00,  1.38it/s]
Alignment complete!
Results saved in aligned_output/
Now check the aligned_output/ folder — you’ll find one .TextGrid file for every .wav file.
Viewing Results in Praat

Download Praat (free): https://www.fon.hum.uva.nl/praat/
Open Praat
Click Open → Read from file… → choose any .wav file
Again Open → Read from file… → choose the matching .TextGrid file
Select both files in the list (hold Ctrl)
Click View & Edit
Magic! You now see:

Blue waveform
Top tier: word boundaries
Bottom tier: phoneme boundaries
Press Play to hear with perfect sync


Zoom with Tab key, select portions, edit boundaries if needed.
Common Issues & Fixes

ProblemSolution"No such file or directory"Double-check folder path and file names match exactly"Dictionary not found"Re-run the two model download commandsNo TextGrid files appearFirst run mfa validate dataset/ english_us_arpa english_us_arpaAlignment looks offAdd --beam 100 --retry_beam 400 to the align commandAudio not .wavConvert using ffmpeg or Audacity first
Demo

Screenshots


Terminal showing successful alignment
Folder structure before/after
Praat window with clear word and phoneme layers

Final Folder Structure After Running
dataset/
├── wavs/
│   ├── speech1.wav
│   └── speech2.wav
├── texts/
│   ├── speech1.txt
│   └── speech2.txt
└── aligned_output/
├── speech1.TextGrid
└── speech2.TextGrid
Author
venkata siva ch
Tools Used

Montreal Forced Aligner (latest v3+)
Praat (v6.4+)
Conda environment: mfa-test

Assignment completed 100% successfully!
