# OpenLANE_SKY130
For OpenLANE/SKY130 workshop 2021

The purpose of this workshop is to introduce audience to the openLANE - an open source flow to for a physical design of electronics. The main purpose of this project is to automate the design flow, from RTL to GDSII.

Currently, this workshop is designed around Skywater 130nm PDK, which was recently was made made open source.


## Day 1
This day is focused on introduction of the OpenLANE as an open source design flow.

OpenLane begins with initialization with `./flow.tcl` command run in main openLANE directory. This command would automatically run all design steps required to get legal GDSII file.

`./flow.tcl -interactive` will run the openLANE session in interactive mode, where each step of a design flow could be adjusted and launched by user.

Next step in interactive flow is `package require openlane 0.9`, which activates packages required for openLANE.

`prep -design picorv32a` will configure the selected cell (_picorv32a_ in this example) for a design by merging required LEF files.

<img src="Images/Day_1/1.png" width= "800" height= "600">

Once the cell LEF file is configured, the cell is ready for Synthesis - one of the first major steps in a design flow.

`run_synthesis` command will launch sysnthesis process in openLANE.

<img src="Images/Day_1/2%20-%20synthesis.png" width= "800" height= "600">

During the synthesis run it can be observed how the cell architecture is automatically configured.

<img src="Images/Day_1/2%20-%20results,%20cell%20count.png" width= "800" height= "600">


## Day 2

## Day 3

## Day 4

## Day 5
