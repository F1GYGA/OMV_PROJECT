# OMV Petrom PROJECT
## Description of the project

###  *Purpose of the simulation:*
  
This simulation shows the influence of using capacitor banks when starting the electric motor(GC2-gas compression 2) used in the Petrobrazi refinery which provides pressure for the entire refinery. Without this motor, the refinery would not function given the fact that all the industrial processes need compressed products(gas, air, liquids).  

###  *Description of the phenomenon:*
  
During the starting phase of an electric motor(which is about 18 seconds for our motor), for a couple of seconds, the motor absorbs a very high current, usually 6-7 times the nominal current of the motor. Given the fact that our motor has a nominal current of 739A, during the starting phase, the motor can absorb up to 4.3 kA of current, which even for a couple of seconds is a huge value. High current can have a huge negative impact on electrical installation, forcing all electrical switching and protective devices. To prevent this phenomenon, there are capacitor bank batteries used to correct the power factor and lower the current during the starting phase of the motor.   

###  *The implementation:*
  
Using the Simulink Electrical and Power library, I developed the simulation for starting the motor. The motor is supplied directly from the powerline, which is modeled by a three-phase power supply, and a resistor to model the actual cable resistance used to supply the motor with voltage. I used voltage and current sensors to make sure the model for the motor is correct and we have the current spike described above. The capacitor banks are modeled by a three-phase parallel load, and reflect the real parameters and connection used inside the Petrobrazi refinery. There are two steps, depending on the need for compensation. The model of the motor is an asynchronous machine used as a motor and has almost the exact parameters of the motor used in Petrobrazi. At the output we have various scopes, used to watch different parameters. The most important one is the motor voltage, in which we can see the voltage drop during the starting phase because of the current spike. If we connect the capacitors banks, after the initial drop, the voltage stabilize at almost the nominal voltage, and the absorbed current spike is still present, but at a much lower value than before.
 
###  ***Important notes:***
 
  1. The datasheet of the motor used to implement the values of the motor wasn't complete. I had to use my class materials from the faculty to make various calculations and approximations to get as close to reality. The values aren't exact, but in the end, they reflect the correct phenomenon and the values are true to reality.
  2. During my classes, I did not use the Electrical and Power library, and I had to study and learn how to use various parameters which could influence the result of the simulation. I mainly used the Simulink library in which each component is well described, even with various examples to better understand. 
  3. My mentor helped me to verify each implementation during the development of the simulation, so the result is as close as possible to simulate the actual phenomenon inside the Petrobrazi refinery.
