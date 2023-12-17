# Audio_Amplifier 🔊
Designing a push–pull audio amplifier for a car speaker

*DISCLAIMER - I want to preface by acknowledging that I'm not an expert in the realm of audio amplification. This field is incredibly vast and intricate. The project served as a valuable opportunity for me to delve deeper into this domain, but it's important to note that I might have made errors or made poor design choices in the process of learning* 

## Goal 🎯
The goal of this project was to design a simple audio amplifier to drive a 4-ohm, 30-watt speaker extracted from a car door. The objective was not to create the most efficient design, but rather to explore various design approaches.

## To-do List 📃
- [x] Pick amplifier class
- [x] Pick power stage amplifier
- [x] Design and simulate in LTSPICE
- [ ] Pick components with appropriate ratings
- [ ] Determine thermal output of transistors
- [ ] PCB design
- [ ] Testing

## History
Initially, I began by driving the speaker with my USB oscilloscope/waveform generator (Analog Discovery 2). The USB waveform generator has the ability to take an MP3 file as an input and output the corresponding waveform. It also has the ability to amplify the signal up to a peak voltage of 5V. However, there were a few problems with this:
1. According to the datasheet, this waveform generator has the ability to output a maximum of 750mA. At a peak voltage of 5V, the power output would only be (0.75A x 5V = 3.75W) 3.75 watts, which is only about 13% of its power output capabilities
2. When set to 5V peak output, the waveform generator only seemed to be able to push out 250mA. This means we were only achieving a power output of (0.25A * 5V = 1.25W) 1.25 watts
3. Lastly, when set to 5V, the speaker seemed to suffer from a lot of distortion and resulted in very muddy tones
4. The final motivation was to see if I could drive the speaker signifcantyl louder. With a 1V waveform signal the loudest sound seemed to be around *INSERT DB MEASUREMENT*

## Constraints
While devising the design for this project, I established a few constraints to prevent overcomplication. The constraints/rules I settled on were as follows:
* The input/audio signal would be anywhere from 100mV to 1V
* I wanted to avoid any audio amplification IC's. This allowed me to focus on the more basic principles of amplification using BJT's and MOSFET's
* I didn't have to make use of the full 30 watt power capabilites of the speaker

# Audio Amplifier Background
To drive a speaker louder (higher output power) there are two things to keep in mind. These elements are evident in the power equation $P = V × I$. To acheive a higher output power we must amplify both voltage and current. Achieving greater output power necessitates amplifying both voltage and current. Therefore, we divide our amplifier design into two stages: the voltage/signal amplifier stage and the current/power amplifier stage. This practice is widely employed in all types of audio amplifiers.

The subsequent step in the process involved determining the preferred classification of audio amplifiers for this design. There are four main classes: A, B, AB, and Class D. Further information about these classifications can be found in the links provided below.

<p align="center">
  <img align="center" width="368" height="256" src="https://blog.minicircuits.com/wp-content/uploads/2021/03/Amplifier_Classes-1.jpg">
</p>

I ended up settling on the class AB design for the following reasons:
* The class AB design is more efficient than the class A design (50 - 70% efficiency)
* The Class AB design does not suffer from the same clipping distortion as the Class B design. It benefits from biasing the transistors in a manner that ensures their conduction throughout all cycles of the input waveform
* It is less complex than a class D design
* The only drawback is that when there is no input signal, the transistors continue to conduct current, resulting in wasted power

The second decision was whether to use MOSFETs or BJTs for the power stage amplifier. I ultimately chose MOSFETs for the following reasons:
* They generally have high input impedance, which reduces the loading effect on the preceding stages
* The require no current to drive the gate pin
* They can switch faster than BJTs, which can be beneficial in certain applications
* Reduced distortion compared to some BJT designs
* The only drawback is they tend to be more expensive than BJT's

# Design
## Schematic
<p align="center">
  <img align="center" width="712" height="512" src="/images/Audio_Amplifier_Schematic.png">
  <p align="center"><small><i>LTSPICE Schematic Capture</i></small></p>
</p>

## Simulation
<p align="center">
  <img align="center" width="712" height="512" src="/images/Simulation_Graphs.png">
  <p align="center"><small><i>[1]Input Voltage [2]Speaker Power Consumption [3]Output Current [4]Output Voltage</i></small</p>
</p>

<p align="center">
  <img align="center" width="712" height="512" src="/images/Frequency_Response.png">
  <p align="center"><small><i>Circuit Frequency Response 20Hz - 48kHz</i></small</p>
</p>
  

# Parts
# Resources
* LTSPICE
* [Online Circuit Simulator](https://www.falstad.com/circuit/)
* [Introduction to the Amplifier](https://www.electronics-tutorials.ws/amplifier/amp_1.html)
* [Audio Amplifier Basics](https://www.youtube.com/watch?v=U0FIG2J6Zls&ab_channel=TexasInstruments)
* [Power Amplifiers](https://en.wikipedia.org/wiki/Power_amplifier_classes#Class_C)
