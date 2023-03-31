# OpenSPS

Open-source Single Photon Detector based on faint-laser technology. Works by generating short pulses that feed a 405nm laser diode, which is attenuated afterwards in order to obtain the desired Poissonian distribution at the final output of the device.

![board](https://github.com/pepassaco/OpenSPS/blob/main/images/board.png)

![spice simulation](https://github.com/pepassaco/OpenSPS/blob/main/images/spice.png)

## IMPORTANT

Currently under testing. I will actively update this repository with measurements and new results as soon as I finish the prototyping stage.

# Electronics

The board consists on an SMA input which should be fed with a square wave of at least 1Vpp amplitude and a maximum frequency of 10MHz. When the voltage passes certain threshold, a comparator is activated. 

The output of this comparator is splitted into two different paths, in which there are two similar but slightly different low pass order-1 RC filters. The fact that these filters have different time constants will result in different slew rates of the (no longer) square pulse at their outputs. These two new signals are fed to two comaprators that recover the square shape, but now one of the signals will have a small delay with respect to the other one. 

Applying an XOR gate to these signals generates a short pulse just during the time they are different (the delay between them). In this way, playing around with the relationship between the time constants of the filters can generate short pulses of different lengths. As it is designed, the output pulses will be 5 nanoseconds wide. 


# Optics

In order to calculate the attenuation needed for our single photon source, we should apply the following calculations: