# flowtrace for MATLAB

Implementation of the flowtrace tool as a function file in MATLAB.

This code has been tested on R2013b and later. It has no special dependencies on particular toolboxes. Future versions might require the Image Processing Toolbox

William Gilpin, Vivek N. Prakash, and Manu Prakash.

## Installation

Use your browser to download flowtrace for MATLAB from [the host repository on GitHub](https://github.com/williamgilpin/flowtrace_matlab) and put it somewhere on your MATLAB path (Direct download link [here](https://github.com/williamgilpin/flowtrace_matlab/archive/master.zip)). On OSX/Linux, you can initiate the download from the terminal using

	curl -OS https://github.com/williamgilpin/flowtrace_matlab/archive/master.zip

Or, using git

	git clone https://github.com/williamgilpin/flowtrace_matlab.git

## Running flowtrace

You can download the test image files for flowtrace and place them in a folder "test_images" somewhere on your MATLAB path. See if the tool is working by running it on the test data included in the file

  >> test_script

You should see fresh image files in the directory `sample_output`

In general, the command to run flowtrace is

  >> flowtrace('some/input/data',30,'some/output/older/')

In order to use custom parameters, pass a struct() to the function

  >> params=struct()
  >> params.subtract_median=true
  >> flowtrace('sample_data',30,'sample_output',params)

## Options

Options are passed as fields in a `struct()`. This struct can be called anything,
but we'll call it `params` here.
    
  >> params = struct()

The various options are:

Subtract the median of each stack of frames before projecting

	params.subtract_median=false

Subtract the first frame of each stack of frames before projecting

	params.subtract_first=false

Take the minimum intensity projection then invert the color. Useful for images of dark particles on a light background

	params.invert_color=false

Take the pairwise difference between all of the images in the time series.

	params.take_diff=false

For each set of frames being merged, apply a gradient of color along the pathlines

	params.color_series=false

For each set of frames being merged, apply an intensity gradient along the pathlines 

	params.fade_tails=false

## Debugging

Flowtrace uses `nargin` to set defaults. Make sure that `params` is defined as a `struct()`if you choose to pass it to `flowtrace()`, even if none of its fields are defined. If you want to use all default parameters, do not pass any object to `flowtrace()` in the fourth input position.

## Future

Bug reports and pull requests are encouraged through [GitHub](https://github.com/williamgilpin/flowtrace_matlab).


<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-52823035-4', 'auto');
  ga('send', 'pageview');

</script>


