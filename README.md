# Noise Canceling Fan Project

A desktop fan that cancels its own noise using active noise cancellation, built utilizing CAD, embedded programming, signal processing, and acoustic analysis to create a standalone product! 



<div style="display: flex; justify-content: center; align-items: center; gap: 50px;">
  <img src="Media/Final_CAD.jpg" alt="Final CAD model of fan" style="width: 270px; height: auto;" />
  <img src="Media/FinalX_sect1.jpg" alt="Cross-section of fan CAD model" style="width: 270px; height: auto;" />
  <img src="Media/Prototype_Crop.jpg" alt="Photo of physical fan prototype" style="width: 161px; height: auto;" />
</div>

---

## What It Does

This fan detects its own blade-generated noise using a microphone, identifies the dominant frequency using an FFT (Fast Fourier Transform), and cancels it in real time by outputting inverted sound through a speaker

---

## How it Works  
1. Error microphone near the fan records raw noise and sends to the microcontroller 
2. The noise data that is sent to the microcontroller from the mic is processed by FFT in the PJRC Audio library.
   - This identifies the major contributing frequency
4. Once the specific frequency is identified, the signal is shifted by 180 deg, and the amplitude/phase are adjusted. The signal is played out of the speaker using AudioConnection 
5. An error mic at the shroud mouth picks up residual sound at the original frequency. The algorithm continues to optimize amplitude and phase to minimize residual sound. 
---

## Testing 
- Ran modal FEA to ensure that the housing doesn't resonate at the fan's blade pass frequency of 172 Hz.
    - Found main vibrational mode at 350 Hz. Well out of range for resonance.
- Conducted bench testing
    - Bench/smoketest is complete. Error mics and speaker mounted and connected to Teensy. 
## Status/Next Steps
- Bench testing is now complete. All components - speaker, mics, Teensy, and fan connect to each other and mechanically fit into the shroud and base. 
- Next steps will be rewiring everything into the 3D printed housing, taking decibel measurements, implementing the algorithm (possibly replace FFT with Goertzel), and creating a PCB to replace the breadboard.

---

## CAD Model Links
| [Part](link)                                                      |   Description  
| [Box](CAD/Project_CAD/box.SLDPRT)                                 |   Box that forms the base. Houses electronics.   
| [Lid](CAD/Project_CAD/lid.SLDPRT)                                 |   Lid that fits flush with top of base. Mounts to support tube with screws.  
| [Support_Tube](CAD/Project_CAD/tube.SLDPRT)                       |   Vertical support tube that rises from lid to shroud. Houses wiring.   
| [Fan_Housing_Front_Plate](CAD/Project_CAD/Fan_Front_Plate.SLDPRT) |   Circular plate that sits in front of fan to create circular profile to fit into shroud.   
| [Fan_Housing_Back_Plate](CAD/Project_CAD/Fan_Back_Plate.SLDPRT)   |   Circular plate that sits in behind fan to create circular profile to fit into shroud.   
| [Fan_Shroud](CAD/Project_CAD/Shroud.SLDPRT)                       |   Horizontal cylinder that houses fan, microphone, and speaker. Connects to support tube at bottom.      
| [Final_Assembly](CAD/Project_CAD/Final_Assembly.SLDPRT)           |   Final assembly of shroud, tubewith holes, lid, and base.

---

## [DevLog](DevLog.md)
