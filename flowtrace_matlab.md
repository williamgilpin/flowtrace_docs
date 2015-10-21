# flowtrace for MATLAB

Implementation of the flowtrace tool as a function file in MATLAB
This was developed and tested primarily on R2014a, but it has no special dependencies on particular toolboxes. Future versions might require the Image Processing Toolbox

William Gilpin, Vivek N. Prakash, and Manu Prakash, 2015

## Installation

Use your browser to download flowtrace for MATLAB from [the host repository on GitHub](https://github.com/williamgilpin/flowtrace_matlab) and put it somehwere on your MATLAB path. On OSX/Linux, you can initiate the download from the terminal using

	curl -OS https://github.com/williamgilpin/pypdb/archive/master.zip

Or, using git

	git clone https://github.com/williamgilpin/pypdb.git

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


## Future

+ Support for color images

Bug reports and pull requests are encouraged.





