## Aim

The goal of the work was to solve the problem of Cognitive Radio (CR) using a low computation solution. Spectrum sensing is one of the most important problems in CR which is the process of identifying occupancy in the spectrum space i.e. the task of identifying if a frequency channel is being used. The idea of CR is based on the observation that a lot of the times, most of the licensed spectrum is not being used by the licensed users. In such cases, secondary (unlicensed) users detect the spectrum holes (unoccupied spectrum) and utilize the spectrum leading to an efficient spectrum utilization.

[Report](/pdf/CSprojectfinalreport.pdf)
[Publication](https://ieeexplore.ieee.org/abstract/document/6749450)

## Motivation

Nyquist-Shannon theorem states that every band-limited signal can be recovered from its discretization if it's sampling rate is at least two times it's cut off frequency. For CR, where wide band signals are typical, this can mean a lot of samples that would need to be acquired causing computational burden on the acquisition device.

## Solution

We identified the problem of CR as a detection rather than an estimation problem. In order to check the occupancy of a channel, we only need to detect if the spectrum is utilized or not, and the actual message signal is not of importance to us. Therefore, we don't need to reconstruct the signal. The novelty in our solution was to formulate CR as a detection problem rather than an estimation problem and using Compressed Sensing (CS) which requires far fewer samples than stated by Nyquist-Shannon criterion.

Compressed sensing states that the you can recover a signal using samples much fewer than stated by Nyquist-Shannon criterion provided the signal exhibits sparsity. In CR, where multiple different frequencies are being used by different primary users, the Fourier Transform (FT) of the signal would show spikes at the respective frequencies being used. Therefore, the resulting spectrum after FT exhibits sparsity making CS a natural solution to our problem in CR. Traditional compressed sensing techniques can be computationally intensive at the receiver end while reconstructing the signal. Our solution avoids recontruction and leads to computational advantages requiring only ~10% of the samples/measurements to perform spectrum sensing compared to traditional techniques. The solution involved solving an undetermined system of equations under the constraint of sparsity.

<img src="images/CS_1.PNG?raw=true"/>
<img src="images/CS_2.PNG?raw=true"/>
<img src="images/CS_4.PNG?raw=true"/>