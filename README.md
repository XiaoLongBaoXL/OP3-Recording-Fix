# OP3 Recording Fix Magisk Module Installer

This Magisk Module fixes the sound distortion when recording in loud environments on the OP3.

## Requirements
* Magisk ([link](https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445))

## Compatibility
This module has been tested on a OnePlus 3 device with:    
* OxygenOS 5.0.8
* Magisk 18.1
* Magisk Manager 7.1.1

## Modified File(s)
This module implements the following changes to ```system\vendor\etc\mixer_paths_tasha.xml```:
```diff
    <path name="speaker-stereo-dmic-ef">
        <path name="speaker-dmic-endfire" />
<!-- #ifdef VENDOR_EDIT -->
<!-- /*zhiguang.su@MultiMedia.AudioDrv , 2016/04/19, mic power high level mode and add adc volume*/  -->
        <ctl name="ADC4 Volume" value="11" />
        <ctl name="ADC5 Volume" value="11" />
        <ctl name="AMIC_3_4 PWR MODE" value="HIGH_PERF" />
        <ctl name="AMIC_5_6 PWR MODE" value="HIGH_PERF" />
<!-- #endif -->
+       <ctl name="DEC4 Volume" value="69" />
+       <ctl name="DEC5 Volume" value="69" />
    </path>

<!-- #ifdef VENDOR_EDIT -->
<!--  [lifei][Multimedia] , 5/7/2017, for recoder stereo control -->
    <path name="speaker-stereo-dmic-ef-other">
        <ctl name="AIF1_CAP Mixer SLIM TX4" value="1"/>
        <ctl name="AIF1_CAP Mixer SLIM TX5" value="1"/>
        <ctl name="SLIM TX5 MUX" value="DEC5" />
        <ctl name="ADC MUX5" value="AMIC" />
-       <ctl name="AMIC MUX5" value="ADC4" />
+       <ctl name="AMIC MUX5" value="ADC5" />
        <ctl name="SLIM TX4 MUX" value="DEC4" />
        <ctl name="ADC MUX4" value="AMIC" />
-       <ctl name="AMIC MUX4" value="ADC5" />
+       <ctl name="AMIC MUX4" value="ADC4" />
        <ctl name="SLIM_0_TX Channels" value="Two" />
<!-- #ifdef VENDOR_EDIT -->
<!-- /*zhiguang.su@MultiMedia.AudioDrv , 2016/04/19, mic power high level mode and add adc volume*/  -->
        <ctl name="ADC4 Volume" value="11" />
        <ctl name="ADC5 Volume" value="11" />
        <ctl name="AMIC_3_4 PWR MODE" value="HIGH_PERF" />
        <ctl name="AMIC_5_6 PWR MODE" value="HIGH_PERF" />
+       <ctl name="DEC4 Volume" value="69" />
+       <ctl name="DEC5 Volume" value="69" />	
<!-- #endif -->
    </path>
```

## Disclaimer
This fix may or may not work on your own device. Try at your own risk. I am not responsible or liable for any damage or loss caused by installing this module.
