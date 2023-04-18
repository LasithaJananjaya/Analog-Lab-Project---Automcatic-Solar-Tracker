# lab_project_solar_tracker
Semester 3 Analog Lab Project.
Automatic Solar Tracker
## Abstract
This project aims to address the challenge of optimizing solar panel energy generation, given that the efficiency of current solar technology is affected by the intensity of sunlight and angle of incidence. The demand for solar power has increased worldwide as a preferred green energy alternative to non-renewable energy sources. To achieve the highest efficiency, an analog PID control circuit is designed to dynamically adjust the angular position of a solar panel along a single axis. This will enable the panel to optimize its generation of electricity, even under varying lighting and positional circumstances.

## Introduction
In contemporary times, the global community has been fervently exploring alternative energy sources, with a keen focus on renewable sources that can mitigate the adverse environmental impact of traditional energy sources. Among the plethora of renewable energy sources, solar energy has emerged as one of the most abundant and clean sources of energy on the planet. The harnessing of solar energy can be achieved through two main methods, namely, photovoltaic (PV) cells and solar thermal systems. Solar panels, which typically contain multiple solar cells, are employed to generate electricity using solar energy. These panels are installed in locations that receive direct sunlight, such as rooftops or solar farms, which may contain millions of solar panel arrays in desert areas. The utilization of solar energy through these methods offers significant potential to contribute to sustainable development and reduce dependence on non-renewable energy sources. 

A significant challenge facing solar panel technology is the inherent limitation that the maximum efficiency can only be achieved when the panel receives direct sunlight, i.e. when light strikes the panel perpendicularly. This constraint restricts the optimal efficiency of the panel to specific time periods during the day when the angle of incidence of the sun’s rays is perpendicular to the panel.

To overcome this constraint and enhance the efficiency of solar panels throughout the day, automatic solar trackers have emerged as a potential solution. These trackers are designed to enable solar panels to automatically align with direct sunlight, thereby maximizing the energy capture potential of the panel.

The incorporation of automatic solar trackers represents a significant advance in solar panel technology, enabling panels to achieve greater efficiency and reducing the environmental impact of energy production. By automatically adjusting the panel’s orientation to align with the sun’s rays, solar trackers offer a practical and effective means of maximizing energy output and promoting sustainable energy practices.

## Functionality Description
First, the two **LDR sensors** sense the intensity of the light that directly falls on. According to those parameters the resistances of the two sensors are varied. According to the design, if the resistance values of the two sensors are equal, the panel should remain still and if there is a difference, the panel should turn accordingly to reduce that difference. The panel is rotated using a motor and the motor is driven by a **PWM Control Signal**. If the duty of the PWM signal is 50%, the motor is not driven. Otherwise, the motor is driven in the required direction. The smooth operation of the motor is ensured by the **PID Controller**.

## System model
### Block Diagram
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/block_diagram.jpg)

### Design Parameters
* Operating Voltage - 12 V
* Reference Voltage - 6 V
* Light Sensor - 12 mm LDR
* LDR Dark Resistance - 1MΩ
* LDR Light Resistance - 5 - 10 kΩ
* OPAMP Selection - UA741CP, LMC660CN and TLC372CP
* Motor Driver - L298N
* Motor - RK-370CA-18260 DC Motor
* Motor Stall Current - 300 mA
* PCB - 4 Layer, Manufactured and imported from JLC PCB (China)
* Enclosure Material - Wood

## Schematic
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/schematic.jpg)

### Difference Amplifier
The difference between the input voltage and the set point voltage of 6 volts is being amplified
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_difference_amplifier.png)

### PID Controller - Proportional Part
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_proportional.png)

### PID Controller - Integral Part
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_integral.png)

### PID Controller - Derivative Part
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_derivative.png)

### Weighted Summing Amplifier
The Proportional-Integral-Derivative (PID) controller outputs are weighted and combined using appropriate algorithm. Specifically, larger resistors are incorporated into the design of the I and D controllers to ensure their effect on the overall operation of the PID controller is suitably reduced. This measure is essential for achieving a stable and effective PID control system.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_weighted_summing_amp.png)

### Voltage Buffers
Voltage buffers have been employed to provide isolation between the input stage and output stage. To accomplish this, we have utilized an operational amplifier with a higher input impedance. This strategic implementation aims to minimize the loading effect and signal distortion that may occur between the two stages, thus ensuring optimal performance of the circuit. The incorporation of voltage buffers and an operational amplifier with higher input impedance serves to enhance the overall reliability and robustness of the circuit, while simultaneously minimizing potential signal loss and distortion.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_vbuff.png)

