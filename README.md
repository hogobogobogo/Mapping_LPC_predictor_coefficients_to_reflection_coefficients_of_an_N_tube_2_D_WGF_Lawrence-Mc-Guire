# Mapping_LPC_predictor_coefficients_to_reflection_coefficients_of_an_N_tube_2_D_WGF_Lawrence-Mc-Guire
This research stems from the motivation to find a system that could analyse voice and resyn- thesize it through the use of another system us- ing the analysis data from the input. This tech- nique in Digital Signal Processing (DSP) is called synthesis-by-analysis and its most known use is in Phase Vocoders. In the first section the sys- tem framework is layed out both for the analysis and synthesis side. What is LPC? How do we calculate the predictor coefficients and of what use can they be for us? Why do we need the Auto-Correlation Function (ACF) for this com- putation? Then the step-down procedure is will be covered in depth to calculate the reflection coefficients ri of an N-tube acoustic tube model. The main goal is to then convert the predictor coefficients ϵi to reflection coefficients ri which are represent the diameter ratio of the two suc- cessive tubelets in the vocal tract model. We would then feed a vocal input to the patch and the synthesizer should be able to more or less model and imitate certain vocal articulations, ei- ther voiced or unvoiced. The output’s formant structure is comparable to the input structure. An implementation is then made in the MaxMSP audio environment, more specifically in the sub- environment ∼gen. A lot of attention has been put in the pre-processing of the input before the analysis takes place. Lastly we evaluate the input and the output by analysing their corresponding wide-band spectrograms

# Max/MSP Patch: 
You can download and get a free trial from the website of Cycling74
https://cycling74.com/downloads

1. Fork the folder 'Patches MaxMsp'
2. Open the 'LPC_toRelfC_VUVswitch.maxpat' patch
# LPC analysis tool
-= Then you'll see an audio player on which you have to click the play button on one audio file. Then Follow the patch cord and bring up the slider. (If the slider is moving instead of sliding, then unlock the screen into 'Edit' mode by clicking the 'Lock pick symbol') 
-= Now click the window 'startwindow' to start the audio, if you're not hearing anything but see an orange volume level on the right bottom, this means you haven't chosen an output audio device -> go to toolbar/options/audiostatus and choose your dedicated output device
-= Go down and change the 3 bottom sliders. The first slider will output the original input, not filtered. The second will take away the filter and show the error signal. Ignore the third  
-= Double click the gen~ object which has 'Levinson-Durbin' commented next to it. This shows the core of the LPC analysis and the mapping of the predictor coefficients to the reflection coefficients. 
-= Check out the plots of the ACF, the filter coefficients, the error signal and also the spectra of all signals are shown here. ALso to check the spectral flatness of the system
-= To see the buffer which contains the Reflection coefficients change, double-click the '~buffer ReflC @samps 512' object. 
-= There's also a pitch followers, zero-x'ing counter and amplitude follower for the control of the synthesis parameters

3. Open the 'LPC_toRelfC_VUVswitch_DUALLATTICE.maxpat' patch
# 2D-Waveguide Filter
-= Make sure the LPC analyis is running and the level meter right-bottom is turned on. If not press the startwindow object in the LPC analysis patch
-= Now turn on the speaker symbol at the bottom
-= and turn up the **LEFT** slider connected slightly
-= If audio is being fed to the linear predictor you should hear the resynthesizer.
-= In the gen object, double click to see the implementation of the acoustic tube model

**------------------------------------------------------------------**

If you don't seem to be able to get sound out of the demo, then play the audio files as follows:

1. Vowel like sound: 
 -= original: vowel.wav  ||  resynthesized: vocalVowelWGF.wav
2. Poetry spoken by male
 -= original: poetry.wav ||  resynthesized: vocalPoetryWGF.aiff
