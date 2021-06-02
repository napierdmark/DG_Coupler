# DG_Coupler
<p>Couple G502A DG to an autopilot.</p>
<p>If the MIT License does not make it clear, the user bears *all* responsibility to test and validate this circuit.  I cannot control what components are used, how the device is fabricated, what ESD protections are used during construction, and how/if a burn in test is done.  Therefore it is not represented as being useful for anything other than the user's edification.</p>
https://www.youtube.com/watch?v=AaAPO0OWc_Q&lc=Ugy0l8xfBywn3WTVZoh4AaABAg
<p>This technology was mature when Apollo was still a thing.  That in mind it is still reliable but due to all the solid state gyro replacements most owners will be throwing these boat anchors away.  Saves weight and long term cost.</p>
<p>This circuit is intended to work with the Navaid ap-1 similar to the Porcine DG Coupler.  The Porcine unit is no longer available and uses a different DG.</p>
https://www.porcine.com/gps/dg/dg_frameset.html
<p>The DG Coupler uses a 3 position SPST switch to select from 3 different Nav sources.  One throw will select the DG input as well as close a relay that changes the autopilot head sensitivy to the L/R signals.  The other two positions select the steering outputs and flag from the Smart Coupler II LE.  Note that the signals polarity and Reference match the output of the Smart Coupler.</p>
https://www.porcine.com/gps/sc/sc_frameset.html
<h1>Theory of Operation</h1>

<p>Refer to dg_cpl_shts.pdf</p>
<p>Power Supply - Ship power PWR_14_IN is on J1:pin 1.  Power Ground is on J1:pin14.  C18 provides a capacitive short to RF EMI.  U7 is an integrated regulator that includes short circuit overload protection, thermal protection, and limited input voltage overload protection.  Several similar devices are available in the same footprint.  C28 provides local input decoupling.  R25, R28, and R29 set the output to 9 Volts.  C10 and C11 are selected to for output stability.  Refer to the BOM or Parts list for exact components.  Note these are selected for proper impedance over temperature.</p>
<p> Oscillator - The 400 Hz oscillator is made using the 555 timing chip.  Note that components for C4 and C5 are in the BOM and selected for stability over temperature.  The output drives the AC Heading Excite Out (HDG_EXC_OUT) and the syncronous detection circuit.</p>
<p>Heading Excite - The DG reference coil is driven from the resistive bridge made by R32 - R35.  These are larger resistors to dissipate heat.  Q1 provides the switching.  The result with the coil is an alternate ramp waveform.  HDG_EXC is on J1:pin 2. NOTE: the return for this signal is on J1:pin 14.  Recommend twisting this pair of wires to the gyro.</p>
<p>Synchronous Detection - AC_HDG (J1:pin 3) comes from the gyro pick up coil.  The reference side is connected to GNDA (J1:pin 15).  The 400 Hz reference serves to rectify AC_HDG using U1A and U2.  The output signal has a DC average proportional to the heading bug offset.</p>
<p>Filter, Null and Gain - R10, C2 and C27 form a single pole low pass filter.  Additional current is summed at this junction from R9 and RV1 to provide a null adjustment to center up the gyro.  R8 and RV2 form a divider that allows the gain to be adjustable.</p>
