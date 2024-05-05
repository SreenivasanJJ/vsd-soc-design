# vsd-soc-design
Directory Structure
pdk used is skywater 130 pdk tool which is open source pdk.
 
The open_pdk is used as the skywater pdk may not be foundry compatible and this mitigates this issue. Skywater130A is made compatible for open source environment.
 
libs.ref – contains the timing lib , the cell libs.
 
These are the various cells that are used. fd- foundry, sc – standard cell and hd – high density.
libs.tech – specific to the tool
 
The libs include the lib for each of the cell with the various supported PVT corners. The lef is library exchange format file.
 
The Default configuration for the flow is present in the following directory.
 

Design Setup
‘docker’ is used for running the flows.
  
flow.tcl file contains all the commands and will be used to run all the tools. The openlane tool is open in an interactive mode.
We will be running the flows for the picorv32a design.
Later the design is prepared and in this process the technology level LEF and the cell level LEF is merged.
 
the src directory consists of the design file and constraint. The config file used for the configuration setup for the design. Any of the configuration that needs to be passed can be passed from this file.
 
 
On preparation of the design the output directory is generated which contains merged lef and various other file. The config.tcl contains the information which is taken.
 
 
config.tcl
 
Synthesis
Synthesis related variables
 
Synthesis tool is now run with “run_synthesis” command.
 synthesized chip area
 
Finding the flop ratio
Flop Ratio = Number of flops / Number of cells = 1613/14876  = 0.108 = 10.8%

 
synthesized netlist
 




Floorplan 
Various Floorplan configurations that can be changed 
 
In the Openlane the metal layer will be one more extra than the set value.
To run floorplan – “run_floorplan”
 
The output logs c
 
Floorplan die area:
 
The configuration of CORE_UTIL is taken from the file : 
 
 
Core utilization is 35%, Horizontal IO metal layer is 4(3+1) and Vertical metal layer is 5 (4+1).
The def file contains the floorplan output. 
 
To open the GUI
 
to select entire layout – s . v – to make it centre.
 
 
Tap cells are highlighted which are placed through ought the floorplan with diagonal equidistance. They prevent the latch up condition that can occur.
 The highlighted cell is in metal 3
 
The standard cell are placed in the corner of the floor plan.
Placement
“run_placement”
First global placement occurs which is used to reduce the wire length. 
Half parameter wire length (HPWL) is used in the openlane. Reduction iof this is the main focus. Several iteration takes place and converges.
 
Gui
 
 
All the standard cells are placed and the DRC reports as No error.
 

Day 3
Changing the configuration in runtime
We can see that the IO is placed equividistantly in the floorplan. This is due to IO_MODE Configuration
 
We are changing the value to 2
It will not be equidistant anymore

 
NGSPICE
Creating standard cell design by cloning it from github.
 

 
The inverter std_cell is opened using the magic tool.
Layers of the inverter



 

Creating a std_cell and extracting spice netlist
“extract all” is to create a extraction file. This will be used to create the spice file by using the command “ext2spice cthresh 0  rthresh 0”
 
 
Extraction File
  
Spice file is generated 
 
 
It shows that PMOS and NMOS is generated in the spice. The value of scale is changed and the pmos and nmos libs are included.
The Voltage values are specified and the Input voltage is provided as a pulse with rise and fall time of 0.1ns and high and low period of 2ns.
The transient analysis is performed.
 
 
 
Modifying the Cload to 2fF
 
Characterization 
20% of 3.3V is 0.66V. The value of time is 
 \
80% of 3.3V is 2.64V. The value of time is 
 
Rise Transition = x1(80%) – x1(20%) = 2.247-2.18 = 0.063ns
Rise propagation delay is around 0.0576ns
 
Fall transition time is 0.0438ns approx..
 
Fall propagation delay is 0.025ns
 
Instruction for Magic DRC Tool usage
Download from the web 
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
 
source file for magic drc 
 
 
Creating a VIA on the metal layer.
 
 
There are several DRC errors
Focussing on the poly.9 diagram
 
We will check out the polyresistance and poly distance 
 
It is less 22u hence there will be an error.
 
The tech file is modified to change the distance between them and it is reloaded. We can observe the change and we can see there is no error.
 
 
nwell.mag is loaded
 
We find the DRC in the selected area.
 
 
Vendor DRC rule
 
Finding missing or incorrect rules
 
 
 
On changing to drc full we can obsere the DRC failure
 
 
Day 4
We need to extract lef file from mag file. Then this will be used in our picorv32 model replacing the standard cell inverter.
tracks.info which is used in the routing 
 
 
The grid is changed based on the li track width
 
Width of standard cell should be in odd multiples of X pitch.
It is 3 grid width   
For LEF file we need to define the ports. Now applying the port to it
 
 
The mag file is saved in a separate file and lef is generated.
 
 
Generated LEF file 
 
Now this will ne plugged in to our design
 
The process is started again by adding the libs and merging the lefs. 
 
The synthesis is run and we can observe that the cell is picked up.
 
We can observe that is also presence of slack violation where the worst negative slack is -23.89ns
 
Observing the min max report, we can see the cell consuming huge delay. 
The current chip area is 
 

 
 
We can observe the synth strategy is AREA so the area is optimized. BUFFERING is already present and sizing can be increased to improve timing.
The synth sizing is set to 1 and strategy is set to DELAY to optimize delay.
 
We can observe there is no timing violation.
 
 
The area is increased.

Floorplan and placement is run
 
 
 
OpenSTA for Post Timing Analysis

