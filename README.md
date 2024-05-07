# vsd-soc-design
Directory Structure
pdk used is skywater 130 pdk tool which is open source pdk.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/85082815-7a0f-4bf5-8722-f63188cf5bfb)

The open_pdk is used as the skywater pdk may not be foundry compatible and this mitigates this issue. Skywater130A is made compatible for open source environment.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/9871b2b6-5d20-4c7b-b873-78319b7eb470)

_libs.ref_ – contains the timing lib , the cell libs.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/981351a6-1263-4fa2-a70c-dc07f513a867)

These are the various cells that are used. fd- foundry, sc – standard cell and hd – high density.
_libs.tech_ – specific to the tool

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/550a807d-688b-4ecb-9e57-06035cbfdec6)

The libs include the lib for each of the cell with the various supported PVT corners. The lef is library exchange format file.
 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/87bae0c0-40fd-4551-84a7-d795d8f9fca6)

The Default configuration for the flow is present in the following directory.
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/8e796bac-1501-4d7b-8555-af30cbe7bb29)

**Design Setup**
‘docker’ is used for running the flows.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/f2e4e87b-5649-4344-af29-56db54687426)

_flow.tcl_ file contains all the commands and will be used to run all the tools. The openlane tool is open in an interactive mode.
We will be running the flows for the picorv32a design.
Later the design is prepared and in this process the technology level LEF and the cell level LEF is merged.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/66ac447c-eadd-46f5-8afd-26eff3b909ec)


The src directory consists of the design file and constraint. The config file used for the configuration setup for the design. Any of the configuration that needs to be passed can be passed from this file.
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/2bc1718b-878f-441d-8144-20a4162e24bc)
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/1bf576ea-2606-4cff-86eb-7a49002207ac)
 
On preparation of the design the output directory is generated which contains merged lef and various other file. The config.tcl contains the information which is taken.
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/e842c2f5-20e1-43d8-b334-9df4e50413e0)
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/62b7a940-7881-4347-bbec-0275ebb48c46)

config.tcl

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/63884d4e-5686-4513-87d3-a3f04799b1d3)

**Synthesis**

Synthesis related variables

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/c50f605c-9e8c-4c5b-bc94-3f89e4126372)

Synthesis tool is now run with _“run_synthesis”_ command.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/4ba6f93c-213f-4c73-a829-469c2b0bd763)

Synthesized chip area
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/93595c2e-3c03-47ec-95ef-9c16a917b473)

**Finding the flop ratio**

_Flop Ratio = Number of flops / Number of cells = 1613/14876  = 0.108 = 10.8%_

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/adae6775-954d-488d-8a6e-1b7f038b0b3b)

 
Synthesized netlist

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/771278e9-b9ff-4f25-b3ca-12eb3a956026)

**Floorplan **

Various Floorplan configurations that can be changed 

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/81f1746d-74c0-4c7c-84a2-6ca0f24e7a1e)

In the Openlane the metal layer will be one more extra than the set value.

To run floorplan – _“run_floorplan”_

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/fbd0bd7d-227a-41da-99b7-50aa97aaad62)

The output logs are generated which is shown in the image.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/b125c5bc-a571-4897-82ff-c029abe8c50a)

**Floorplan die area:**

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/397a71a3-351e-47f6-934f-a5d7f4cba519)

The configuration of CORE_UTIL is taken from the file :

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/22fa9c9d-f905-4331-a056-180d7a892e88)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0d1d22a2-2a2d-4524-ac86-755a4644c95e)

 
Core utilization is 35%, Horizontal IO metal layer is 4(3+1) and Vertical metal layer is 5 (4+1).

The def file contains the floorplan output. 

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/54f3f777-5667-4bc5-b424-20d9019924bc)

To open the GUI, type in the command as shown.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/a057615e-ad75-425f-969f-2f9aaefdaeb3)

to select entire layout – s . v – to make it centre.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/3737df27-4651-4a0e-b2d4-336d8c9e56d3)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/8126962f-649b-4cf9-8c40-6114474108a0)
 
Tap cells are highlighted which are placed through ought the floorplan with diagonal equidistance. They prevent the latch up condition that can occur.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/afc71fd4-f4ef-4cc8-9b1c-5d426caad07f)

The highlighted cell is in metal 3
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/7f0a44f4-ce1d-4018-84cf-5f2282db3067)

The standard cell are placed in the corner of the floor plan.

**Placement**

_“run_placement”_

First global placement occurs which is used to reduce the wire length. 

Half parameter wire length (HPWL) is used in the openlane. Reduction iof this is the main focus. Several iteration takes place and converges.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/52bc8db8-b93d-4c11-8a59-84d99359ed30)

**Gui**

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ec4a7f86-9ce6-445e-8a0c-8ab5ae28866c)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/9468979e-dc26-4391-8257-a8bfab9fac48)
 
All the standard cells are placed and the DRC reports as No error.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/077d8309-09f8-4f20-bd31-2e71b473e5fd)

**Day 3**

Changing the configuration in runtime

