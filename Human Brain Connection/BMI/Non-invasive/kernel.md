# Kernel
## Goal
"At Kernel, our primary goal is to enable improved and accelerated insights into the human brain", by providing Neuroscience as a Service (NaaS) serving online neuroscience studies.  
"Two key factors restricting progress towards understanding the brain":  
1. "Acquiring the best brain signals today requires expensive, complex, and room-sized equipment with the need for full-time, trained technicians. The cost and sheer size of these machines, in addition to the restrictions placed on user movement and experimental environments, limit their scale and potential."  
    -> "Hardware for brain signal acquisition that is low-cost, scalable, easy to use, and that supports natural environments and motion"  
2. "The complexities and diverse requirements for measuring and interpreting neural signals which [...] require input and expertise from a wide array of disciplines[,] including fundamental sensor physics, hardware design, firmware development, experimental design, signal processing, machine learning, and neuroscience."  
    -> Putting expertise in all required areas under one roof  

## Experiments
### 1. Speller
Decoding gaze from brain signals to get the tiles consisting of 26 letters and 10 digits the subjects were looking at.  

### 2. Sound ID
Measuring brain activity to determine what someone is listening to. Two sets of sounds, one with speech and one with songs, were given to the subjects. The subjects then chose from these sets and listened to the sounds. While they were listening, the brain signal was measured and an algorithm determined the probability of each song the person might be listening to. As algorithm, a canonical correlation analysis (CCA) has been used. To train the CCA, the brain and audio signals were downsampled to 100 samples per second. For each time step, 16 sensors recorded data into 32 channels while for each channel the audio envelope has been delayed by 0 to 240ms in 20ms steps to account for the latency of neural responses to external stimuli. CCA acts both as a temporal filter, tuned to isolate the information of most relevance to the perceived stimulus in the brain signals as well as a spatial filter, combining information across channels to achieve maximal correspondence between the stimulus and the brain signal.  
The average correlation values were passed into a softmax operator with an additional parameter controlling how differences in correlation values are amplified in the output, while the output of the softmax function will be used as probability score to rank the sound snippets.  
Results have shown that smaller subsets of sensors (at least 4 sensors) were able to achieve a similar accuracy and confidence level compared to the full set of sensors. Altogehter an accuracy of up to 100% (averaging between 80 and 90%) has been obtained with a softmax probability of up to 1 for the speech. The accuracy and probability for the songs has been significantly lower though with an accuracy more close to 40%, while this still is far more accracte than guessing whihc would result in a 10% accuracy.  

[kernel.com, 12.10.2020](https://www.kernel.co/hello-humanity)