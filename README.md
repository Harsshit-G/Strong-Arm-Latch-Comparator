# Strong-Arm-Latch-Comparator
This project focuses on the design of A Strong Arm Latch Comparator integrated with IHP-SG13G-OpenPDK on eSim FOSSEE.

# Opensource Tools used
1. eSim (previously known as Oscad / FreeEDA) is a free/libre and open-source EDA tool for comprehensive electronic circuit design. Developed by FOSSEE, IIT Bombay, it serves as an integrated platform built upon existing open-source software like KiCad, Ngspice, and GHDL. eSim provides a complete workflow for schematic capture, circuit simulation, analysis, and PCB design. It offers capabilities comparable to commercial tools like OrCAD and HSPICE, making it an affordable and accessible alternative for educational institutions and small-to-medium enterprises (SMEs) by eliminating the cost of proprietary software licenses. More Info: https://esim.fossee.in/home

2. Ngspice is the open-source circuit simulator for electrical and electronic circuits. It is a powerful derivative of the original SPICE (Simulation Program with Integrated Circuit Emphasis) program developed at Berkeley. Ngspice provides a wealth of device models for active, passive, analog, and digital components, with model parameters often supplied by semiconductor manufacturers. Users define their circuits via a netlist (text-based description), and the tool's output is saved as data files or visualized as graphs of electrical quantities (voltages, currents, etc.). Its robustness and open-source nature make it the default simulation engine for many other EDA projects, including eSim. More Info: http://ngspice.sourceforge.net/

3. IHP-SG13G-OpenPDK: The IHP-SG13G-OpenPDK is an open-source Process Design Kit (PDK) specifically developed for the IHP SG13G technology node, a high-performance Silicon-Germanium BiCMOS process. Unlike generic CMOS PDKs, the SG13G process is optimized for mixed-signal, RF, and high-frequency applications (like those in radar, wireless communications, and sensors). The OpenPDK provides all the necessary files—such as design rules, technology files, and device models (like those for SiGe HBTs)—needed to create manufacturable layouts and run accurate simulations for designs targeting IHP's fabrication facility. By being open-source, it enables broader academic and community access to state-of-the-art specialized semiconductor technology.

# Reference Circuit Diagram
<img width="850" height="507" alt="image" src="https://github.com/user-attachments/assets/53519e3b-ec57-494c-8492-124fa864cdb4" />

# Schematic
<img width="3507" height="2480" alt="image" src="https://github.com/user-attachments/assets/b73e39a9-e63a-40ef-b53b-1aeee69517f4" />

# Netlist
```
.title KiCad schematic
.model __M21 PMOS
.model __M20 NMOS
.model __M8 NMOS
.model __M6 NMOS
.model __M10 NMOS
.model __M19 NMOS
.model __M18 PMOS
.model __M5 NMOS
.model __M7 NMOS
.model __M14 NMOS
.model __M17 NMOS
.model __M9 PMOS
.model __M11 PMOS
.model __M15 NMOS
.model __M16 NMOS
.model __M13 PMOS
.model __M12 PMOS
.model __M4 PMOS
.model __M3 PMOS
.model __M1 PMOS
.model __M2 PMOS
M21 Net-_M13-G_ out2 VDD VDD __M21
M20 Net-_M13-G_ out2 GND GND __M20
M8 Net-_M10-S_ clk GND GND __M8
Vv3 V2 GND DC 0.8 
M6 out1 out2 Net-_M10-D_ GND __M6
M10 Net-_M10-D_ V2 Net-_M10-S_ GND __M10
M19 Net-_M17-G_ out1 GND GND __M19
M18 Net-_M17-G_ out1 VDD VDD __M18
M5 out2 out1 Net-_M5-S_ GND __M5
M7 Net-_M5-S_ V1 Net-_M10-S_ GND __M7
Vv5 V1 GND DC 1 SIN( 1 0 500000 0 0 0 ) AC 0.7 0 
Vv1 clk GND PULSE( 0 2 0.1n 0.1n 0.1n 15n 30n 200 ) 
M14 OUT OUT' GND GND __M14
M17 OUT Net-_M17-G_ GND GND __M17
M9 Net-_M11-S_ Net-_M17-G_ VDD VDD __M9
M11 OUT OUT' Net-_M11-S_ VDD __M11
M15 OUT' Net-_M13-G_ GND GND __M15
M16 OUT' OUT GND GND __M16
M13 OUT' Net-_M13-G_ Net-_M12-D_ VDD __M13
M12 Net-_M12-D_ OUT VDD VDD __M12
M4 out1 clk VDD VDD __M4
Vv4 VDD GND DC 2 
M3 out1 out2 VDD VDD __M3
M1 out2 out1 VDD VDD __M1
M2 out2 clk VDD VDD __M2
.end

```

# Ouput Waveform
<img width="1722" height="842" alt="output" src="https://github.com/user-attachments/assets/53bc551b-7b8f-4ec0-be3e-232461154a16" />

# Conclusion
The Strong-ARM Latch is an effective dynamic comparator, valued for its zero static power consumption and rail-to-rail output swing, making it the architecture of choice for high-speed, power-efficient mixed-signal circuits like ADCs.

#References
1] B. Razavi, "The StrongARM Latch [A Circuit for All Seasons]," IEEE Solid-State Circuits Magazine, vol. 7, no. 2, pp. 12–17, Spring 2015.
2] "Lecture 10: Deriving the StrongARM latch; Introduction to Flash ADC," SSCD IIT Kanpur, YouTube, 2023. [Online]. Available: http://www.youtube.com/watch?v=TfC96c5wgHo
