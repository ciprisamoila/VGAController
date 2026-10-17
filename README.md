# VGA Controller

VHDL/Vivado project for generating VGA graphics on a Digilent Basys3 FPGA board.

## Features

- 640×480 VGA output with a 25 MHz pixel clock
- Horizontal and vertical synchronization
- Selectable square, triangle, circle, and diamond shapes
- Movable figures controlled by the Basys3 buttons
- Selectable foreground and background colors
- Optional UTCN logo rendering using hardcoded pixel-coordinate switch cases
- Button debouncing and reset support

## Project structure

The main design is `Tester.vhd`, which connects the following modules:

- `Frequency_Divider.vhd` — creates the 25 MHz pixel clock from the 100 MHz board clock
- `VGA_controller.vhd` — generates VGA timing and pixel coordinates
- `center_calculator.vhd` — controls the figure position
- `Draw_*.vhd` — generates the available shapes
- `Color_Selector.vhd` and `BGColor_Selector.vhd` — select RGB colors
- `Debouncer.vhd` — filters button inputs
- `Draw_Memory.vhd` — contains the hardcoded UTCN logo pixel-coordinate cases

## Usage

Open `VGA_Project/VGA_Project.xpr` in Vivado, synthesize the project, generate the bitstream, and program a Basys3 board connected to a VGA display. Switch and button assignments are defined by the project constraints.
