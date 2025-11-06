# Minibadge Tutorial

This tutorial is designed for KiCad 9.0.3.
Download the latest version of KiCad from [kicad.org](https://www.kicad.org/download/).
A KiCad configuration with metric unit settings is assumed.

## Download Minibadge Symbols and Footprints

Navigate to [github.com/BYU-I-eBadge/minibadge](https://github.com/BYU-I-eBadge/minibadge) and go to the latest release.

![minibadge GitHub page](github_page.png)

The KiCad symbol and footprint variants can be found on the releases page. On the latest release[^1], download `minibadge_full.kicad_sym` and `MiniBadge_Full.kicad_mod` for this tutorial. Save these in a folder that can be navigated to later.

![minibadge release](releases_page.png)

## Design in KiCad

### Initial Project Setup

Make and open a new project in KiCad. Save it in a directory of your choice.

![hint make new project](open_project.png)

After making the new project, the symbol and footprint need to be added so they are accessible from library browsers. Navigate to `Preferences` on the toolbar.

![go to preferences](preferences.png)

Then, go to `Manage Symbol Libraries`.

![go to manage symbol libraries](manage_symbols_highlighted.png)

A new window will appear. Navigate to the `Project Specific Libraries` tab to add the Minibadge symbol to this project only.

![switch tabs](sym_switch_tabs.png)

Once switched to the correct tab, click the button with the folder icon to open the downloaded symbol library.
**For KiCad symbols, open the `*.kicad_sym` file to add the library.**

![add symbol library button](add_sym_library.png)
![point out symbol libraries are files](sym_is_file.png)

Press OK to save changes and close the window for managing symbol libraries. In preferences again, navigate to manage footprint libraries.

![go to manage footprint libraries](manage_footprint_highlighted.png)

Similar to the window for managing symbol libraries, navigate to the `Project Specific Libraries` tab.
Click the button with the folder icon to open the downloaded footprint library.
**For KiCad footprints, open the folder that contains `*.kicad_mod` file(s) to add the library. This can reside in the same directory as your symbol library and other files; KiCad will only inventory the `*.kicad_mod` files from the selected folder.**

![add footprint library button](add_footprint_lib.png)
![point out footprint libraries are folders](footprint_is_directory.png)

### Schematic

Enter the schematic editor by pressing the icon in the main window.

![hint enter schematic editor](enter_schematic_editor.png)

A blank schematic will be shown. Start by placing symbols by pressing the highlighted icon or using the shortcut (A).

![initial screen hint add symbol](initial_screen_add.png)

Click anywhere on the schematic. A new window will appear that will allow for selecting symbols for components.
Search for the minibadge symbol that was downloaded. Select the one that looks like the one pictured, and press OK to close the window.

![select symbol window minibadge example](select_symbol.png)

The symbol should appear attached to your cursor. Click to place the symbol. If the symbol still appears to follow your cursor after placement, press the ESC key to release your cursor; this is a side effect of having `Place repeated copies` selected.

![symbol on schematic](place_in_schematic.png)

For this tutorial, we will design a basic minibadge that has a simple LED circuit.
Add symbols for an LED and resistor to the schematic by following a process similar to placing the minibadge.

![add additional symbols](place_more_symbols.png)

Now that all the symbols are placed, wires need to be added to connect the symbols together.
Wire the LED anode (the side with the triangle base) to the `+3V3` pin on the minibadge symbol.
Wire the LED cathode (the side with the flat line) to any side of R1.
Wire the unconnected side of R1 to the GND pin of the minibadge symbol.
**It is important that the circuit in your schematic is correct. It is easier to correct schematic issues before starting PCB design, rather than after.**

![add wire](select_wire.png)

For completeness, the circuit should have its used power paths (3.3V, Ground) labeled and attached to the schematic.
Click on the icon to place power symbols or use the shortuct (P).

![add power symbols](select_power.png)

A window will appear that operates identical to picking symbols for components.
For our ground (0V), use the `GND` symbol. Every pin that says `GND` on the minibadge should connect to one of these.

![select ground symbol window](select_gnd_symbol.png)

Similarly, power symbols should be placed for 3.3V. These should go on the pins labelled `3V3+` and `+3V3`.

![select 3.3V symbol window](select_3V3_symbol.png)

The schematic design is nearly complete. Click on the icon to place "no connect flags" on the remaining unused minibadge pins.

![select no connect flags](select_no_connect_flags.png)

Annotate the schematic so that the design can be checked for errors and be imported to the PCB editor.

![select annotate schematic](select_annotate_schem.png)

Click `Annotate` on the window that appears. The default settings in this window should work for this design.
**Note that this overwrites all reference designators. This may not be ideal for different designs.**

![annotate window](annotate_dialog.png)

Now that the schematic is fully annotated, the Electrical Rules Checker (ERC) should now be run.

![select ERC](select_electrical_rules_checker.png)

Click `Run ERC` on the window that appears.

![run ERC](erc_dialog_run.png)

As of time of writing[^1], running the ERC will result in certain warnings and errors that are safe to ignore.
**If there are additional errors, it is likely there is an actual error in the design that needs troubleshooting.**

[^1]: *2025-07-21*. Latest minibadge version 2.1c at time of writing. KiCad Version 9.0.3. Tutorial shown on Arch Linux/KDE Plasma.

![ERC false errors](note_on_false_erc_errors.png)

After verifying the the design is electrically sound, click the icon to assign footprints to all symbols in the schematic.

![select assign footprints](select_assign_footprints.png)

A window will appear that will assist with assigning footprints to each part.
Footprints are the way that components will physically appear and connect to the board.
When picking footprints consider whether the part is SMD[^2] or THT[^3].
**Make sure the package[^4] matches the actual components.**
For this tutorial, footprints for a 5mm LED and small through-hole resistor are used.

[^2]: *Surface-Mount Device.* These components are typically smaller and may be hard to solder by hand.
[^3]: *Through-Hole Technology.* These components are larger and typically easier to solder by hand.
[^4]: The package determines the physical dimensions of a device.
    For simple SMD devices, standard sizes may be used, such as 0603, or 1206.
    For THT devices, ensure the dimensions match or will be compatible.
    This involves verifying pitch between pins or other dimensions.
    **If a datasheet is available, these dimensions should be available and able to be matched with a KiCad footprint.**

![used footprints](used_example_footprints.png)

Save and close the schematic editor.

### PCB Layout

From the main window, enter the PCB editor by clicking on the icon.

![select PCB editor](enter_pcb_editor.png)

A blank PCB design will appear. Click the icon to update the PCB from the schematic or use the keyboard shortcut (F8).

![select update PCB from schematic](initial_pcb_update_from_schem.png)

A window will appear. Use the defaults and click `Update PCB`.

![update PCB window](update_pcb_dialog.png)

Components will appear on the PCB editor. Close the window an click near the center to place the mess of footprints.

![see added footprints to place](see_added_footprints.png)

Place the LED and resistor inside the minibadge footprint by clicking and dragging.
The resistor and LED should be placed on the back of the minibadge.
With the component selected, either:

1. Right click, then select `Change Side/Flip`.
2. Press `F`.

![flip components hint](flip_components.png)

After arranging components, the design should appear similar to this:

![example footprint placement](after_footprint_placement.png)

Again, note that the resistor and LED are placed on the back.
Minibadges typically are designed so that light can pass through the PCB.
In order for this to work, the design needs an area that prevents copper layers and soldermask from existing in a certain exclusion zone.

Click on the icon for drawing rule areas.

![select draw rule area](select_rule_area.png)

Then, **very intentionally pick a point on the PCB that will be the starting point to draw a polygon for the rule area.**
After clicking a point on the PCB, a window will appear.
Select the copper layers and all relevant keepout rules.
**Do not select the footprint keepout rule because that will include the minibadge itself. Selecting it will cause errors later.**

![rule area window](rule_area_dialog.png)

The default clearance rules are too strict for the minibadge and will throw errors. Fix this by entering the `Board Setup`.

![select board setup](select_board_setup.png)

Select `Constraints` from the categories available. Then, set "Copper to edge clearance" to `0.35 mm`.
Press OK to close the window.

![board setup window](board_setup_dialog.png)

Now that there are constraints and keepouts in place, areas for ground and power planes can be drawn.[^5]

[^5]: Normally, it is a bad idea to have a ground *and* a power plane on a two layer PCB.
    However, because there is only one connection other than power and ground and no rapid switching (like PWM signals),
    this is acceptable.
    Note that other designs may find it favorable to omit the power plane.

First, make sure a copper layer is selected.
Then, select the `Draw Filled Zones` tool, then select one of the corners of the PCB on or outside the `Edge.Cuts` layer.

![select draw filled zones](select_draw_filled_zones.png)

After clicking the initial point to start the polygon drawing for the filled zone, a window will appear.
Select the front copper layer.
Select the `GND` net.
Optionally name the zone "Ground plane".
Press OK when finished.

![ground plane properties window](ground_plane_properties.png)

After drawing the area for the ground plane, repeat the process for the power plane.
The power plane will reside on the rear copper layer.

![power plane properties window](power_plane_properties.png)

Press `B` to refill all copper zones. This will automatically route all connections for power and ground.

Only one connection remains. Select the icon to `Route Single Track` or press the shortcut `X`.

![select route track](select_route_traces.png)

Click on one of the pads that has a faint line that connects two of them.
The design will appear to be faded, except for the track currently being routed.
Click on the other pad to connect the devices together.

![draw track hint](draw_track.png)

Make sure to refill the zones so that the track is isolated from either plane.
Press `B` to refill all copper zones.

![refill zone hint](refill_zone.png)

A silkscreen design should be placed over the light passthrough window.
Designs can be made from images.
Go back to the main KiCad window without exiting the PCB editor, then select the icon for the image converter.

![select image converter](select_image_converter.png)

A new window will open.
Select `Load Source Image` and navigate to the image that will be placed on the PCB silkscreen.

![select load image source](select_load_source_image.png)

The image will likely not fit within the desired dimension of the window on the PCB.
Return to the PCB editor.
Use the `Measure` tool to record the constraining dimension (whichever is smaller).

![get dimensions of window hint](get_dimensions_of_window.png)

Return to the image converter window.
Make sure to dimension the image to fit in the window using the constraining dimension (height in this case).
If the source image isn't black and white, adjust the threshold and negative.
**Make sure the output format is a footprint on the `F.Silkscreen` layer.**
Press `Export to Clipboard` when done.

![export image window](export_image_to_silk.png)

Return to the PCB editor.
Paste the image using `Ctrl+V` or right click and paste.
Click the place the silkscreen should reside.
An additional reference designator will be pasted alongside the image.
Select it, and press `Del` to delete it.

![delete ref designator for vanity image](delete_ref_for_decor.png)

Light will not ideally escape through the light passthrough window yet.
Soldermask still will be applied over the window unless it is drawn over on the Mask layers.

Select the `F.Mask` layer then the `Draw Rectangles` tool.
After drawing the rectangle in the appropriate spot (over the rule area drawn earlier), select it.
Open the properties by right clicking and clicking `Properties` or using the shortcut key `E`.

![select rectangle properties](rectangle_properties.png)

In the properties, make the rectangle a filled shape.
Double check the layer is correct.

![rectangle properties front window](rectangle_properties_fill_shape.png)

Do the same process for the rear mask.
Ensure the properties are similar to the front mask, especially the filled shape property.

![rectangle properties back window](repeat_mask_delete_rear.png)

Verify the design using the Design Rules Checker (DRC).
Click on the DRC icon.

![select DRC](select_drc.png)

A new window will appear.
Select `Run DRC`.

![DRC window](drc_dialog.png)

**No errors should appear.**
There should be a warning for the intentionally placed silkscreen clipped by soldermask.
It can be safely ignored.

![DRC safe warnings](safe_drc_warning.png)

# Export PCB for Fabrication

Navigate to the `Gerbers` fabrication output.

![select gerber output](select_gerber_output.png)

Ensure all needed layers are selected.
Select the output directory. Directories relative to the KiCad project are allowed.
After selecting the output directory, click `Plot` to generate the gerber files for each layer.
Afterward, select `Generate Drill Files`.

![gerber plot window](plot_dialog.png)

Another window will appear on top of the plot window.
Ensure the output folder for the drill files is the same as the gerber output directory.
Then, select `Generate`.

![generate drill window](gen_drill_dialog.png)

Close the drill file generation window.
Navigate to the folder with the gerber and drill files.
The easiest way to do this is by using the icon to open the folder with the system file manager.

![open directory shortcut](plot_open_dir.png)

Use any method to zip all of the files in the directory to make a single output file.
This zipped file will be used for fabricating the actual PCB.

![zip output files](zip_output_files.png)

These instructions assume using JLCPCB as a PCB manufacturer.
This process should be similar for other companies that do PCB fabrication.

On [jlcpcb.com](https://jlcpcb.com), upload the zip file containing your gerber and drill files.

![JLCPCB upload](upload_to_jlcpcb.png)

After a successful upload, a preview, cost estimate, and settings will appear.

![preview JLCPCB](post_upload_jlcpcb.png)

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

![JLCPCB order settings](order_settings.png)

The minibadge PCB can now be ordered.