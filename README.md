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

Floorplan stage is required to place pins and non-standart cells on an area of a die.

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

Focus of this day is on a custom cell layout and characterization.

_magic_ is a robust tool for layout visualization, design and characterization. For example, it allows to highlight the placed pins on a die, which were generted with custom floorplan configuration.

<img src="Images/Day_3/1%20-%20ngspice%20inv/1%20-%20aldered%20pin%20distance%20on%20a%20layout.png" width= "800" height= "600">

Moreover, this tool allows to characterize custom cells. Example bellow shows layout of the custom CMOS inverter layout. 

<img src="Images/Day_3/1%20-%20ngspice%20inv/2%20-%20inv%20layout%20in%20magic.png" width= "800" height= "600">

Some basic commands in _magic_ simplifies the operation and characterization of layout components. `what` _magic_ command is used to describe selected layout component, such as nmos.

<img src="Images/Day_3/1%20-%20ngspice%20inv/3%20-%20inv%20layout%20in%20magic%20what%20nmos.png" width= "800" height= "600">

One of the main features of the _magic_ is a layout parasitics extractions as a ***spice*** file.

<img src="Images/Day_3/1%20-%20ngspice%20inv/4%20-%20extracted%20spice%20file.png" width= "800" height= "600">

_ngspice_ is a circuit simulation tool, which can characterize electrical circuits in ***spice***, so it is a usefull tool to study the parasitics introduced by the layout imperfections. 

<img src="Images/Day_3/2%20-%20Sky130%20spice/1%20-%20ngspice%20file%20sim.png" width= "800" height= "600">

Extracted from layout spice file shows numerous sources of parasitic capacitances, so the timing performance of the inverter could be compromised. Capacitive effects could be characterized using transient analysis in spice with _ngspice_.

<img src="Images/Day_3/2%20-%20Sky130%20spice/2%20-%20ngspice%20tran%20output.png" width= "800" height= "600">

_ngspice_ point and click GUI is helpful  in estimation of capacitive dependant characteristics, such as delays, rising and falling times.

<img src="Images/Day_3/2%20-%20Sky130%20spice/3%20-%20ngspice%20timing%20char.png" width= "800" height= "600">

<img src="Images/Day_3/2%20-%20Sky130%20spice/4%20-%20ngspice%20fall%20delay.png" width= "800" height= "600">

<img src="Images/Day_3/2%20-%20Sky130%20spice/4%20-%20ngspice%20RT%20and%20FT.png" width= "800" height= "600">



## Day 4

## Day 5
