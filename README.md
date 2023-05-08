Download Link: https://assignmentchef.com/product/solved-uwee538-final-project-strain-gage-low-noise-signal-project
<br>
The final project for this course involves the design of the signal conditioning electronics for a strain gage sensor. You will design amplification and filtering for a strain gage signal with minimum amplitude in the µV range. The goals of this project are:

<ul>

 <li>To understand how to translate application specifications (e.g. dynamic range of a sensor output) into circuit specifications</li>

 <li>To understand the impact of different noise sources in a circuit and how they affect the achievement of performance targets (e.g. SNR), both individually and collectively</li>

 <li>To understand how to choose devices and apply gain and filtering to optimize for SNR, power dissipation, size, and cost</li>

 <li>To understanding the impact of manufacturing variations on performance goals, and how to select components that achieve the optimal balance between performance, component availability, and cost</li>

</ul>

The project will comprise two phases, each phase lasting 2-3 weeks. At the end of Phase 1 you are asked to submit 5-10 slides providing the details of your design choices and the results of any relevant analyses (e.g. circuit analysis or simulation results). Your Phase 2 submission will be a design report summarizing your approach and presenting your simulation results.

Please note that you will not be graded on meeting specifications until the final report submission. The primary purpose of the slide submission is to receive feedback and ensure that you are on track for meeting the final submission deadline. <em>Full credit will be given for the Phase 1 submission if all required deliverables are included (details to come). </em>

<h1>Table 1. Submission deadlines</h1>

<table width="624">

 <tbody>

  <tr>

   <td width="247"><strong>Item </strong></td>

   <td width="155"><strong>Due date </strong></td>

   <td width="222"><strong>Proportion of project grade </strong></td>

  </tr>

  <tr>

   <td width="247">Phase 1 slides</td>

   <td width="155">May 30</td>

   <td width="222">30%</td>

  </tr>

  <tr>

   <td width="247">Phase 2 report</td>

   <td width="155">June 12</td>

   <td width="222">70%</td>

  </tr>

 </tbody>

</table>

<strong> </strong>System Architecture

Many sensor systems employ analog multiplexing, a technique in which more than one sensor output is processed by a single ADC. Multiplexing reduces the overall component count and cost by sharing components between multiple sensor “channels”. Because the ADC samples multiple inputs, the sampling frequency needs to be higher than the case where the ADC only converts a single channel. To first order, the sampling frequency of the ADC should be at least N times higher than the Nyquist frequency, where N is the number of sensor channels.

Amplifier

<strong>Figure 1. Strain gage signal conditioning architecture. </strong>

Fig 1. show the sensor signal conditioning “front-end” architecture for a single channel. The differential output voltage of the strain gage is amplified by the instrumentation amplifier and converted to a single-ended voltage. The output of the amplifier is fed to a bandpass filter which sets the noise bandwidth of the front-end circuitry and removes DC offset. The ADC driver is needed to settle the output voltage within the short sampling period of the multiplexed ADC.

The strain gage produces a differential output in response to an applied strain. This occurs as the result of the lengthening or shortening of a conductive element, which in turn changes its resistance. These changes in resistance are typically quite small, as the change in length (D<em>L</em>) relative to the nominal length (<em>L</em>) is small, on the order of 0.1% (for example).

Strain gage configurations are typically based on the Wheatstone bridge, a network of four resistances with an “excitation voltage” applied across the bridge (<em>V</em><em>DD</em> in Fig. 1). The number of bridge resistances subjected to strain determines the strain gage sensitivity (expressed in mV/V).

Phase 1

For the first phase you are to design a low-noise instrumentation amplifier to amplify the strain gage signal while adding minimal noise.

Table 2. Phase 1 specifications

