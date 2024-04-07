Tutorial Outline

This is a highly detailed step-by-step outline designed to guide the student through the process of preparing jobs as well as 
operating the F1 laser.

# Intro to the F1 laser

  - this is a 10W diode laser (blue) and a 2W infrared laser (green)
  - it is a "galvo" laser - using mirrors that can quickly move the beam accurately
  - it can engrave and cut a variety of light organic materials and can etch some metals
  - very fine detail is possible
  - it has a 4 inch square work area
  
# Materials

  - visible laser is effective on paper, cardboard, acrylic, light wood, stone
  - IR laser is effective on stone and many metals: copper, brass, anodized aluminum, stainless steel
    - (and apparently gold and silver)

# Safety

  - The energy in this laser can  permanently and irreversibly damage your retinas if not operated safely.
  - both direct and diffuse reflection of this beam can do damage, faster than you can react
  - when operated behind the filter, with the lid closed, it's a Class 1 laser and will not hurt you.
  - without the filter, it's a Class 4 laser, and requires protective eyewear or shielding for any who could be exposed.
  
# Setup and laser orientation

  - laser turned on
  - top left button is emergency shutoff - if depressed it won't power up, turn button to release the lock.
  - top right button is used for focusing and for starting a job
  - lid slides up to access the working area, slides down to completely enclose it.
  - air filter is attached and sits alongside the laser
  - XCS software launched and connected to laser
  - confirm settings: all safety toggles on AND IR laser preheat on.
  

