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
The focus of this day was on floorplan and placement steps of the flow. 

Florrplan stage is required to place pins and non-standart cells on an area of a die.

`run_floorplan` is a command to run this stage. Additional switches can be used to customize the floorplan strategy, such as pin allocation.

Figure below shows the finished floorplan run with default configurations.

<img src="Images/Day_2/florrplan/1%20-%20floorplan%20default.png" width= "800" height= "600">

Floorplan generates a def file, fragment of which is shown below.

<img src="Images/Day_2/florrplan/2%20-%20floorplan%20def%20file.png" width= "800" height= "600">

Generated def file allocates mentioned die elements on a grid. Generated configuration can be visualized with _magic_ as a layout. It requires a PDK ***tech*** file, a cell ***lef*** file and a ***def*** file of a floorplan.

<img src="Images/Day_2/florrplan/3%20-%20magic%20layout.png" width= "800" height= "600">

Zoomed in view shows placed pin and decoupling capacitors (non standart cell).

<img src="Images/Day_2/florrplan/4%20-%20magic%20layout%20zoomed%20in.png" width= "800" height= "600">

The next step is to allocate standard cells by running `run_placement` command. Similiar to a floorplan, the placement run can be customized with additional swithces if neeeded.

A finished placement run with default confogurations and generated magic layout shown below.

<img src="Images/Day_2/Library%20and%20placement/1%20-%20placement%20run.png" width= "800" height= "600">

<img src="Images/Day_2/Library%20and%20placement/2%20-%20layout%20after%20placement%20run.png" width= "800" height= "600">

## Day 3

## Day 4

## Day 5
