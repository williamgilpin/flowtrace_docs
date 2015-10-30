# flowtrace for Fiji and ImageJ

Implementation of the flowtrace tool as a macro for Fiji / ImageJ. Please make sure that you are running the latest version of [Fiji](http://fiji.sc/Fiji) or [ImageJ](http://imagej.nih.gov/ij/).

This has been tested in ImageJ32, ImageJ64, and Fiji.

William Gilpin, Vivek N. Prakash, and Manu Prakash, 2015

## Installation

Download the code and sample images from [the GitHub repository](https://github.com/williamgilpin/flowtrace_imagej)

Alternatively, on OSX/Linux you can initiate the download from the terminal using

	curl -OS https://github.com/williamgilpin/flowtrace_imagej/archive/master.zip

Or, using git

	git clone https://github.com/williamgilpin/flowtrace_imagej.git


## Running flowtrace

Open a folder containing an image time series as a stack or virtual stack
<img src="screenshots/tool.png" width="50%" />
<!-- ![flowtrace x ImageJ](screenshots/tool.png) -->


In order to run the tool without installing, go to `Plugins > Macros > Run`

<img src="screenshots/run_macro.png" width="50%" />
<!-- ![Save Directory](screenshots/run_macro.png) -->

Navigate to the folder into which you downloaded the tool and double click on it. You will be presented with a list of options for running the tool

<img src="screenshots/options.png" width="30%" />
<!-- ![Options menu](screenshots/options.png) -->

For "Number of frames to merge," select the number of frames that should be used to make each pathline. The larger this number, the longer the resulting pathlines (for best performance, this should be as large as possible while still smaller than the number of frames over which the unsteady flow noticeably changes). 

The remaining options are described in greater detail below. Click `OK` to continue. 

Now follow the prompt to choose a directory into which to save the output images. Click `OK` to run the tool.


## Permanent Installation

If you find yourself using flowtrace on a regular basis, you may want to install it as a permanent macro in Fiji or ImageJ's plugins menu. 

**In ImageJ:** 
+ Manually drag `flowtrace.ijm` into the folder `ImageJ/macros` (located in the installation directory of ImageJ), 
+ Restart ImageJ.

**In Fiji on OSX:** 
+ Go to `Applications/Fiji`, right-click the icon, and select "Show package contents"). 
+ Rename the file `flowtrace.ijm` to `flowtrace_.ijm` (it needs to have a name containing an underscore because of the way that Fiji checks for packages). 
+ Place `flowtrace_.ijm` into `Applications/Fiji`
+ Open Fiji and go to Plugins > Install Plugin, and then select `flowtrace_.ijm` from the file list when prompted. 
+ Restart Fiji.

**In Fiji on Windows:** 
+ Find your installation directory, it is likely somewhere like `Program Files (x86)/Fiji.app`
+ Rename the file `flowtrace.ijm` to `flowtrace_.ijm` (it needs to have a name containing an underscore because of the way that Fiji checks for packages). 
+ Place `flowtrace_.ijm` into the installation directory.
+ Open Fiji and go to Plugins > Install Plugin, and then select `flowtrace_.ijm` from the file list when prompted. 
+ Restart Fiji.  


## Options

When flowtrace is run, you are presented with the following options:

<img src="screenshots/options.png" width="50%" />
<!-- ![Options menu](screenshots/options.png) -->

+ Fade the ends of trails

	+ Linearly dim the pathlines in each image, such that the portion of the pathline that comes from frames further in the past appears dimmer.

+ Invert projections

	+ If you are using movies of dark objects against a light background (such as bright field microscope images, or a video of an insect flock or swarm), then invert the projection process in order to generate the appropriate pathlines

+ Color Frames

	+ In each frame of the resulting time series, color-code the pathlines by time. The portion of the streamline that is further in the past will appear more blue, while the more recent frames will be colored redder. The most recent frame is left untinted

+ Frames to skip

	+ If you don't want to project from every frame in the range of the time series (for example, if you want dotted lines, or if you think your data oversamples in time), then set "Frames to skip" to a number larger than 1. If you are not certain, leave this as 1.

+ Pairwise Difference

	+ Take the pairwise difference between all of the images in the time series.
	+ This is useful for removing very slow-moving particles from the field of view. Use this when "Subtract Median" does not remove artifacts aggressively enough.
	+ This works by default in Fiji. In order to make this work in other versions of ImageJ, please install the "Kymograph" plugin from [EMBL](http://www.embl.de/eamnet/html/kymograph.html). That plugin should be attributed to  J. Rietdorf, FMI Basel and A. Seitz, EMBL Heidelberg.

+ Subtract Median

	+ For each substack for which a pathline will be generated, subtract out the median of each pixel value. This option is good for eliminating backgound objects (or any objects that move slower than the tracer particles or moving organisms)

## Debugging

**"Color Frames" option fails** 
+ If the output log says `Unrecognized Array function` and `rvals = Array.<getSequence>(nmerge);` then you need to update to the latest version of Fiji or ImageJ

<img src="screenshots/macro_error.png" width="50%" />


## Future

<!-- + Subtract first frame of each series
 -->
Bug reports and pull requests are encouraged [through GitHub](https://github.com/williamgilpin/flowtrace_imagej)

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-52823035-4', 'auto');
  ga('send', 'pageview');

</script>