# Single-Instrument Music-Loops Generator
## What is it?
This is a (audio/text)-to-audio pipeline that, as the name says, is able to take a musical idea of the user (as audio file), and generate a specified single instrument loop, with specified style and characteristics, that is coherent with the given idea, automatically understanding and following technical constraints such as BPM and Key, and more broad constraints such as Genre and Mood, in order to make the final generation as coherent as possible with the initially given idea.

For the generation you can choose between 3 different generative models, which, because of very different training data and method, yields substantially different results given the same input.
Given the same audio + text prompt input, here is a brief comparison between the models:
- **AudioLDM2-Music**: very unexpected results, can be interesting for experimental generative sounds, expecially on "long" sounds (such as pads, drones...). Not very trustable when it comes to the Key and BPM constraints.
- **Stable Audio Open**: the best model for single instrument generation, dry-sounding loops ready to work with, you can feel how the training data contains also a good amount of separated instruments and the model performs pretty well on them. Pretty much controllable, sometimes lacks a bit of creativity, which can be a pro in some contexts and a cons in others.
- **MusicGen**: state-of-the-art model, definitely more creative than Stable Audio Open, creates intricate melodies, rhythms and soundscapes, BUT often refuses to generate just the instrument requested, generating also related instruments (expecially adding drums) or sounds, and making the output audio pretty wet of distortion or spacial effects even if not requested


There are 2 execution modes:
- **Normal Mode**: uses what i found to be the best settings and models, intended for quick tests/demos and non-professional use. It uses Stable Audio Open as generation model, which is the most suited for the idea of this pipeline. Everything happens "under the hood".
- **Advanced Mode**: more control and customization, gives the possibility to choose between the generation models, and the user can also revise the features automatically extracted from the input audio, to check/correct if needed, and get the most professional and personalised results as output.





# Guide

## 1. Setup
Execute **SETUP** (first time only).

## 2. Install generation model libraries
Install the libraries for the **generation models** you want to use:

- **AudioLDM2-Music** and **Stable Audio Open** share the same dependencies.
- **MusicGen** requires separate libraries and takes significantly longer to install.

### Requirements
- **Hugging Face login** is required to use the models.  
  You need an API key (free), which can be generated here:  
  https://huggingface.co/settings/tokens
- **CUDA drivers** and a **CUDA-compatible GPU** are required.  
  Recommended: **NVIDIA A100** for music generation inference.  
  If executing it on Google Colab, it may also work on **T4 GPUs**, but memory is often insufficient to complete inference.

## 3. Upload audio
Go to **UPLOAD** and:
1. Upload the musical idea you want to build on (`.mp3` or `.wav` only).
2. Press **Save file**.
3. A confirmation message and an audio preview will appear.

## 4. Mode selection
- **Advanced Mode**: more control and customization for professional results.
- **Normal Mode**: intended for quick tests or non-professional use.

---

## Known bugs / limitations

At the moment, it is only possible to install and use **either**:
- **AudioLDM2-Music + Stable Audio Open**, **or**
- **MusicGen**

If AudioLDM2 and Stable Audio Open libraries are installed, it is **not possible** to install `audiocraft` due to the following error: NotImplementedError: A UTF-8 locale is required. Got ANSI_X3.4-1968
fixes attempted but none resolved the issue for me:
1)
import locale
locale.setlocale(locale.LC_ALL, 'en_US.UTF-8')
2)
sudo locale-gen en_US.UTF-8
sudo update-locale

