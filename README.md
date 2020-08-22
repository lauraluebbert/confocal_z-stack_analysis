# confocal_z-stack_analysis
Imaging experiments in Biology often involve the acquisition of confocal z-stack images to quantify fluorescent signal in a biological sample. These z-stacks are most often analyzed using open-source programs such as FIJI, which are notoriously frustrating to work with, and do not facility intuitive high-throughput analysis of many images at once. Manual image analysis is labor-intensive, time-consuming, and prone to human error.

I compiled two notebooks to streamline two of the most commonly performed tasks in the analysis of confocal z-stack images:

1. The first notebook ("TEMPLATE_max_projec") allows the user to generate and save maximum projection images with a variety of adjustable parameters, such as filters, channel colors, adjustable scale bar (position, size, and color), and more. These parameters are defined once at the beginning of the notebook, in addition to a directory containing the raw tif files. The notebook then automatically generates and saves maximum projections (the saving folder and data format of the generated images can be adjusted too). Remember that one time you spent hours changing the lookup table (LUT) and scale bar size in hundreds of images for a presentation or publication? All of that is just two clicks away now.

2. The second notebook ("TEMPLATE_fluo_analysis) is designed to aid you in the analysis of the pixel (or fluorescence) values in your images. For this purpose, it first generates sum projections from your z-stacks (the notebook includes the option to save these locally too). You can then manually draw regions of interest (ROIs) and define background (BG) areas to normalize against. From your manually drawn ROIs, the notebook will compute the raw integrated density (sum of all BG normalized pixel values in ROI) as well as the integrated density (product of ROI area (number of pixels in ROI) and mean BG normalized pixel value inside the ROI) for each sample and save them to a clean csv file for further analysis. The images, ROI coordinates, and pixel values are saved to a dictionary and continuously linked to their sample#, channel, condition, and original filename, so nothing ever gets confused. These dictionaries are also saved locally as pickle files, which you could import into a new notebook for further analysis. They also contain your ROIs, which means that you will never ever have to redraw ROIs again over and over in FIJI just to change that one parameter in your analysis. 

A few ground rules:
1. Please read the text at the top of each notebook for instructions on how to use it. 
2. Name your tif files as follows: 
  "X_samplecondition_sample_channel" , where "X" is optional and can be filled as desired by the user (do not use spaces).  
      - "Samplecondition" can be a string of text separated by "-", e.g., "GCaMP-30C-6d_sample_channel" (Do not use spaces or "_" within the condition, else part of it will be cut out in the dictionary.)  
      - "Sample" and "channel" can be a simple numer or a description, e.g.: "samplecondition_1_1" or "samplecondition_Brain1_DAPI".  
3. The code currently only works for tif files containing one fluorescence channel each. (The maximum projection notebook does not have a merging option, yet.)
4. Let me know if you run into issues; I would love to hear your feedback! This code is quite versatile and I am happy to help you tailor it to your needs.
5. Please [cite](https://academia.stackexchange.com/questions/14010/how-do-you-cite-a-github-repository) this GitHub repository if you found it to be useful. 

ENJOY!

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3995395.svg)](https://doi.org/10.5281/zenodo.3995395)