<table width="623">

 <tbody>

  <tr>

   <td width="312"><strong>Parameter </strong></td>

   <td width="180"><strong>Specification </strong></td>

   <td width="132"><strong>Unit </strong></td>

  </tr>

  <tr>

   <td width="312">Supply voltage (<em>V</em><em>DD</em>)</td>

   <td width="180">5</td>

   <td width="132">V</td>

  </tr>

  <tr>

   <td width="312">Peak-to-peak input signal amplitude (max)</td>

   <td width="180">20</td>

   <td width="132">mV</td>

  </tr>

  <tr>

   <td width="312">Nominal strain gage resistance (R)</td>

   <td width="180">1</td>

   <td width="132">k</td>

  </tr>

  <tr>

   <td width="312">Peak-to-peak output amplitude (max)</td>

   <td width="180">2</td>

   <td width="132">V</td>

  </tr>

  <tr>

   <td width="312">Signal-to-noise ratio (<em>V</em><em>id,rms</em> = 10mV/2)</td>

   <td width="180"> 77</td>

   <td width="132">dB</td>

  </tr>

  <tr>

   <td width="312">Signal bandwidth</td>

   <td width="180">1 – 5k</td>

   <td width="132">Hz</td>

  </tr>

  <tr>

   <td width="312">CMRR</td>

   <td width="180">90</td>

   <td width="132">dB</td>

  </tr>

  <tr>

   <td width="312">Power dissipation (<em>I</em><em>DD</em> × <em>V</em><em>DD</em>)</td>

   <td width="180">Optimize</td>

   <td width="132">mW</td>

  </tr>

  <tr>

   <td width="312">Cost</td>

   <td width="180">Optimize</td>

   <td width="132">$</td>

  </tr>

 </tbody>

</table>

<strong> </strong>Recommended design approach

<ul>

 <li>Determine the input-referred <em>voltage noise density</em> required to meet the specifications.</li>

 <li>Perform noise analysis of the instrumentation amplifier and determine the relative impact of all noise sources on the input-referred noise.</li>

 <li>Be sure to include the noise from the strain gage resistance. You should model the strain gage as a Thevenin equivalent circuit.</li>

 <li>Use the first stage to realize the required gain. This will minimize the impact of <em>U</em><em>3</em>’s noise, as well as that of <em>R</em><em>1</em> and <em>R</em><em>2</em><em>.</em></li>

 <li>Select component values that allow you to achieve the noise target, with resistor tolerances that make it possible to meet the CMRR specification.</li>

 <li>Use Digikey’s or Analog Devices’ component selection tables to select opamps that meet the requirements. Note that one limitation here is that the opamps you use have available SPICE models that include noise. Many of Analog Devices’ models are already available in Ltspice. For any that aren’t, you just need to import the SPICE netlist and create a new component (Ltspice will autogenerate the symbol for you, but you can also create a custom symbol).</li>

 <li>Take a systematic approach, rather than trying to simulate the amplifier straight away and “guess” at the component values.</li>

</ul>

<strong>Note on supply voltage and input range:</strong> <em>You need to ensure that both the single-ended supply voltage of 5V and the nominal sensor output voltage (5V/2 = 2.5V) are compatible with your opamp selection. The small sensor output swing of </em><em>5mV won’t be an issue for any opamp worth using. </em>

<strong>Flicker (</strong><strong><em>1/f</em>) noise: </strong>Some CMOS opamps exhibit particularly high <em>1/f</em> corner frequencies (<em>f</em><em>c</em>), which can significantly degrade your SNR. This can often be seen by the <em>e</em><em>np-p</em> parameter provided in many datasheets (or the ‘<em>0.1 to 10Hz VNoise</em>’ parameter in Analog Devices’ opamp selection table). If your noise simulation result seems higher than expected, make sure your noise isn’t being dominated by flicker noise.

<h1>Phase 1 deliverables</h1>

5-10 slides detailing the following:

<ol>

 <li>Input-referred noise target based on the specifications</li>

 <li>Expression showing the relative contribution of each noise source on the input-referred noise. Justify any assumptions.</li>

 <li>Complete schematic showing the strain gage model, supply voltages, opamp models, resistor values, and DC operating point voltages at all nodes</li>

 <li>AC simulation results showing the frequency response of the amplifier</li>

 <li>Input-referred noise plot showing the noise density at 1kHz, along with the integrated noise from 1Hz to 5kHz.</li>

</ol>