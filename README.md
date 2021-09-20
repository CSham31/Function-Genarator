# Function-Genarator
Abstract

Numerous instrumentation engineers and re-
searchers frequently manage analog electronic issues
when moving toward sensitive estimations. Regardless
of whether off-the-shelf measuring solutions exist, per-
ception of the analog electronic of the measuring so-
lutions is frequently a need. The function generator is
also known as the signal generator is become the most
used testing device. The function generator delivers an
accurate calibrated range. This report talks about the
overview of a signal generator, how to generate function
using analog electronics, and changing its characteris-
tics like waveform, modulation, frequency, and ampli-
tude voltage.
Contents

1 INTRODUCTION 2

2 Electronic Design 2
2.1 Design Specifications.......... 2

3 Wave Genaration 2
3.1 Square Wave.............. 2
3.2 Trangular Wave............. 3
3.3 PWM Wave............... 3
3.4 Sawtooth Wave............. 3
3.5 Sine Wave................ 4

4 Output Circuit 5
4.1 Summing Amplifier........... 5
4.2 Push-Pull amplifier........... 5

5 Power Supply 5

6 Component Selections 5

7 Simulations 7

8 PCB Designs 10

9 Enclosure Design 11

10 Discussion 12

1. INTRODUCTION

A function generator is an electronic device that is
used for generating various types of electrical wave-
forms such as sine waves, square waves, triangular
waves, Sawtooth waves over a frequency range. These
waveforms can be either single-shot signals or repeti-
tive signals. In addition to changing the type of wave-
form, the function generator is also capable of varying
the waveform characteristics such as frequency, ampli-
tude. Uses of the function generator,

    Sweep generation
    AM/FM generation
    Phase-Locked Loops
    In addition to the above applications function gen-
    erators are also used for repair, development, and test
    of electronic devices. Function generators are primar-
    ily used for working with analog circuits, related pulse
    generators are primarily used for working with digital
    circuits.
    Most of the modern function generators are made
    using Digital components. The objective of this project
    is to build and implement a fully functional analog func-
    tion generator which generates various waveforms with
    varying amplitude and frequencies.
    In this report, we describe the different circuits
    used for the generation of noise-free waveforms and
    how potentiometers and transistors are used to change
    the frequencies and the amplitudes of the waveforms.

2. Electronic Design
2.1. Design Specifications

In this project, we will fulfill thesespecifications.

    The function generator should be able to generate
    sine, triangular, saw-tooth, square and pulse width
    modulation(PWM) waves.
    The frequencies of the waves should be able to
    vary from 20 Hz to 20000 Hz.
    The amplitudes of the waves should be able to vary
    up to 20V peak-to-peak.
    In the PWM wave, the pulse width should be able
    to vary from 1% up to 99%.
    The function generator should be able to supply
    the waves to a 50W load.
    The function generator should be able to give a DC
    shift to the waves.

3. Wave Genaration
3.1. Square Wave

A square wave is a wave which is a non-sinusoidal
periodic waveform. A square waveform can be repre-
sented as an infinite summation of sinusoidal waves.
Square wave generator can be constructed using the
Schmitt trigger circuit. A Schmitt inverter is the in-
verse to that of its input. It uses a Schmitt trigger action
that changes state between an upper and lower threshold
level as the input voltage signal increases and decreases
about the input terminal.

Figure 1. Schmitt Trigger

This simple square wave generator circuit consists
of a single Schmitt inverter logic gate with a capacitor
connected between its input terminal and ground and
the positive feedback required for the circuit to oscillate
being provided by the feedback resistor.
Let us take,

V 2 =Voltageat invertingterminal
V 1 =Voltageat thenon−invertingterminal
Vid=di f ferential voltage

When the charge across the capacitor is below
Schmitt’s lower threshold level it makes the input to the
inverter at a logic “0” level resulting in a logic “1” out-
put level (inverter principals).
At this stage,

V 2 = 0 V
There fore,Vid=V 1

