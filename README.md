# Audio_Amplifier 🔊
Designing a push–pull audio amplifier for a car speaker

# Goal 🎯
The goal of this project was to design a simple audio amplifier to drive a 30 watt speaker that I pulled out from a car door. The goal was not to make the most efficent design but to explore various designs.

# History
Initially, I began by driving the speaker with my USB oscilloscope/waveform generator (Analog Discovery 2). The USB waveform generator has the ability to take an MP3 file as an input and output the corresponding waveform. It also has the ability to amplify the signal up to a peak voltage of 5V. However, there were a few problems with this:
1. According to the datasheet, this waveform generator has the ability to output a maximum of 750mA. At a peak voltage of 5V, the power output would only be (0.75A x 5V = 3.75W) 3.75 watts, which is only about 13% of its power output capabilities
2. When set to 5V peak output, the waveform generator only seemed to be able to push out 250mA. This means we were only achieving a power output of (0.25A * 5V = 1.25W) 1.25 watts
3. Lastly, when set to 5V, the speaker seemed to suffer from a lot of distortion and resulted in very muddy tones
4. The final motivation was to see if I could drive the speaker signifcantyl louder. With a 1V waveform signal the loudest sound seemed to be around *INSERT DB MEASUREMENT*

# Constraints

# Parts
