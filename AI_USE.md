# AI Use Log

This file documents how AI was used in this project, as required for DSC 180 (Piazza @129). It lists every prompt used to build the code and the report, and how the results were tested.

**Tool:** Claude (Anthropic), in [the claude.ai app / Claude Code].
**Student:** Sahar Zahir · **Mentor:** Victor Minces

---

## Part 1: Code

Each prompt is copied exactly as I sent it. A back-and-forth on one feature is grouped under a single session.

### Session 1: First version of the harmonics app (Oct 2, 2026)
**Chat:** "Understanding vibe coding"

**Prompt 1:**
> Can you explain to me what vibe coding is

**What Claude produced:** An explanation of vibe coding: describing what you want in plain language and letting AI write the code, its benefits, its risks, and how it differs from AI-assisted coding.

**Prompt 2:**
> Perfect, I just got an assignment to vibe code this web app about sound and frequency. I can describe what my mentor told me to do and give you a picture of his vibe code, could you help me achieve this?

**Prompt 3:**
> With that set up make a web app: Set up amplitude of the fundamental frequency (f0) and harmonics
>
> * Control: fundamental frequency
> * Waveform box
> * Fourier transform box
>
> Essentially recreating what we were shown in class

**What Claude produced:** The first app, "soundLab harmonics", as a single web page. It has an f0 control (slider plus number box, 20 Hz to 2 kHz), 60 harmonic bars that work as sliders with presets (Sine, Saw, Odd/square, Triangle, Flat, Clear), a waveform window with an adjustable time window (2 to 100 ms), and a Fourier transform (spectrum) window that measures the real sound with an FFT, on a log or linear scale. It also has noise and level controls.

