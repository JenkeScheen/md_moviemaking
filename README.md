# Making high quality movies/gifs using molecular dynamics trajectories
Steps needed to create publication-ready movies of MD trajectories using PyMol. The main purpose of this work was to create light-weight movies fit for slidedecks which is why the movies are written as GIFs. 

#### Prerequisites
- PyMol
- Input protein (and ligand)
----------------------------------
### Using PyMol

- load [protein.pdb]

- load [trajectory]

Remove solvent, format atom representations etc manually, position the view to point of interest.

- run `intra_fit [main_object_name]` (this makes the (ligand-)protein centered in the simulation - no need to mess around with mdtraj!)

- run `smooth` (smoothens between frames)

- if needed the trajectory can be trimmed by setting n frames by: `mset 1 -250` (for first 250 frames e.g.)

Set some colouring:

- run `set bg_rgb, white`

- run `set ray_opaque_background, on`

Set some moviemaking parameters

- run `set ray_trace_frames=1` (will ray-trace every frame - intense on hardware but worth it in the end)

- run `set cache_frames=0`

- run `mclear`

if you want transparent atoms:

- run `set transparency_mode, 2`

- run `set_bond stick_transparency, 0.5, sele`

Now create the movie. Instead of a movie file, this will output a high-res .png for each frame in the local folder.

- run `mpng mov` (will create mov0001.png, mov0002.png, etc.)

----------------------------------
### Using Quicktime (on MacOS):
- file -> open image sequence -> multi-select the .png files (converts to .mov)

----------------------------------

### Use ffmpeg and gifsicle on macos terminal (https://gist.github.com/SheldonWangRJT/8d3f44a35c8d1386a396b9b49b43c385):
- run `ffmpeg -i Untitled.mov -pix_fmt rgb8 -r 10 output.gif && gifsicle -O3 output.gif -o output.gif`

----------------------------------
#### Result:
![unnamed](https://user-images.githubusercontent.com/43140137/196655872-1178d800-9df0-433e-96b5-3b28e27d2509.gif)

