Tutorial Outline

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

	- top left: choose inches or mm
	- [keyboard shortcuts](https://support.xtool.com/article/132)
	- File/Project controls (ignore the Cloud Projects tool)
	- Left side - tools for placing objects onto the main canvas
	- Top bar - controls for manipulating objects on the canvas
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

## Build and Save aluminum job

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
		
		

## build and Save paper job

	

	

	  