# Glenn's notes for the plasma cutter

## Drawing
Need a .dxf of what you want to cut.  I've done these out of onshape, but you can do Illustrator as well.  There are sometimes some "arc" issues with onshape projections...best to check in illustrator that the lines are as you want them.

## Enroute
This program takes your DXF and creates toolpaths (gcode).  Start by doing File->Import and select your DXF.

Next, we need to merge the "linework" into paths:
* use ctl-A to "select all"
* In the "Transform" menu, select "merge selection".

At this point, all of your lines should be red or blue.  Move the path artwork so that it's close to the bottom left corner...this will help us with aligning when we bring it into the CNC tool.

Next, we want to convert lines to toolpaths.  Since we're doing plasma cutting, we want "Kerf" paths.  Some tips:
* If you are cutting the outside of the shape, you want a male kerf path.  
* if you are doing something inside of your main cut, (like screw holes) you want a female path.
* You can select the "entry" as a line or angle...and you can use "Toolpaths->Entry/Exit" to change where on that shape we "enter".  Note clicking and dragging the green entry line can be tricky...
* If your toolpath doesn't quite look right, you can edit it (under toolpath menu).  Don't select "kerf" again...that will make a new toolpath for the same line (giving you two).  Sometimes if the program isn't editing it the way you want it's better to just "delete" the existing toolpath and make a new one.

Once you've got the toolpaths the way you want them, you need to order them.  Start with the inside stuff, then cut the outside.  There's a virutal "jog wheel" to tweak the order of what goes first.

Finally, we need to output the gcode...this is under "machining->output".

## Velocity CNC
This is the program that drives the plasma cutter.  We've got three things we need to turn on:
* the big table itself (hold green button)
* the "air" (small aux box on the right)
* the compressor itself (back room)  Note, if the compressor isn't on, the "air" box will be flashing yellow.

Now connect Velocity to the table...it's the "two plug" looking icon in the left-middle of the top.  It'll take a second or two.

Next we need to import that gcode from the previous step.  The import button can be tricky to find...it's the file-folder-looking button in the middle-left of the screen.

Find a place on the sheet where you want your cut.  You can use the jog-wheel to move the plasma head to where you want that lower-left corner to be (x=0, y=0).
Z should be less than an inch...rule of thumb is make it finger height above the table.  When you've got the head where you want it, set those coordinates as zero by clicking the program menu (top right) and picking "zero all".

To see if this is where you want it, you can do a dry run.  Click that checkbox (top-leftish), and hit the play button.  The head will move through where it wants to do it's cuts.

If things need to move, you can use the jog-shuttle to move the head and make a new zero point.  You can start the head at the current zero by:
* selecting the menu (3 horizontal lines) in the positioning area, then select "point" rather than "jog" and do "go to zero" which will move it to our 0,0,0 point.  
* Hit that menu again to go back to jog mode and move the head to the new start location
* click "zero all" from the program menu (like before) to try again.

Note:  every time you run through the gcode, you need to "reset" it...there's a refresh button (circle-arrow) in the middle of the screen to do this.  If your "play" arrow is greyed out, chances are you need to reset the g-code.

When you are satisfied (and ready to cut), un-check "dry run", put on those glasses, and click go.  

