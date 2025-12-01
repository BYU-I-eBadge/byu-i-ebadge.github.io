# Minibadge Tutorial

This tutorial is designed for KiCad 9.0.4.
Download the latest version of KiCad from [kicad.org](https://www.kicad.org/download/).
A KiCad configuration with metric unit settings is assumed.

## Download Minibadge Symbols and Footprints

The Minibadge follows a standard which can be accessed as a set of KiCad libraries for footprints and schematics.

To obtain the files necessary to build your Minibadge, navigate to [github.com/BYU-I-eBadge/minibadge/releases](https://github.com/BYU-I-eBadge/minibadge/releases).

The KiCad symbol and footprint variants can be found on the releases page. On the latest release[^1], download `minibadge_full.kicad_sym` and `MiniBadge_Full.kicad_mod` for this tutorial. Save these in a folder that can be navigated to later.

![minibadge release](../imgs/minibadge_tutorial/releases_page.png)

## Design in KiCad

### Initial Project Setup

Make and open a new project in KiCad. Save it in a directory of your choice. Feel free to name the project something memorable.

![hint make new project](../imgs/minibadge_tutorial/open_project.png)

After making your project, the window should now look something like this:

![created project](../imgs/minibadge_tutorial/project_made.png)

Now that the project has been made, the symbol and footprint need to be added so they are accessible from library browsers. Move the downloaded files into your project folder or somewhere easily accessible.

![created project](../imgs/minibadge_tutorial/relocated_files.png)


Navigate to `Preferences` on the toolbar.

![go to preferences](../imgs/minibadge_tutorial/preferences.png)

Then, go to `Manage Symbol Libraries`.

![go to manage symbol libraries](../imgs/minibadge_tutorial/manage_symbols_highlighted.png)

A new window will appear. Navigate to the `Project Specific Libraries` tab to add the Minibadge symbol to this project only.

![switch tabs](../imgs/minibadge_tutorial/sym_switch_tabs.png)

Once switched to the correct tab, click the button with the folder icon to open the downloaded symbol library.
**For KiCad symbols, open the `*.kicad_sym` file to add the library.**

![add symbol library button](../imgs/minibadge_tutorial/add_sym_library.png)

Select the `minibadge_full.kicad_sym` file from the folder it was stored in and open it.

![add symbol library file](../imgs/minibadge_tutorial/add_sym_lib_file.png)

Next, to avoid any pathing related errors, rename the library Nickname from "minibadge_full" to "Minibadge" (case-sensitive).

![add symbol library file](../imgs/minibadge_tutorial/rename_sym_nickname.png)

The Symbols Library Window should now look something like this:

![point out symbol libraries are files](../imgs/minibadge_tutorial/sym_is_file.png)

Press OK to save changes and close the window for managing symbol libraries. It may take a moment for the library to load into the project.

In preferences again, navigate to manage footprint libraries.

![go to manage footprint libraries](../imgs/minibadge_tutorial/manage_footprint_highlighted.png)

Similar to the window for managing symbol libraries, navigate to the `Project Specific Libraries` tab.
Click the button with the folder icon to open the downloaded footprint library.
**For KiCad footprints, open the folder that contains `*.kicad_mod` file(s) to add the library. This can reside in the same directory as your symbol library and other files; KiCad will only inventory the `*.kicad_mod` files from the selected folder.**

![add footprint library button](../imgs/minibadge_tutorial/add_footprint_lib.png)

Navigate to the folder which contains the `MiniBadge_Full.kicad_mod` file and click on the "Select Folder" button or any equivalent for your operating system.

![add footprint library folder](../imgs/minibadge_tutorial/add_footprint_lib_folder.png)

Once again, change the Nickname to `Minibadge` (case-sensitive).

![point out footprint libraries are folders](../imgs/minibadge_tutorial/footprint_is_directory.png)

You can now press the OK button and return to the main project window.

### Schematic

Now we are ready to build the circuit with the installed libraries.

Enter the schematic editor by pressing the icon in the main window.

![hint enter schematic editor](../imgs/minibadge_tutorial/enter_schematic_editor.png)

A blank schematic will be shown. Start by placing symbols by pressing the highlighted icon or using the shortcut (A).

![initial screen hint add symbol](../imgs/minibadge_tutorial/initial_screen_add.png)

It may take a moment for the symbols to load. A new window will appear that will allow for selecting symbols for components.
Search for the minibadge symbol that was downloaded. Select the one that looks like the one pictured, and press OK to close the window.

![select symbol window minibadge example](../imgs/minibadge_tutorial/select_symbol.png)

The symbol should appear attached to your cursor. Click to place the symbol. If the symbol still appears to follow your cursor after placement, press the ESC key to release your cursor; this is a side effect of having `Place repeated copies` selected.

![symbol on schematic](../imgs/minibadge_tutorial/place_in_schematic.png)

For this tutorial, we will design a basic minibadge that has a simple LED circuit.
Add symbols for an LED and resistor to the schematic by following a process similar to placing the minibadge.

![add additional symbols](../imgs/minibadge_tutorial/place_more_symbols.png)

By double clicking on the resistor, the value can be changed. For this tutorial, the desired resistance is 100Ω, so in the "value" field, "R_US" can be replaced with 100ohm as shown below. Afterwards, press OK.

![change resistance](../imgs/minibadge_tutorial/change_resistance.png)

Now that all the symbols are placed, wires need to be added to connect the symbols together. To draw wires, press the highlighted wire button or press the (W) key.

![add wire](../imgs/minibadge_tutorial/select_wire.png)

Wire the LED anode (the side with the triangle base) to any `+3V3` pin on the minibadge symbol.

Wire the LED cathode (the side with the flat line) to any side of R1.
Wire the unconnected side of R1 to any GND pin of the minibadge symbol.

**It is important that the circuit in your schematic is correct. It is easier to correct schematic issues before starting PCB design, rather than after.**

![wired schematic](../imgs/minibadge_tutorial/wired_schematic.png)

For completeness, the circuit should have its used power paths (3.3V, Ground) labeled and attached to the schematic.
Click on the icon to place power symbols or use the shortuct (P).

![add power symbols](../imgs/minibadge_tutorial/select_power.png)

A window will appear that operates identically to the window for picking component symbols.
For our ground (0V), use the `GND` symbol. Every pin that says `GND` on the minibadge should connect to one of these.

![select ground symbol window](../imgs/minibadge_tutorial/select_gnd_symbol.png)

Similarly, power symbols should be placed for 3.3V. These should go on the pins labelled `3V3+` and `+3V3`.

![select 3.3V symbol window](../imgs/minibadge_tutorial/select_3V3_symbol.png)

The schematic design is nearly complete. Click on the icon to place "no connect flags" on the remaining unused minibadge pins.

![select no connect flags](../imgs/minibadge_tutorial/select_no_connect_flags.png)

Your schematic should now resemble the following:

![powered circuit](../imgs/minibadge_tutorial/powered_circuit.png)

Annotate the schematic so that the design can be checked for errors and be imported to the PCB editor.

![select annotate schematic](../imgs/minibadge_tutorial/select_annotate_schem.png)

Click `Annotate` on the window that appears. The default settings in this window should work for this design.
**Note that this overwrites all reference designators. This may not be ideal for different designs.**

![annotate window](../imgs/minibadge_tutorial/annotate_dialog.png)

Now that the schematic is fully annotated, the Electrical Rules Checker (ERC) should now be run.

![select ERC](../imgs/minibadge_tutorial/select_electrical_rules_checker.png)

Click `Run ERC` on the window that appears.

![run ERC](../imgs/minibadge_tutorial/erc_dialog_run.png)

With the current configuration in the schematic, there should be 2 errors and 0 warnings.
**If there are additional errors, it is likely there is an actual error in the design that needs troubleshooting.**

[^1]: *2025-12-01*. Latest minibadge version 2.1d at time of writing. KiCad Version 9.0.4.

![ERC power errors](../imgs/minibadge_tutorial/erc_power_errors.png)

The reason why these errors occur is because the power symbols (`GND` and `+3.3V`) are technically undefined according to KiCad. To resolve this, we need to specify the power symbols by using a `PWR_FLAG` component.

Open the power symbols window, the same window which had the `GND` and `+3.3V` symbols, and find the `PWR_FLAG` symbol and place it in the schematic.

![power flag symbol](../imgs/minibadge_tutorial/pwr_flag.png)

Now, place two `PWR_FLAG` symbols, one for `GND`, and one for `+3.3V`. Next, connect a `GND` symbol to one and a `+3.3V` symbol to the other.

![power defined schematic](../imgs/minibadge_tutorial/powered_schematic.png)

Rerun the ERC to verify that there are no additional errors.

![fixed ERC](../imgs/minibadge_tutorial/fixed_ERC.png)

After verifying the the design is electrically sound, click the icon to assign footprints to all symbols in the schematic.

![select assign footprints](../imgs/minibadge_tutorial/select_assign_footprints.png)

A window will appear that will assist with assigning footprints to each part.
Footprints are the way that components will physically appear and connect to the board.
When picking footprints consider whether the part is SMD[^2] or THT[^3].
**Make sure the package[^4] matches the actual components.**
For this tutorial, footprints for a 5mm LED and a small through-hole resistor are used.

The exact footprint names used in this tutorial are the following:
D1: `LED_THT:LED_D5.0mm`
R1: `Resistor_THT:R_Axial_DIN0204_L3.6mm_D1.6mm_P5.08mm_Horizontal`

You can search for the exact components by typing in the text box to the right of the Footprint Filters section.

To assign a footprint, select the component you are assigning a footprint to (i.e. D1), and double click on an option from the Filtered Footprints sidebar.

![used footprints](../imgs/minibadge_tutorial/used_example_footprints.png)

[^2]: *Surface-Mount Device.* These components are typically smaller and may be hard to solder by hand.
[^3]: *Through-Hole Technology.* These components are larger and typically easier to solder by hand.
[^4]: The package determines the physical dimensions of a device.
    For simple SMD devices, standard sizes may be used, such as 0603, or 1206.
    For THT devices, ensure the dimensions match or will be compatible.
    This involves verifying pitch between pins or other dimensions.
    **If a datasheet is available, these dimensions should be available and able to be matched with a KiCad footprint.**

Press the OK button.

The schematic portion is now complete. Save your project and close the schematic editor.

### PCB Layout

From the main window, enter the PCB editor by clicking on the icon.

![select PCB editor](../imgs/minibadge_tutorial/enter_pcb_editor.png)

A blank PCB design will appear. Click the icon to update the PCB from the schematic or use the keyboard shortcut (F8).

![select update PCB from schematic](../imgs/minibadge_tutorial/initial_pcb_update_from_schem.png)

A window will appear. Use the defaults and click `Update PCB`.

![update PCB window](../imgs/minibadge_tutorial/update_pcb_dialog.png)

Components will appear on the PCB editor. Close the window an click near the center to place the mess of footprints.

![see added footprints to place](../imgs/minibadge_tutorial/see_added_footprints.png)

Place the LED and resistor inside the minibadge footprint by clicking and dragging.
The resistor and LED should be placed on the back of the minibadge.
With the component selected, either:

1. Right click, then select `Change Side/Flip`.
2. Press `F`.

![flip components hint](../imgs/minibadge_tutorial/flip_components.png)

After arranging components, the design should appear similar to this:

![example footprint placement](../imgs/minibadge_tutorial/after_footprint_placement.png)

Again, note that the resistor and LED are placed on the back.
Minibadges typically are designed so that light can pass through the PCB.
In order for this to work, the design needs an area that prevents copper layers and soldermask from existing in a certain exclusion zone.

Click on the icon for drawing rule areas.

![select draw rule area](../imgs/minibadge_tutorial/select_rule_area.png)

Then, **very intentionally pick a point on the PCB that will be the starting point to draw a polygon for the rule area.**
After clicking a point on the PCB, a window will appear.
Select the copper layers and all relevant keepout rules.
**Do not select the footprint keepout rule because that will include the minibadge itself. Selecting it will cause errors later.**

![rule area window](../imgs/minibadge_tutorial/rule_area_dialog.png)

The default clearance rules are too strict for the minibadge and will throw errors. Fix this by entering the `Board Setup`.

![select board setup](../imgs/minibadge_tutorial/select_board_setup.png)

Select `Constraints` from the categories available. Then, set "Copper to edge clearance" to `0.35 mm`.
Press OK to close the window.

![board setup window](../imgs/minibadge_tutorial/board_setup_dialog.png)

Now that there are constraints and keepouts in place, areas for ground and power planes can be drawn.[^5]

[^5]: Normally, it is a bad idea to have a ground *and* a power plane on a two layer PCB.
    However, because there is only one connection other than power and ground and no rapid switching (like PWM signals),
    this is acceptable.
    Note that other designs may find it favorable to omit the power plane.

First, make sure a copper layer is selected.
Then, select the `Draw Filled Zones` tool, then select one of the corners of the PCB on or outside the `Edge.Cuts` layer.

![select draw filled zones](../imgs/minibadge_tutorial/select_draw_filled_zones.png)

After clicking the initial point to start the polygon drawing for the filled zone, a window will appear.
Select the front copper layer.
Select the `GND` net.
Optionally name the zone "Ground plane".
Press OK when finished.

![ground plane properties window](../imgs/minibadge_tutorial/ground_plane_properties.png)

After drawing the area for the ground plane, repeat the process for the power plane.
The power plane will reside on the rear copper layer.

![power plane properties window](../imgs/minibadge_tutorial/power_plane_properties.png)

Press `B` to refill all copper zones. This will automatically route all connections for power and ground.

Only one connection remains. First, make sure you have the bottom copper layer selected (the power plane), and select the icon to `Route Single Track` or press the shortcut `X`.

The reason we want to have the power plane selected is to avoid splitting the ground plane. Not splitting the ground plane is generally considered good practice.

![select route track](../imgs/minibadge_tutorial/select_route_traces.png)

Click on one of the pads that has a faint line that connects two of them.
The design will appear to be faded, except for the track currently being routed.
Click on the other pad to connect the devices together.

![draw track hint](../imgs/minibadge_tutorial/draw_track.png)

Feel free to readjust the tracks.

Make sure to refill the zones so that the track is isolated from either plane.
Press `B` to refill all copper zones.

![refill zone hint](../imgs/minibadge_tutorial/refill_zone.png)

A silkscreen design should be placed over the light passthrough window.
Designs can be made from images.
Go back to the main KiCad window without exiting the PCB editor, then select the icon for the image converter.

![select image converter](../imgs/minibadge_tutorial/select_image_converter.png)

A new window will open.
Select `Load Source Image` and navigate to the image that will be placed on the PCB silkscreen.

For this tutorial, any image will do, but the tutorial will use the [Github Pages QR code](../imgs/qr_code/main.png).

![select load image source](../imgs/minibadge_tutorial/select_load_source_image.png)

The image will likely not fit within the desired dimension of the window on the PCB.
Return to the PCB editor.
Use the `Measure` tool to record the constraining dimension (whichever is smaller).

![get dimensions of window hint](../imgs/minibadge_tutorial/get_dimensions_of_window.png)

Return to the image converter window.
Make sure to dimension the image to fit in the window using the constraining dimension (height in this case).
If the source image isn't black and white, adjust the threshold and negative.
**Make sure the output format is a footprint on the `F.Silkscreen` layer.**
Press `Export to Clipboard` when done.

![export image window](../imgs/minibadge_tutorial/export_image_to_silk.png)

Return to the PCB editor.
Paste the image using `Ctrl+V` or right click and paste.
Click the place the silkscreen should reside.
An additional reference designator will be pasted alongside the image.
Select it, and press `Del` to delete it.

![delete ref designator for vanity image](../imgs/minibadge_tutorial/delete_ref_for_decor.png)

Light will not ideally escape through the light passthrough window yet.
Soldermask still will be applied over the window unless it is drawn over on the Mask layers.

Select the `F.Mask` layer then the `Draw Rectangles` tool.
After drawing the rectangle in the appropriate spot (over the rule area drawn earlier), select it.
Open the properties by right clicking and clicking `Properties` or using the shortcut key `E`.

![select rectangle properties](../imgs/minibadge_tutorial/rectangle_properties.png)

In the properties, make the rectangle a filled shape.
Double check the layer is correct.

![rectangle properties front window](../imgs/minibadge_tutorial/rectangle_properties_fill_shape.png)

Do the same process for the rear mask.
Ensure the properties are similar to the front mask, especially the filled shape property.

![rectangle properties back window](../imgs/minibadge_tutorial/repeat_mask_delete_rear.png)

Verify the design using the Design Rules Checker (DRC).
Click on the DRC icon.

![select DRC](../imgs/minibadge_tutorial/select_drc.png)

A new window will appear, much like the ERC when the schematic was checked. Select `Run DRC`.

**No errors should appear.**
There should be a warning for the intentionally placed silkscreen clipped by soldermask.
It can be safely ignored.

![DRC safe warnings](../imgs/minibadge_tutorial/safe_drc_warning.png)

# Export PCB for Fabrication

Navigate to the `Gerbers` fabrication output.

![select gerber output](../imgs/minibadge_tutorial/select_gerber_output.png)

Ensure all needed layers are selected.
Select the output directory. Directories relative to the KiCad project are allowed.
After selecting the output directory, click `Plot` to generate the gerber files for each layer.
Afterward, select `Generate Drill Files`.

![gerber plot window](../imgs/minibadge_tutorial/plot_dialog.png)

Another window will appear on top of the plot window.
Ensure the output folder for the drill files is the same as the gerber output directory.
Then, select `Generate`.

![generate drill window](../imgs/minibadge_tutorial/gen_drill_dialog.png)

Close the drill file generation window.
Navigate to the folder with the gerber and drill files.
The easiest way to do this is by using the icon to open the folder with the system file manager.

Use any method to zip all of the files in the directory to make a single output file.
This zipped file will be used for fabricating the actual PCB.

![zip output files](../imgs/minibadge_tutorial/zip_output_files.png)

These instructions assume using JLCPCB as a PCB manufacturer.
This process should be similar for other companies that do PCB fabrication.

On [jlcpcb.com](https://jlcpcb.com), upload the zip file containing your gerber and drill files.

![JLCPCB upload](../imgs/minibadge_tutorial_old/upload_to_jlcpcb.png)

After a successful upload, a preview, cost estimate, and settings will appear.

![preview JLCPCB](../imgs/minibadge_tutorial/post_upload_jlcpcb.png)

The most relevant settings for minibadge designs are:

* PCB Thickness
* PCB Color
* Silkscreen Color
* Mark on PCB

The thickness of the PCB affects parasitic capacitance.
Capacitance decreases inversely with thickness.

Assuming that FR-4 has a relative permittivity of 4.5:

| Thickness (mm) | A (mm^2)  | Capacitance (pF) |
| -------------- | ------- | ---------------- |
| 0.4            | 400     | 39.84            |
| 0.6            | 400     | 26.56            |
| 0.8            | 400     | 19.92            |
| 1.0            | 400     | 15.94            |
| 1.2            | 400     | 13.28            |
| 1.6 (Default)  | 400     | 9.96             |
| 2.0            | 400     | 7.97             |

The default thickness shouldn't cause problems.

Certain PCB colors may take longer to manufacture.

Make sure to select `Remove Mark` so that a JLCPCB order number doesn't appear on the minibadge.

![JLCPCB order settings](../imgs/minibadge_tutorial_old/order_settings.png)

Congratulations! You have finished designing your very own minibadge PCB! The minibadge PCB can now be ordered.

> [Go to Home](../README.md)

---