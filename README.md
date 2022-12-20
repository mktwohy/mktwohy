# Personal Portfolio

## ToneTutor
> **Links** [Repo](https://github.com/mktwohy/ToneTutor), [Demo](https://www.youtube.com/watch?v=Vf4jq-M7OHs)

When beginner musicians are learning how to play an instrument, it’s relatively easy to determine if you’ve played the right notes or not. However, they often overlook the *timbre* of these notes, which is equally important. Timbre is the quality of a note; for example, *warm* and *round* vs *sharp* and *bright*.

The main aspect that defines timbre are *overtones*. Overtones (often referred to as the *harmonic series*) are a sonic phenomenon where a root frequency is accompanied by frequencies which are integer multiples of the root. So, if an instrument plays the note $A_{\large4}$, you are not only hearing the root frequency $440\text{hz}$, but also $440\text{hz} \times 2$, $440\text{hz} \times 3$, $440\text{hz} \times 4$, etc. Different instruments and playing techniques (such as picking vs plucking, or playing near the bridge vs near the neck) alter the volume of certain overtones, thus changing the timbre.

**This project aims to invent the means for quantifying timbre, so that beginner musicians can receive real-time, visual feedback to train their ear and improve their playing technique.**

ToneTutor assigns a number to timbre with three steps:
1. it uses pitch detection to determine the fundamental note
2. it performs a Fourier transformation to figure out the overtones corresponding to that note. 
    - In ToneTutor, this is called the *harmonic fingerprint*. 
3. it calculates a weighted sum of the harmonic fingerprint, with higher overtones having a higher weight. 
    - In ToneTutor, this is called a *benya*. 
      - In general, a smaller benya results from a warm note, whereas a large benya results from a bright note.

*Note - ToneTutor is still a work in progress.*

<details><summary>Expand to learn more about the harmonic series</summary>
  <p>
    
  - [Harmonic Series Interactive Visualizer by Alex Anderchen](https://alexanderchen.github.io/harmonics/?howmany=16)
  - [Harmonic Series Video by Andrew Huang](https://www.youtube.com/watch?v=Wx_kugSemfY)
  - [Fourier Transform Video by 3Blue1Brown](https://www.youtube.com/watch?v=spUNpyF58BY)
    
  </p>
</details>

## Synth
> **Links** [Repo](https://github.com/mktwohy/Synth), [Demo](https://www.youtube.com/watch?v=TbRYWaP0Ipc)

An Android app for additive synthesis. After adjusting the harmonic-series editor and waveshape selector to construct a sound, the user can play music with the resizable, polyphonic keyboard and pitch bend slider.  

The app uses a [synth library](https://github.com/mktwohy/Synth/tree/Main/SignalLib/src/main/java/com/example/signallib) I wrote in a Kotlin for generating, manipulating, and playing periodic signals with overtones. This library is also used in ToneTutor for testing purposes.

This was my first dive into app development, and it ended up being a fantastic learning experience. 


## SatisfactoryCalculator
> **Links** [Repo](https://github.com/mktwohy/SatisfactoryCalculator)

[Satisfactory](https://www.satisfactorygame.com/) is a factory building game that I've been playing for the past few months. However, the game requires some ratio math that can become tiresome when planning larger factories. So, using [Compose for Desktop](https://www.jetbrains.com/lp/compose-desktop/), a Kotlin framework, I created a desktop app for browsing the game's recipes and calculating the clock speeds required for a given output/minute or vice versa. As a bonus, the app's UI mimics an in-game menu.

![SatisfactoryCalculator - Demo](https://user-images.githubusercontent.com/69822801/208554237-17409dc0-f5b6-4f39-9cb5-9a98c23fa508.gif)


## TimeCalc
> **Links** [Repo](https://github.com/mktwohy/TimeCalc)

Time arithmetic is something that is quite tedious to me. And, with a hybrid-remote job where I need to track my hours, it's something I need to do quite often. So, I wrote TimeCalc, a CLI [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)-like program for performing arithmetic with time and durations. 

TimeCalc was written with [Kotlin-Native](https://kotlinlang.org/docs/native-overview.html), which compiles down to a binary executable rather than a JVM byte-code. This makes it easier to add the executable to PATH and run from the command line.

TimeCalc supports the following:
1. Addition and subtraction
  ![TimeCalc - Addition and Subtraction](https://user-images.githubusercontent.com/69822801/208552095-b5499009-4fba-43c7-8fcf-65bfa5b3264c.gif)

1. Parentheses
  ![TimeCalc - Parentheses](https://user-images.githubusercontent.com/69822801/208552108-09b6962f-c405-4cf1-961a-8732eabff517.gif)

3. Variables and a reserved variable `now`
  ![TimeCalc - Variables](https://user-images.githubusercontent.com/69822801/208552122-86f2d28a-1eec-479d-90f8-ca921dff45d6.gif)

A common use case is seeing what time I will be ending work that day. Suppose I want to get 8 hours, and I've already spent an 5 hours and 26 minutes. In TimeCalc, this is achieved with the following:
![TimeCalc - Example](https://user-images.githubusercontent.com/69822801/208552281-256929eb-3a0e-4b99-8438-1d9842bb511e.gif)
	
## ToolNotifier
> **Links** [Repo](https://github.com/mktwohy/ToolNotifier)

I developed an app to help my brother stay updated on the latest tools available on hyperKitten.com, a simple website that doesn't have a mailing list. The app regularly checks the website and sends notifications via email or text when it is updated. This helps my brother, who does hand carpentry, stay informed about new tool releases without having to manually check the website himself.

To accomplish this, the app uses [WorkManager](https://developer.android.com/guide/background/persistent), a popular library for scheduling tasks, to run a script in the background on an old Android phone. This script checks the website, scrapes the last-updated date, compares it to the previous last-updated date, and alerts the mailing list if the date is new. 
