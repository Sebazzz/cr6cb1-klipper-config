# CR-6 SE klipper config

My CR-6 SE klipper configuration based on [my Voron V0.2r1](https://github.com/Sebazzz/moronv0-klipper). It assumes the installation of the [BTT Mantra M4P](https://github.com/bigtreetech/Manta-M4P/) with [BTT CB1 board](https://github.com/bigtreetech/CB1/), and that the CB1 also itself [has also been set-up as a Klipper MCU](https://www.klipper3d.org/RPi_microcontroller.html).

Read more [on my Voron build on my website](https://damsteen.nl/blog/2023/12/29/ldo-voron-v02-build-notes).

## Features

- Split all the important configurations (like homing configuration) to separate config files
- Use audio cues for important events like filament loading and print start
- Bed lightning represents the printer state
- Filament sensor auto-loads filament
- Support gcodes
   - M300 *beep*
   - M600 *filament change*

## Usage

Download all the files by going to the green "Code" button, and then selecting "Download ZIP".
Then upload all the configurations to your Klipper instance.

Then modify the MCU paths in [`configs/mcu.cfg`](./configs/mcu.cfg) to point to your MCUs.

In your slicer use the following start-gcode:

```
SET_PRINT_STATS_INFO TOTAL_LAYER=[total_layer_count]
PRINT_START EXTRUDER=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer_single]
PRINT_INIT_HOTBED_TEXTURED  # One of these
PRINT_INIT_HOTBED_SMOOTH
```

Use the following `PRINT_END`:

```
PRINT_END
```