As Vid is positive, it will drive the Vout to the pos-
itive saturation voltage. (Since the capacitor does not
have any charge at the initial stage, the gain is maxi-
mum)

At this time capacitor gets started charging and it
will increase the voltage of the capacitor. Therefore,
V2 gets an increase. After V2 getting a little higher
than V1, it will give negative output and Vout will
be switched from positive saturation voltage to nega-
tive saturation voltage.At this negative saturation volt-
age,V1 can be given as,
At this negative saturation voltage,V1can be given
as

Vid=−V 1 +V 2

−V 1 =(R 4/R 4 +R 3)*(−Vsaturation)

Since V1 is negative, the capacitor starts to dis-
charge through the resistor towards negative saturation
voltage.
After reaching V2 slightly less than -V1, the output
will again be switched to a positive saturation voltage.
This process will happen again and again, and a square
wave is generated.
Overall,
|V 1 |=(R 1/R 1 +R 2)*|Vsaturation|

Let

R 1 +R 2 =R

We can write the product as,

T= 2 RC×ln

2 R 4 +R 3
R 4

since f=1/T=1/2 RC×ln^2 R^4 R+ 4 R^3 Hz

Since R4 and R3 are constants,

f α 1/RC

Therefore, by changing R and C values, we can change
the frequency of the square waveform.The R2 is used to
prevent the resulting resistance from becoming zero.
3.2. Trangular Wave

Method I
This method is based on passing the square waves
through an integrator. This method has two main parts.
Which are,

    Square wave generator – which generates square
    waves.
    Integrator – which converts square waves to trian-
    gular waves.

Method IIWhen the capacitor charges and dis-

Figure 2. Triangular Wave Genaration

charges,theoretically the shape of the voltage across the
capacitor is an exponential waveform. But practically,it
will be triangular. So, we can use a capacitor as a trian-
gular waveform generator.
we are using second method because easy to inte-
grates with other circuits.

3.3. PWM Wave

PWM signal is used to get low-frequency signal
by high-frequency source by switching the voltage be-
tween upper and lower levels, and output can be taken
as the average of voltage over the period of switching
between upper and lower level.
The PWM waves are generated by passing the tri-
angular waves through a comparator.

3.4. Sawtooth Wave

A triangular waveform is a waveform that
is linear,non-sinusoidal, triangular shape waveform.
When the rise time and the fall time are equal, the wave-
form is named as a pure triangular waveform.
When the rising time and falling time are differ-
ent the waveform named Sawtooth Waveform.The saw-

Figure 3. With Schmitt Trigger

Figure 4. Comparator PWM Genaration

tooth waveform can be generated using a cascade com-
bination of a Schmitt trigger circuit and an integrator.
The Schmitt trigger gives the output as a square wave.
By feeding this output by an integrator we can gener-
ate triangle and sawtooth waveforms.In our circuit we
use PWM as the input, by doing that we can adjust the
rising/falling time by using PWM duty adjuster.
In this circuit, the non-inverting terminal of the in-
tegrating op-amp is given a dc voltage. The second op-
amp integrates the Schmitt trigger output of the first op-
amp and gives a saw-tooth waveform. By varying the
dc voltage given to the non-inverting input of the inte-
grator, we can change the rising and falling time of the
saw-tooth waveform. When this dc voltage becomes
zero, the output will be a triangular waveform. The fre-
quency of the output voltage can be varied by varying
R1 resistor and capacitor.

Figure 5. Intergrating PWM Wave

3.5. Sine Wave

There are many ways to create a sine wave. Such as
Wien bridge oscillator, Phase-shift oscillator, Colpitts
crystal oscillator,Square waveform and filter, Pulse-
based sine wave generator.

We have chosen the square waveform and filter.
From the Fourier series theory, a square wave can
be thought of as sinusoidal waves. We can similarly
think of triangular waves. So, we can obtain the sinu-
soidal waves by sending the amplified triangular waves
through a low pass filter.