We can see that the IO is placed equividistantly in the floorplan. This is due to IO_MODE Configuration

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/f0536397-e68f-4885-b8fc-aa19f076d985)

We are changing the value to 2. It will not be equidistant anymore

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/a6ba5955-0a84-4644-925d-20c6a232c7f8)

**NGSPICE**

Creating standard cell design by cloning it from github.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/6de5a9d0-66ce-4da4-a585-c525d6afa07c)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/784f3ab2-888f-414d-b869-a8e5f9144c74)
 
The inverter std_cell is opened using the magic tool.

**Layers of the inverter**

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/8652dbfa-40b0-491a-b685-c0bb038e409c)

**Creating a std_cell and extracting spice netlist**

“extract all” is to create a extraction file. This will be used to create the spice file by using the command _“ext2spice cthresh 0  rthresh 0”_

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0e187f03-5e18-4096-90eb-4ac993cbaa76)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/8652e009-246d-4fdd-ad1d-cd59beb45719)

**Extraction File**

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/d73a3c9e-17b4-46fb-b100-0349850d7270)

Spice file is generated 

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ae2bce0b-00bd-4f00-8763-a55c8266c3c1)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/5aa59880-37ae-441a-80fa-1ea57e1bc51e)
 
It shows that PMOS and NMOS is generated in the spice. The value of scale is changed and the pmos and nmos libs are included.
The Voltage values are specified and the Input voltage is provided as a pulse with rise and fall time of 0.1ns and high and low period of 2ns.

The transient analysis is performed.
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/d30ec2b2-6c52-42e3-9995-ad6a6b80c29e)
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/98cbdaa2-18f6-40c2-a688-4188ee03e328)
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/34dcdaa1-50c7-48f4-82a9-e32fe2419cc1)

Modifying the Cload to 2fF

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/7e3a2ada-9061-443f-abd0-ccbcb393f4f1)

**Characterization **

20% of 3.3V is 0.66V. The value of time is 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/dbac4a6b-6519-4345-adfb-2660165a83ab)

80% of 3.3V is 2.64V. The value of time is 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/631031ac-3359-49b3-9eb8-7163e33e2268)

Rise Transition = x1(80%) – x1(20%) = 2.247-2.18 = 0.063ns

Rise propagation delay is around 0.0576ns
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/64e914d4-67d8-4299-8f0c-bff37705e83f)

Fall transition time is 0.0438ns approx..

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/5b6f2c59-d7ab-4811-95c3-fa4ff12ab1fb)

Fall propagation delay is 0.025ns

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/530cb6ec-26f2-4218-b079-1bd88f48aa2d)

**Instruction for Magic DRC Tool usage**

Download from the web 
_wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz_

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/aecc632f-84bc-4b23-a60c-076b217d46a7)

source file for magic drc 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/9563142b-86a9-4a12-a262-28126c68e71e)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/3dfcbe99-6095-429b-8007-b389eca477a6)
 
Creating a VIA on the metal layer.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/aaf0bf45-12c9-44c9-911e-26af030976e5)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/80102a79-c9bb-4b37-97e0-a07985c37a7d)

 
There are several DRC errors

Focussing on the poly.9 diagram

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/629f5c17-45e6-442c-99b0-3956a76b4ef0)

We will check out the polyresistance and poly distance 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/876fdf9b-b9bc-4641-9fef-99bf51edd4a9)

It is less 22u hence there will be an error.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0e7a64b2-ca3f-4bcc-ab01-1cc638c57965)

The tech file is modified to change the distance between them and it is reloaded. We can observe the change and we can see there is no error.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/2455e5d9-f296-4846-8bdd-88caa14663f6)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/60aaa019-80c1-4279-b7ba-3ace82ef57ab)

 
nwell.mag is loaded

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/388f732b-1507-4347-8518-d10e3196bee8)

We find the DRC in the selected area.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/2f676d72-1a97-4e27-bdc6-321b50049939)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/96ce34e0-e455-4233-aced-53d617161f5b)

 
Vendor DRC rule

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0a040cd9-f3a4-4903-b96f-e8955076c270)

Finding missing or incorrect rules
 
 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/b003a5cb-453d-4880-9973-df6eb202c6c7)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/4da088f5-d93d-4c65-98d9-a9660a2f8e6c)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/c8a24af2-1978-448f-a241-0ed0e9031e31)

 
On changing to drc full we can obsere the DRC failure
 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/62efcdc9-800e-4876-a392-d02fca49b723)
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/a3ebc7d9-b6ba-4e4e-8950-0985e6ce4bd0)
 
**Day 4**

We need to extract lef file from mag file. Then this will be used in our picorv32 model replacing the standard cell inverter.
_tracks.info_ which is used in the routing 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/717dc020-a055-4975-8847-4d9ad1937b19)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/dd8b1830-1a8c-4f26-b921-744ebcfd47a0)
 
The grid is changed based on the li track width

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/5a3e0e6a-c0e6-45fb-9094-515a8426cd4c)

Width of standard cell should be in odd multiples of X pitch.

