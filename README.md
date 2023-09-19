# Flatfielding
Fiji macros to flatfield raw images.
# Overview 
To ensure accurate image analysis, correction for non-uniform illumination using flatfielding is recommended. The typical Gaussian illumination profile results in dimmer edges of the image than the center. Flatfielding evens out the illumination (Figure 1) enhancing accuracy of image analysis. <br/> <br/>
![Picture1](https://github.com/SpillaneLab/Flatfielding/assets/143707918/c04eadb4-92d9-43f9-9049-492d84366528) <br/> <br/>
Figure 1: Representative image showing example raw image (left) having non-uniform illumination, which follows a Gaussian distribution. Flatfielding corrects for aberrations and uneven illumination (right). <br/> <br/>
Image a dye on a clean glass coverslip matching each channel of a multi-channel acquisition (termed “single colors”; see Figure 2) to generate an image stack for flatfielding. Acquire a minimum of 36 images per channel and ensure the same imaging conditions (intensity, exposure and laser power) as used for the imaging experiment. Acquire in the same order as for the imaging experiment to check for bleedthrough between channels. Also, acquire a minimum of 36 images with no laser to obtain background counts (dark counts), generate an image stack and then an average projection saving as “AVG_Stack.tif ”. <br/> <br/>
![Picture2](https://github.com/SpillaneLab/Flatfielding/assets/143707918/394d3299-d2c0-4edf-a5d1-c48c28940d44) <br/> <br/>
Figure 2: Example setup for single color imaging using an 8-well Lab-Tek chamber. The outside chambers should be avoided where possible to prevent knocking the objective whilst imaging. <br/> <br/>
# Installation 
Analysis performed using Fiji (Schindelin et al., 2012). 
1.	Copy the code (from browser or download as .txt) and paste into macro window as: 
     Plugins > New > Macro
2.	Ensure the language is set to IJ1 Macro in the Language tab of the macro window. 
3.	Save the macro using .ijm extension. 
# How to use 
Macros written for multi-channel image acquisition. Run macros in order numbered. 
1.	Create_stack_for_flatfielding.ijm <br/> <br/>
This macro creates an image stack for each channel of the “single colors”. Adjust the macro to close all channels other than the one a stack is to be made for. <br/> <br/>
2.	Create_normalized_image.ijm <br/> <br/>
This macro subtracts the average background counts for the camera from each image in the stack taken for the channel. It then creates a median projection from the stack of images and normalizes the projection by dividing by the mean value. <br/> <br/>
3.	Flatfield_and_reformat.ijm <br/> <br/>
This macro processes raw images by dividing each channel by the corresponding normalized flatfield image. This macro can be used to flatfield Z-stack or single-plane images. 
Check flatfielded images using line profile analysis in Fiji (https://imagej.net/imaging/image-intensity-processing). An inverse Gaussian profile is indicative of over-processing. <br/> <br/>
4.Make_composite.ijm <br/> <br/>
This macro creates a composite image and can be used if encountering errors with splitting channels. 
# Authors
Hannah McArthur – macros and description. 
# References 
Schindelin, J., Arganda-Carreras, I., Frise, E., Kaynig, V., Longair, M., Pietzsch, T., Preibisch, S., Rueden, C., Saalfeld, S., Schmid, B., Tinevez, J.-Y., White, D.J., Hartenstein, V., Eliceiri, K., Tomancak, P., Cardona, A., 2012. Fiji: an open-source platform for biological-image analysis. Nat. Methods 9, 676–682. https://doi.org/10.1038/nmeth.2019