Figure 6. Sine Wave Genaration

Figure 7. Output Circuit

4. Output Circuit
4.1. Summing Amplifier

Summing amplifier is used to give DC offsets and
Changing Amplitude of the final output signal.

Gain= Vout/Vin =R f/ Rin

Rf is constant.So

when Rin= 10 k

Gain=10 k/10 k = 1
Also Rin= 1 k

Gain=10 k/1 k= 10

By changing Voltage of non-inverting terminal, We can
add DC offsets to the output circuit.
4.2. Push-Pull amplifier

A push-pull amplifier is an amplifier that has an
output stage that coulddrive a current in both directions
through the load. The output stage of a typical push-pull
amplifier consists of two identical BJTs or MOSFETs
one sourcing current through the load while the other
one sinking the current from the load.
5. Power Supply

Figure 8. Power Supply Circuit

In this project power supply wants to give sev-
eral outputs. They are DC outputs because electronic
components need DC power. To complete our require-
ment, we must create +12V and -12V DC power sup-
ply. There were two options for this. They are, Using a
rechargeable battery. Using the AC power supply. Con-
sidering these two options we are mostly thinking about
the second option. Our product is laboratory equipment.
And it must be work for a long time. If we choose a
rechargeable battery it cannot withstand against those
conditions.
We use a step-down transformer and plug its inputs
to the main power supply through the fuse for the pro-
tection of the circuit. Then there is a diode bridge for
the full-wave rectifier. Then use a smoothing capac-
itors and then use a regulation done by LM78712 and
LM7912 regulators. Finally,there is another capacitors
for further improving output voltage quality.

6. Component Selections

In this project we have use RC oscillator for mak-
ing and changing frequiency of the wave. First we de-
cided to usevariable resistor. Then we realised that we
need more resolution so we usedMulti turn variable
resistorsfor fine tuning. Also we usedDescrete set of
capacitorsfor make it more fine.
Op-amp selectionThe waveform generation and
amplification is done by op-amp circuits. To meet
the given specifications a suitable op-amp must be se-
lected.The selected op-amp for this project is TL084.
Which has higher GBP 1MHz and This low noise op-
amp has a high slew rate of 13Vus.This is an important

Figure 9. Capacitor set

factor in square wave generation.

maximumgain=1 × 106/2 × 104 = 50

Transistor selectionThe push-pull amplifier output
stage is to drive a 50Ωload through the function gener-
ator. The maximum power and current which should be
given across a 50W load by a 20V peak-to-peak wave
can be calculated as follows.

maximum power = 102/50 = 2 W

maximumcurrent=10/50= 200 mA

So We selected TIP 31 and TIP 31 transistors.
In power supply circuit we choose LM7812 and
LM7912 which has maximum output cuurent of 3A. In
that case, we have used GBU6M/DGBU6A bridge rec-
tifier.
We have used DPDT switches which has locking
mechanisms on it for selecting options.
7. Simulations

Power Supply

Figure 10. Power Supply Circuit

Figure 11. Output Results by Power Supply

Output Circuit
Main Circuit

Figure 12. Output Circuit

Figure 13. Input Signal for Output cct. Simula-
tions

Figure 14. Amplitude Changing

Figure 15. DC Offsets

Figure 16. Main Circuit

Figure 17. Square Wave

Figure 18. 20 Hz

Figure 19. 20000 Hz

Figure 20. Triangular Wave

Figure 21. PWM Wave

Figure 22. Sawtooth Wave

Figure 23. Sine Wave

8. PCB Designs
9. Enclosure Design

(exploded view, isometric view of front and back)

10. Discussion

By using analog electronic components we can
make waves. We can determine characteristics such as
frequiency, Amplitude, DC offset,Wave shape and Duty
Cycle.Using Op amp as the main block of the design,
We could implement comparators, Inverters,amplifiers
and Schmitt Trigger... etc.By combine them together
and using several filters for joints we could make work-
ing function genarator at the end.