It is 3 grid width   

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ced1876d-2266-46a0-9e79-f1639a5c9b5d)

For LEF file we need to define the ports. Now applying the port to it

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/819e73b2-806c-4235-8dad-ee65ba571cf6)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/b52558d3-0d8b-4ee8-a9de-5ada0b7221bb)

The mag file is saved in a separate file and lef is generated.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/45876297-ebb2-40cf-b4f9-87bb4f40dc89)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/24ef730e-98b0-479d-b96d-1032af0ece9b)
 
Generated LEF file 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/26b0dd55-74b1-40af-aef4-4778063cb3af)

Now this will ne plugged in to our design

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/3b375fcd-abeb-40cb-94bb-3f25b0b39993)

The process is started again by adding the libs and merging the lefs. 

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/cd7b32b2-8442-4af3-848a-a1f8ab64cb4a)

The synthesis is run and we can observe that the cell is picked up.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0c5d090a-dd6a-4918-9a22-5b343663b543)

We can observe that is also presence of slack violation where the worst negative slack is -23.89ns

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/d7a4c312-4eea-4e73-b38c-9c6925fc1be2)

Observing the min max report, we can see the cell consuming huge delay. 

The current chip area is 
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/6529720b-4fed-47b6-b415-964758c10613)

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/563f0e72-6b28-4a89-a68b-0db0e4093f7c)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/3bb3f32c-800d-40f0-9ea1-1cb10c31936f)

 
We can observe the synth strategy is AREA so the area is optimized. BUFFERING is already present and sizing can be increased to improve timing.
The synth sizing is set to 1 and strategy is set to DELAY to optimize delay.

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/d9f593f5-d6c1-46a5-9caf-c030ffb1a213)

We can observe there is no timing violation.
 
 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ed7ddbe9-4c27-4ba8-afb5-5392a03f77fa)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ea16b890-fe46-4bf3-9591-58163ddb9de4)

The area is increased.

Floorplan and placement is run
 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/4dd56def-6f83-49be-9a71-57f79be893fb)
 
![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/8014df79-5490-4084-b4f7-e06bcfb22b85)

 ![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/998aa334-1999-4a80-be99-1269dae2e1db)
 
**OpenSTA for Post Timing Analysis**

Creating pre_sta.conf file and my_base.sdc file

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/2ba50779-6942-446d-8e99-85edde1c2c41)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/1830ed94-9bd4-46f5-a48d-ed81fbdc4e88)

Now Running STA _“sta pre_sta.conf”_

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/eeea3166-2b9f-46cc-8dff-95ef263460d9)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/5c5c5213-f792-460d-a945-c3513829694c)

The fanout is huge as the fanout value used is 6 so we reduce it to 4. The Total negative slack has reduced a bit but wns is still not changed much.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/1be42c33-107e-4def-8632-c7889781b104)

The cells that consume higher delay are changed to have bigger cell. By this we have achieved to reduce the wns.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/2d222759-14b6-40ac-b1ea-2619736e18bc)

_“write_verilog”_ command is used to write it into a file. We overwrite this to the current synthesis file.
Placement is performed with the generated netlist.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/d9bcd454-af8b-41e0-bbdd-281d82b1c4f7)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/99151403-43ea-49c7-8869-ae711306085d)

**Clock Tree Synthesis**

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ff673c8b-82be-48d3-8bec-b9f66129eff5)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/1269e7b0-703e-417d-be3d-e855b9f1cd54)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/e2a27ebc-a196-4268-8672-d18d8137c2ef)

The limitation of TritonCTS is that is optimized to provide clock tree only for the typical library and does not include all the corners.

**Performing Timing Analysis with Clock Tree**

OpenSTA is already integrated into the openroad. Thus openroad in invoked.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/26a48ce4-4fc8-4cfd-8248-4c2852052f20)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/7616b9c1-77da-48f4-acd6-2d8387a05e28)

We can observe both Setup slack and hold slack is met. This is not a proper analysis as the CTS is only for typical lib. 

**Typical Corner : **

Hold:

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/c9429709-a6fe-44b8-80e8-015a26be46c1)

Setup:

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/b6836e72-b203-4af9-869e-5f69f66bf864)

The Clock Buffer 1 is replaced and then the CTS is rerun.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/e51210df-2865-475e-8149-b5f445da6df2)

The setup slack has improved a bit. 

We can also observe clkbuf_2 is used.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/0525330f-c78d-4188-83bc-1f9f75a0d010)

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/adce62c7-4b03-4586-937f-27f42f5f249a)

**Creating Power Distribution Network**

_gen_pdn_ – runs the pdn.

The std cell row is placed with 2.72 um distance. This has to in multiples of the std cell height otherwise it cannot be placed.

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/9ff32e47-164b-490a-add7-02a9e9a06cb7)

**Routing **

The Routing uses the TritonRouting.

To execute we run the command :_ run_routing_

![image](https://github.com/SreenivasanJJ/vsd-soc-design/assets/56498597/ca862dc0-2221-4865-93cf-05a0e2fb92d8)