**How I tested it:**
Me: [e.g., Opened it in the desktop app. Pressed Start audio and listened. Clicked Saw and then Odd (square) and checked that the waveform changed from a ramp to a blocky shape and every other spectrum peak disappeared. Compared it against my mentor's version from class.]

**Prompt 4:**
> here are some extra messages from my mentor, does this have everything he is asking for?
>
> [pasted Victor Minces's Sep 29 email: set up Claude Code; create a web app with sliders for the fundamental frequency and harmonics; a control for the fundamental frequency; a window showing the waveform; a window showing the Fourier transform]

**What Claude produced:** A check of the app against each requirement in the email: all the web app requirements were covered. It noted that the one item not covered was setting up Claude Code, which I had to do on my own computer.

**Prompt 5:**
> So I am in the desktop app right now can you detect that?

**What Claude produced:** An explanation that this was a regular chat, not Claude Code, and how to find the Code tab in the desktop app.

### Session 2: Partials Lab, the first build (Oct 13, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1:**
> -Make an app that allows you to add frequencies and amplitudes by typing. Make sure you can see the waveform and hear the sound.
> Play with it.
> Add 'random' frequencies.
> Add a frequency and its multiples e.g. 100, 200, 300,...
> Compare how they sound. Compare how they look.
> For the waveform window, make sure that you can change the scale. See many seconds, 100 ms, etc.
>
> -Get creative, control sound (e.g. fundamental, number of harmonics, you name it) with some gesture (body positions from the camera, accelerometer, maybe something else....)
>
> make the colors follow a neutral color palette browns and desert tones

**What Claude produced:** Claude rebuilt the app as "Partials Lab", a single web page. It has two sounds, A and B, each a list of frequency/amplitude rows I can type, or enter as a list like "100, 200:0.5, 300". A note under each list says whether the sound is harmonic, periodic or inharmonic, and how often its waveform repeats. A Generate panel makes a frequency and its multiples (with equal, 1/n, 1/n² or odd-only amplitudes), random frequencies, and side-by-side comparisons (multiples vs random, multiples vs detuned ±3%, missing fundamental). The waveform view's time window goes from 1 ms to 20 s (preset buttons, a slider, mouse-wheel zoom), with height controls and a "scroll in time" mode. The spectrum view shows one line per frequency on a log scale, in dB or linear. Hear A / B / A⇄B compares the sounds by ear. A gesture synth controls the fundamental, number of harmonics, brightness and stretch with sliders, a touch pad, phone tilt/shake, or camera body tracking. Colours use a brown/desert palette.

**How I tested it:**
Me: [e.g., opened it, pressed Sound on, compared "multiples vs random" by ear and by looking at the waveform at 10 ms and 10 s, tried the touch pad.]
Claude's checks: ran the page in a headless Chrome browser at desktop and phone widths, in light and dark mode. Typed a list, generated multiples and random sets, and used the touch pad, checking for errors. Took screenshots and fixed what they showed: frequency boxes that cut off long numbers, a wrapping column header, and overlapping labels on the pad and spectrum.

### Session 3: Hosting and sharing (Oct 13, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1:**
> Is this under a git repo on my account?

**Prompt 2:**
> Ok so I need to publish the website?

**Prompt 3:**
> Yeah I would like a private link how do I do that

**Prompt 4:**
> perfect now lets launch it as a public link

**What Claude produced:** Confirmed the code was in my GitHub repo saharzahir/VibeCode-Practice on the branch claude/zen-rubin-1d17o3. Explained when a web address is needed (phone tilt, and the camera in some browsers). Published a private claude.ai link to the app. For a public link, explained the two options: the Share menu on the claude.ai page, or GitHub Pages (Settings > Pages > pick the branch).

**How I tested it:**
Me: [e.g., opened the private link; set up / tried GitHub Pages.]
Claude's checks: confirmed the branch on GitHub and the published link.

### Session 4: Redesign (Oct 13, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1** (with two reference images: a desert dune colour palette and the "KIMI Aviation" website):
> can we make the website look more modern and follow these color patterns it looks so dingy right now.

**What Claude produced:** A new look built on the dune palette (#D2D9D8, #D9C3A9, #BF9B7A, #A67458, #734B34). A rounded header shows a hazy sky over three dune layers, with a thin, wide-spaced "PARTIALS / LAB" title like the KIMI site. Panels are frosted "glass", buttons and switches are pill-shaped, and sliders are thin and fill up to the handle. New fonts (Jost and Manrope). A light "day" theme and a dark "dusk" theme follow the device setting.

**How I tested it:**
Me: [e.g., opened the updated link and compared it with the reference images.]
Claude's checks: screenshots in light and dark mode. Fixed one problem: the Hear switch looked washed out in the dark header.

### Session 5: Understanding the app (Oct 13 to Oct 19, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1** (Oct 13):
> what does the stretch refer to woth the head tild in the camera setting

**Prompt 2** (Oct 19):
> Can you give me in depth writing about what this webpage does

**What Claude produced:** An explanation of "stretch": the harmonics are pushed off exact whole-number multiples (harmonic n plays at f0 × n^(1+stretch)), and the more the head tilts, the more stretch is applied. Then a document, "Partials Lab: How It Works", covering the acoustics ideas behind the app, a tour of every panel, the gesture controls, how the app is built (with a diagram), experiments to try, and the app's limits.

**How I tested it:**
Me: [e.g., read the document and checked it against the app.]

### Session 6: Voice recording and vowel synthesis (Oct 28, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1:**
> theres a few things we need to add:
>
> 1-Add a microphone button. It activates the microphone. Through the app you can visualize the 'waveform' and the spectrum.
> 2-pick a few vowels (match the tone), make sure the fundamental is the same. Tinker withe the harmonics (sliders) so you recreate your vowels. Save the original sound and the  synthesized sound so you share it with the class. Try the same vowels with a different pitch. Note the differences. Send a video by Monday afternoon. Less than 3 minutes.
> 3-Find an automatic way of synthesizing your vowels. That means finding the fundamental frequency and the harmonics and playing stuff back. (this might be difficult). You can fail.
> Let me know anytime if you have any questions.
>  we need to discuss back and forth how to approach 3

**What Claude produced:** For parts 1 and 2, a Voice panel with a microphone button and level meter, a live waveform and spectrum of my voice, pitch detection, recording up to 10 s, Hear "Voice" and "Voice⇄A" to compare my recording with Sound A, a spectrum hover that reads my voice's level at any frequency as an amplitude to type in, "Use as base frequency", and saving the original and the synthesized sounds as .wav files. For part 3, Claude first laid out the options (copy the harmonics exactly vs copy the vowel's overall shape; one snapshot vs following changes over time) and asked me four questions: where it should live, whether it needs to change pitch, whether my teacher named a method, and how high my voice is.

**Prompt 2:**
> lets do it as a button, change-pitch so its inclusive, no method mentioned and I have a fairly high voice

**What Claude produced:** A "Synthesize from recording" button that measures each harmonic of my recording and rebuilds it in Sound A. A "Change pitch" slider (±12 semitones) rebuilds the vowel at a new pitch from its shape: a line through the harmonic peaks, chosen because it works better for a high voice. An option puts a "plain copy" in Sound B, so I can hear why keeping the shape matters. The vowel shape is drawn as a dashed line on the spectrum.

**How I tested it:**
Me: [e.g., recorded my own vowels, tried Use as base frequency, copied amplitudes by hand, used Synthesize from recording and Change pitch, compared Voice⇄A and A⇄B, saved the .wav files.]
Claude's checks: fed a fake microphone into a headless browser, using synthetic "ah" vowels with known resonances (150 Hz and a high 330 Hz voice, with slight vibrato and breath noise). Pitch was detected exactly. Recording and saving produced the expected .wav files. After shifting the pitch, Sound A stayed within about 2 to 5 dB of the true vowel shape, while the plain copy in B drifted 6 to 11 dB away.

**Follow-up questions in this session** (explanations, no code changes):
> What am i supposed to do

> is this right

(sent with a screenshot of the merged pull request on GitHub)

> please explain to me as if I were a 5 yr old what each thing does and why we have different harmonics

> How does the mic work

**What Claude produced:** A step-by-step plan for the assignment and the video. Confirmation that my merge was correct, plus the GitHub Pages link. A simple explanation of sound, harmonics and every part of the app. An explanation of how the microphone is sampled, drawn, analysed for pitch, and recorded.

**How I tested it:**
Me: merged the pull request on GitHub and checked it with Claude [add anything else you did].

### Session 7: Filter and Morph Lab (Nov 2 to Nov 3, 2026)
**Chat:** "Frequency waveform synthesizer"

**Prompt 1** (Nov 2):
> add these additions to the website:
>
> 1 - Incorporate a filter
> 2 - replicate the vowels by maxing all the harmonics and fundamental, and applying a filter. (send me a video, 1 minute)
> Add 1 and two to the sound lab application.
>
> 3 - Record two sounds, add a slider that goes between those two sounds, when the slider is all the way to one end, you will hear one sound, when it is all the way to the other end, you will hear the other sound. When is allong the path it will 'interpolate the sounds'.
> 4 - Generalize 3, to two dimensions. Make a square (2 dimensional space), make it so you can record sounds and assign them to 'dots' in that square. Then when you click on the square, you will generate a sound such that if you click on one of the recorded sounds you will hear the recorded sound.
> (3 and 4 are an app on their own)
>
>
> also review this part we added:
> 1-Add a microphone button. It activates the microphone. Through the app you can visualize the 'waveform' and the spectrum.
> 2-pick a few vowels (match the tone), make sure the fundamental is the same. Tinker withe the harmonics (sliders) so you recreate your vowels. Save the original sound and the  synthesized sound so you share it with the class. Try the same vowels with a different pitch. Note the differences. Send a video by Monday afternoon. Less than 3 minutes.
> 3-Find an automatic way of synthesizing your vowels. That means finding the fundamental frequency and the harmonics and playing stuff back. (this might be difficult). You can fail.

**What Claude produced:** For parts 1 and 2, a Filter panel in Partials Lab. It has up to 6 bands (band-pass, low-pass, high-pass, peak), each with frequency, width (Q) and level, plus Filter A / Filter B switches. Presets cover low-, high- and band-pass and the vowels ah, ee, oo, eh. "Fill A with a flat source" sets every harmonic to amplitude 1 ("maxing all the harmonics"), and "Fit to my recording" finds my vowel's resonances and turns them into bands. The filter affects the sound, the waveform, the spectrum and the saved files. For parts 3 and 4, a new app, Morph Lab. It records up to 8 sounds (four example vowels are included). A Line slider moves between two sounds (part 3). In a Square, each sound is a dot, and pressing anywhere blends the sounds by distance (part 4); an Arrange mode moves the dots. The blend mixes pitch and vowel shape, and on a dot it plays the real recording. A Crossfade mode is included for comparison. Both apps also got a built-in "How to do the assignments" guide, and Claude wrote a step-by-step tutorial for the previous week's features.

**How I tested it:**
Me: merged the pull request on GitHub and opened the live site [add what you tried: presets, Fit to my recording, the line slider, the square].
Claude's checks: the filter maths matched the browser's own filter exactly (0.0000 dB difference) for every filter type. "Fit to my recording" found resonances at 712, 1166 and 2601 Hz on a test vowel whose true values were 700, 1200 and 2600 Hz. In Morph Lab, halfway between a 220 Hz and a 330 Hz sound gave 269.5 Hz (the musical midpoint), the centre of the square gave 25% of each of four sounds, and pressing on a dot gave 100% of that sound. Recording a new sound with a fake microphone worked. Also checked at phone width and in dark mode.

**Follow-up questions in this session** (Nov 3; explanations, no code changes):
> How do I reset a recording if I dont like how it came out

> So does the partials lab section where I'm recording my own voice just allow me to study the different components of my voice and thats its purpose? Just to study the frequency and wavelengths of my voice making vowel noises?

> how does part 1 rebuild my voice? How do I use the instrument to do that?

> where do I set the count?

> where is the filter?

> is it on there now?

> what does the generate and filter panel do because it seems like nothing

**What Claude produced:** How to redo a recording in each app. The purpose of the Voice panel: measure, rebuild, compare, change. A worked example of rebuilding a vowel by hand. Where the Count box is. That the Filter panel was missing from my live site because the second pull request hadn't been merged yet; after I merged it, Claude confirmed it was live. A one-minute test to clearly hear what Generate and Filter do.

**How I tested it:**
Me: merged the second pull request and reloaded the live site; [add what you tried after the one-minute test].

---

## Part 2: Written report

**Chat:** [Capstone Log] (Nov 4–6, 2026)

| Report part | What AI did | What I did |
|---|---|---|
| Abstract | Fixed spelling and grammar, corrected the order of the history (gesture before speech), and suggested adding a sentence on what I built and toning down "revolutionize." | Wrote the original abstract and chose which suggestions to accept. |
| Introduction paragraph | Revised the wording and checked that it was accurate. | Drafted my description of the project. |
| Literature review | Found and checked sources with web search, and edited the paragraphs. | Chose and removed sources, opened every link to confirm it, and drafted the text. |
| Data description | Drafted a description of the app's data. | Rewrote it in my own words and added what I recorded. |
| Fourier transform paragraph |[Edited it.] | Drafted it.|
| LaTeX | Converted the text into the DSC 180 Overleaf template and wrote the BibTeX references. | Pasted it into Overleaf, compiled it and fixed errors. |