# XCS Interface

  - top left: choose inches or mm (we'll assume mm in this tutorial)
  - [keyboard shortcuts](https://support.xtool.com/article/132)
  - File/Project controls (ignore the Cloud Projects tool)
  - Left toolbar - tools for placing objects onto the main canvas
  - Top toolbar - controls for manipulating objects on the canvas
  - Right side - controls for manipulating laser settings
  - Bottom right: preview (Framing) and run (Process) the job
  - floating layers palette for grouping objects with similar settings
  
  
# Artwork Supported

  - vector files: SVG is the most typical
  - raster files: JPEG, PNG, GIF are typical
  - vector files can be manipulated after import
  - raster images can be scaled, and traced after import
  
# Laser settings

  - vector scoring - draw the outline of the objects on canvas - usually very quickly
    - variables: power, speed, passes
  - vector engraving - draw and fill the objects on canvas - measured in lines/cm so slower
    - variables: power, speed, passes, lines/cm
  - vector cut - when you want to cut through the material
    - variables: power, speed, pases
  - raster engrave - when you want to "print" a raster image using the laser
    -variables: dot duration, power, DPI, passes, bitmap mode, engraving mode
  
# Material settings

  - Xtool material settings page is a good place to start
  - presets can be selected, but should be confirmed for your material
  - constructing a material test grid is a good way to quickly zero in on appropriate settings
  - you can only adjust by two variables - power and speed (or dot duration and speed for bitmap)
  
# Material testing

## Standard Settings for most jobs:

  - without anything selected, in the RHS panel check that these settings are on:
    - `Laser Flat`
    - `Material`: User defined
    - `Thickness`: Use autofocus before init
    - `Processing Path`: Auto planning

## Building a material test for paper

  - draw a circle or rectangle on canvas, typically around 5 mm
  - with object selected:
    - set initial mode (score) and laser (blue light), power to 50%, speed to 1000 mm/s
    - from the top toolbar, select Array, then Material Array
    - set power/speed based upon the material you're testing, here power 10-50%, speed 10-50 mm/s
    - maybe set the Spacing between objects down to 2mm if you want it smaller
    - hit OK to place the array on the canvas
    - you can now move the array as a single group as you see fit
    
## Using layers to make the test more legible

  - the material test grid is a group.
  - use the top toolbar 'ungroup' command to remove that grouping
  - click outside the area to un-select the objects
  - draw a selection box around the left hand text (NOT the grid of objects)
  - in the layer palette, select the "Move to" button and select one of the unused colors
    - this will create a new layer named "Layer 2"
  - repeat this for the top and bottom text and labels, moving them to the same "Layer 2"
  - select the new layer and rename it "text labels"

## Adjust layer settings

  - with the new layer "text labels" selected, adjust the laser settings on the right panel:
  - `output` radio button should be selected
  - `processing type`: engrave
  - `setting`: manual setting
  - `Laser Type`: Blue light
  - `Power`: 75%
  - `Speed`: 150 mm/s
  - `Pass`: 1
  - `Lines per cm`: 220
  - `Engraving Mode`: Bidirectional
  
## Check framing and save the project 

  - load your test material (here a sheet of thick paper)
  - focus the laser using the top-right knob to align the red & blue dots
  - select the Framing button - this will draw a low-power outline of the object on the material
  - select and move the object on canvas while observing its location on the material
  - select Stop Framing once position is as desired.
  - using the top "Folder" menu, select `Save As` and give it a file name
  - in the example files, I called it `material-test-65lb-paper.xcs`
  
## Run the Project

  - Select the Process button, this takes you to the Preview page
  - if the job looks correct, make sure that the laser lid is closed and press Start
  - the knob on the top right side of the laser should be blinking, once pressed it will start running the job.
  - if you accidentally hit the emergency shutoff button on the top left, we'll have to reconnect and restart the job.
  - when the job is finished, it's safe to open the lid and examine the results
  - take note of the desired settings: you need to find for our use:
    - a setting which marks the paper legibly w/o cutting through
    - the minimal setting which cleanly cuts through the paper
  
## Material test for aluminum

  - we're going to use a preloaded one for that, it's the same process with these differences:
    - use vector engrave mode
    - use IR laser mode
    
# Example of importing SVG graphics

  - from a web browser (or Inkscape if installed)
    - open the file graphics-files/combo-example-01.svg
    - note what the image looks like on screen

  - in XCS
    - open a new project 
    - select Image import from the left toolbar and select the file graphics-files/combo-example-01.svg
    - note what the imported image looks like
    
  # Detailed difference notes:
    - paths are imported correctly, but
      - stroke is rendered, stroke width and fill is ignored
      - complex vector paths (brush stroke example) will show the path artifacts 
      - curved vector paths that are not closed paths need to be scored not engraved
      
    - text converted to paths is imported correctly
      - text using a font, is not rendered
    
    - layers are counter-intuitive
      - actual Inkscape layers are SVG groups
      - XCS groups into its own layers using the stroke color
    
    - imported raster images are rendered fine
      - selecting these open up a "bitmap image" toolbar

# Class Project

We're going to engrave an aluminum business card using imported vector graphics. 
We'll add custom text to the card.
We will then score and cut a paper backing to hold the card.

The project we will build looks something like this:
[engraved metal card on paper](./tutorial-project-example.png)

## Build and Save aluminum job

Here are detailed steps to setup a job for aluminum card engraving.

  - prepare the project for the material size:
    - launch XCS and open project template-files/blank-f1-project.XCS
    - use "save as" to save this project to a new location with name of your choice
    - import the image file templates/template-card-86x54.SVG
    - place the image somewhere near the center of the frame
    - with the object select, in the RHS toolbar set the Object Setting to "Ignore"
    - rename the Layer 1 name to "card outline"
    - save the project 
  
  - import a vector image into the Project
    - import one of the SVG graphics files from graphics-files/ directory
    - drag the selected object to within the card outline area
    - note that its on its own layer, you can rename this to "graphics"
    - set the 
    
  - add text directly
    - select the Text tool
      - this drops a big block of text ("HELLO") on your project and opens a Text panel on the right
    - set the text value in this panel to something ("Established 1977" with a linebreak in the example.)
    - set the text size (in points) to something that will fit in your space (14 pt in the example)
    - drag the selected text to a place you want it, and adjust the size to make it fit
    - set the typeface and style to something you like, and tweak settings to get what you want.
    - leave Spacing and Leading set to 0 for default settings
      - Spacing is the space between characters (kerning)
      - Leading is the space between lines
      - both can be positive or negative values
    - set Alignment as you prefer
    - do NOT select "Weld" as this will permanently fix the text to thest settings
    
  - add another text 
    - repeating the above actions, put another block of text with your name in it
    - format this text to fit into whatever space you want for the design
    - you might need to play with the leading (space beween lines)
    
  - adjust the layer settings
    - note that the two text blocks came in as "black" color, and are assigned to "Layer 2"
    - rename the layer to "text and graphics"
    - with this layer selected, use the Object Settings panel to these values:
      - `Output` selected
      - `Processing type`: engrave
      - `Setting`: Manual setting
      - `Laser type`: IR
      - `Power`: 100%
      - `Speed`: 655 mm/s
      - `Pass`: 1
      - `Lines per cm`: 220
      - `Engraving mode`: Bidirectional
      
    - Save your Project
    
    

## Build and Save paper job

Here we'll build the paper frame backing. Much of the steps are similar to the prior job, so these instructions will
concentrate more on the differences.


  - prepare the project for the material size:
    - launch XCS and open project `template-files/blank-f1-project.XCS`
    - use Save As to save this project to a new location with name of your choice
    - select the rectangle tool, and draw out a rectangle on the canvas
    - in the upper toolbar:
      - select the "lock" button to unlock it the dimensions,
      - type in width 112.5mm, height 92.5mm, and
      - select the lock button again to lock the dimension (proportions)
    - set the Output Settings to Ignore. 
    - import the image template for the card to use for positioning
      - location templates/template-card-86x54.SVG
    - place the image on the canvas inside of the larger rectangle, roughly centered.
    - move the smaller rectangle to the same layer as the larger one (probably Layer 1)
    - select that layer, rename it to "backgound" and ensure that Output settings are set to "ignore"
    - Save the project file

  - setup graphics to be 'drawn' on the page
    - there are some SVG files in the `graphics-files/` directory, feel free to position ones you like on your canvas
      - keep in mind that we're going place the card into the frame so get things positioned the way you like.
    - once you've imported 1 graphic, move it to a new layer, and rename that layer "line graphics"
    - import any other graphics you want, keeping them in that same layer
    - once finished, select the layer, and apply these settings to it:
      - `Object setting`: output
      - `Laser type`: Blue light
      - `Processing type`: score
      - `Power`: 45%
      - `Speed`: 30 mm/s
      - `Pass`: 1
      
  
  - setup cut lines to be used to hold the card in the frame
    - using the Line tool, draw a line at a roughly 45° angle, across the top left corner of the inner rectangle
      - the intent is that this corner of the card fill slide into the line cut here, so position appropriately
      - bounding box should be approximately 10mm x 10mm.
    - move the selected line to a new layer, rename the layer to "cut lines"
    - select the line, copy/paste to create a duplicate and drag it over to the top right corner
    - in the top toolbar, select `Reflect` ->` Reflect horizontall`y, then move the line to an appropriate position
    - copy/paste the top right line, drag to the lower right corner, use `Reflect` -> `Reflect vertically` and adjust position.
    - copy/paste the bottom right line, drag to the lower left corner, use `Reflect` -> `Reflect horizontally` and adjust
    - with the layer selected, set the Object settings to match:
      - `Object setting`: output
      - `Laser type`: Blue light
      - `Processing type`: cut
      - `Power`: 40%
      - `Speed`: 10 mm/s
      - `Pass`: 1
      
  - setup layer planning so that cut lines go last
    - not necessary for this job, but can be useful for more complex jobs
    - without anything selected, in the RHS panel set `Processing Path` to `By Layer``.
    - rearrange the order of the layers in the layer palette by drawing the "cut lines" below the "line graphics"
      - this will cause cut lines to happen after all of the prior layers are scored
      
    - Save your Project

    
# Setup and run the job

Using the files from the previous section, we will run the jobs on the laser.
(If you don't have a completed project file, you can use the ones found in the `examples/` directory:
 `example-card-and-frame-metal-only.xcs` has the metal parts enabled, and `example-card-and-frame-paper-only.xcs` has the paper
 parts enabled.)
  
  - Common Laser Job steps
    - turn on the laser
    - open XCS, and wait for it to connect to the laser
    - verify that all safeties are on AND that IR Preheat is on
    
  - Setup Materials
    - open lid and place material on the bed
    - focus the laser using the RHS knob until the red/blue dots converge on the material
    - open your project File
    - select the Framing button - and position either the material and/or your artwork to desired position
    - Stop Framing
    - Close the lid, being careful not to move your material.
      - some small/light materials may need to be taped down.
      
  - Run the job
    - Select the `Process` button
    - if the contents of he Preview look okay, select the `Start` button in the top right of the window.
    - Press the knob on the upper right of the laser unit
    - wait for the job to complete
    - lift lid, remove material, and evaluate results
    - if you want to make another one at this time, you could,
      - at least if you've put some sort of alignment tape/jig on the bed
    -  otherwise cancel the Preview and go back to the canvas.
    
  - Repeat the above setups (setup materials and run the job) for the paper and metal project.
    - order does not matter, just make sure you have the correct job for the selected material!
    
    
# Where to go from here

Ona area that we have not explored in this introductory material is using engraving into metals. 
While the results are promising, they take awhile - a small piece of metal can easily require 20 minutes.
This is due to the slow speeds required, as well as the fine level of detail (lines/cm or DPI).


Another area is the engraving of raster images. Here one must experiment with the dot duration and the speed, along with the
algorithm used to establish the dot pattern. Again, these take time to process, too much for a single intro class.