### Triangular Wave Generation
The generation of a triangular waveform within the range of 0-12V and with a frequency of 500Hz is accomplished through the utilization of a Schmitt trigger and an integrator circuit. Specifically, the frequency of the waveform is tailored through the adjustment of resistor R13, which serves as a key variable in the control of the wave form’s frequency. Additionally, the threshold voltage is adjusted by maintaining a ratio of approximately unity between resistors R2 and R17, thereby ensuring that a nearly uniform amplitude variation of 0-12V is achievable.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_triangular.png)

### PWM Generation
The pulse-width modulation (PWM) waves, which correspond to the control signal generated by the PID controller, are synthesized by the comparator through the utilization of a triangular waveform.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/4_PWM.png)

## PCB design
The Printed Circuit Board (PCB) comprises a total of four layers, of which the Top and Bottom layers function as two distinct signal layers. An additional layer is dedicated to ground pour, while another accommodates 12V and 6V pours, thereby providing a comprehensive and multifaceted platform for the effective transmission and distribution of electrical signals. The use of these multiple layers not only ensures the efficient utilization of space on the PCB but also facilitates the effective management of electrical energy, thereby enhancing the overall functionality and reliability of the circuitry without any effect of unnecessary noise.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb.jpg)

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb_3d_model.jpg)

### Top Layer
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb_top_layer.jpg)

### Bottom Layer
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb_bottom_layer.jpg)

### Layer 1
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb_layer_1.jpg)

### Layer 2
![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/pcb_layer_2.jpg)

## Enclosure design
The base of the structure measures 30cm x 10cm x 1cm and is designed to be affixed to a surface using screws. The entire assembly consists of the structure that holds the solar panel, motor, and printed circuit board (PCB). The solar panel is fixed to a frame that is supported by two arms, which have dimensions of 26cm x 5cm x 1cm. These arms are inserted into specially designed grooves in the base and secured in place with glue. A rod is used to secure the frame, and the motor, along with the PCB box, is attached to one of the arms using screws. The motor is directly connected to the rod, allowing the frame to rotate. The rod has a diameter of 1cm and a length of 30cm. The frame itself has an inner edge dimension of 30cm x 20cm and an outer edge dimension of 24cm x 14cm. Two light-dependent resistors (LDR) sensors are connected to the distant edges of the frame, which holds the solar panel. Two cylindrical structures with a diameter of 8mm and a height of 15mm are used to cover the LDR sensors, preventing sunlight from hitting the sensors from directions other than perpendicular to the sensor surface. The enclosure of the device is made of wood, and laser cutting is used for manufacturing. The wood panels used are of thickness 6mm and 4mm, and the screw nails used are of 3mm in diameter and 1.5 inches in length. Additionally, the enclosure is designed to hold the PCB and has a hole with a diameter of 2cm to accommodate the wires.

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/enclosure_1.jpg)

![](https://github.com/LasithaJananjaya/Analog-Lab-Project---Automcatic-Solar-Tracker/blob/main/Report/enclosure_2.jpg)

## Conclusion and Future Works
Further tuning of the system is necessary to optimize its performance. Given that the system draws a relatively low power of approximately 1.4 W, it is feasible to explore the potential of powering it with a solar panel. To achieve this objective, it is recommended to incorporate a motor driver with a higher current capacity to accommodate the increased power demands of the system. Additionally, the inclusion of a Buck converter can significantly reduce power wastage and improve the system’s overall energy efficiency. These enhancements are critical to ensuring the sustainable and effective operation of the system and reducing its environmental impact.

## Acknowledgements
We would like to express our deepest appreciation and gratitude to the project supervisors for their invaluable contributions and unwavering support in the successful completion of this report. Their profound expertise, meticulous guidance, and astute insights have been pivotal in ensuring the excellence and effectiveness of this project. Furthermore, we extend our heartfelt thanks to our esteemed colleagues and team members for their unwavering dedication, exceptional competence, and tireless efforts in bringing this project to fruition. Their unrelenting commitment and teamwork have been crucial in overcoming the numerous challenges and obstacles encountered throughout the project’s execution.

In conclusion, we recognize and acknowledge the significant contributions of all those involved in this project, and we remain deeply grateful for their unwavering support, dedication, and commitment to the success of this endeavour.
