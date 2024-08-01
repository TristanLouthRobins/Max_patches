# Max MSP patches
## A repository of Max patches created for projects or simply as experiments.

### **Metallic Rain (2024)** sound design for Airen, 2024
A patch consisting of two Markov Chains (leveraging Ben Smith's `ml.markov` object) to generate chord progressions and modal scale sequences. The chords and scales are outputted as MIDI data into virtual instruments in Logic Pro. The result is a long form soundscape that is ethereal and darkly ambient. Intended to be broadcast in a small exhibition space at a low volume. 

The matrices and graph diagrams for the respective Markov algorithms can be found below.

This project also incorporated an engineered prompt (ModalPilot v1 - `modalpilotv1.dm`) to determine the scales that would best fit the chords. This code can be found in the `prompt_engineering_frameworks` repository.

![unnamed](https://github.com/user-attachments/assets/da6a9545-5f9c-4da5-ac2d-d941404cd8c6)

#### Engineered prompt (ModalPilot v1) applied to generate extended chords and modal scales for each chord:
```
User input:
C# major 7th, A# minor. These chords will repeat themselves, but please suggest a couple of passing chords - maybe additional minor chords - which would work in a coherent chord progression.

Response #1:
For the progression starting with C#maj7 and A#m, you can use the following passing chords for a smooth and coherent sound:

Recommended Chord Progression:

	•	C#maj7
	•	F#7 (passing chord)
	•	A#m
	•	D#m7 (passing chord)

Associated Scales for Improvisation:

	•	C# Ionian (Major) Scale: For the C#maj7 chord.
	•	F# Mixolydian Scale: Over the F#7 passing chord.
	•	A# Aeolian (Natural Minor) Scale: For the A#m chord.
	•	D# Dorian Scale: Over the D#m7 passing chord.

These passing chords create a smooth transition and maintain coherence in the key of C#. Enjoy your improvisation!

User input #2:
Can you substitute the F#7 for something a little more mellow and open? Perhaps a 9th, 11th or extended 13th chord instead?

Response #2:
Sure! Here's an alternative with a more mellow passing chord:

Updated Chord Progression:
- **C#maj7**
- **F#maj9** (passing chord)
- **A#m**
- **D#m11** (passing chord)

Associated Scales for Improvisation:
- **C# Ionian (Major) Scale**: For the C#maj7 chord.
- **F# Lydian Scale**: Over the F#maj9 passing chord.
- **A# Aeolian (Natural Minor) Scale**: For the A#m chord.
- **D# Dorian Scale**: Over the D#m11 passing chord.

These chords offer a smoother and more open sound. Enjoy playing around with them!

User input #3:
Can you please list the notes which make up the F#maj9 and D#m11 chords?

Response #3:
Of course! Here are the notes for each chord:

F#maj9
- **F#**
- **A#**
- **C#**
- **E# (F)**
- **G#**

D#m11
- **D#**
- **F#**
- **A#**
- **C#**
- **G#**

User input #4:
Oh, can you please list the notes in the scales that you recommended?

Response #4:
Of course! Here are the notes for each chord:

F#maj9
- **F#**
- **A#**
- **C#**
- **E# (F)**
- **G#**

D#m11
- **D#**
- **F#**
- **A#**
- **C#**
- **G#**
```

#### Chord generation initialisation matrix:
|            | C#^7 | A#m | F#^9 | D#m11 | Silent |
| ---------- | ---- | --- | ---- | ----- | ------ |
| **C#^7**   | 0    | 0.8 | 0    | 0.1   | 0.1    |
| **A#m**    | 0.7  | 0   | 0.3  | 0     | 0      |
| **F#^9**   | 0    | 0.5 | 0    | 0     | 0.5    |
| **D#m11**  | 0    | 0   | 0.3  | 0     | 0.7    |
| **Silent** | 0.8  | 0   | 0    | 0     | 0.2    |

#### Graph design:
![unnamed](https://github.com/user-attachments/assets/f8aea4bc-d5c6-4051-804d-9ee48b26b7c7)

#### Scale generation initialisation matrix:
|       | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| ----- | --- | --- | --- | --- | --- | --- | --- |
| **1** | 0   | 0.5 | 0.1 | 0.2 | 0.1 | 0.1 | 0   |
| **2** | 0   | 0   | 1.0 | 0   | 0   | 0   | 0   |
| **3** | 0   | 0.3 | 0   | 0.7 | 0   | 0   | 0   |
| **4** | 0   | 0   | 0.3 | 0   | 0.7 | 0   | 0   |
| **5** | 0   | 0   | 0   | 0.5 | 0   | 0.5 | 0   |
| **6** | 0   | 0   | 0   | 0   | 0.3 | 0   | 0.7 |
| **7** | 1.0 | 0   | 0   | 0   | 0   | 0   | 0   |

#### Graph design:
![unnamed](https://github.com/user-attachments/assets/5b54a907-52ad-47f2-bc9f-468cef47177d)


### **outdoor furniture music (2022)** - version 1.0, 2022
Inspired by this Disquiet Junto prompt: https://llllllll.co/t/disquiet-junto-project-0566-outdoor-furniture-music/59371/16

A crude tone generator with its sequence of notes (based on a Bb Maj7 chord) determined by a Markov Chain algorithm. Uses Ben Smith's awesome `ml.markov` object. 

![Screen Shot 2022-11-05 at 3 00 58 pm](https://user-images.githubusercontent.com/62044678/200106367-bcc8d988-e0f9-4fee-8fa2-07568b7db106.png)

The final result (for the Junto prompt) took the Max output and routed it through Morphagene and DLD modules. A Soundcloud link to the audio is here: https://soundcloud.com/red_robin/disquiet_junto_0562-outdoor-furniture-music-made-with-max-a-markov-chain-and-morphagene

A video documenting the audio ported into a battery powered mp3 player and deployed in my courtyard can be found here: https://www.youtube.com/watch?v=hTUc7C0mCrE

### **On Another Ocean (2019)** - version 1.0, 2019
A Max patch naively emulating the computer process of David Behrman's *On The Other Ocean* (1977). To be revisted and improved upon at some point.

Read about the inspiration behind the patch on my blog here: https://tristanlouthrobins.wordpress.com/2019/08/26/communique-3-wild-is-the-wind/

Demonstration of patch: https://www.youtube.com/watch?v=SeZE_50RPCY

### **Zona (2018)** - version 3.0, 2018
A complex sampler patch which was developed to create 'lowercase' sound textures and compositions. It was the primary compositional tool used for the creation of several compositions featured in my 2018 installation work, Compression and the album of the same name.

Read more about the installation work here: http://www.tristanlouthrobins.com/work-compression.html
Album link (Bandcamp): https://tristanlouthrobins.bandcamp.com/album/compression

### **Goyder's Line (2014-2017)** - version 5.0, 2017
The finalised Max patch that drives the realisation of this work.

Read more about this work here: http://www.tristanlouthrobins.com/work-goyder.html

### **Noise Wave (2011)** - version 2.0, 2011
A second attempt to emulate the sound of a crashing wave on a beach using Max/MSP - `noise~`  via `filtergraph` and function objects which determine frequency range/bandwidth and the level of gain over a 20 second duration.

Demonstration of patch: https://www.youtube.com/watch?v=mqAIYQMm4DM&t=251s






