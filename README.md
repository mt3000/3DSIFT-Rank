# 3DSIFT-Rank

## FeatExtract
featExtract is the program used to extract SIFT-Ranked features from images. It accepts nifti images (.nii, .hdr, .nii.gz) as input, and output a list of keypoints and their descriptors.

#### Usage
Volumetric local feature extraction v1.1  
Usage: featExtract [options] \<input image\> \<output features\>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<input image\>: nifti (.nii,.hdr,.nii.gz).  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<output features\>: output file with features.  

#### Options 
 <table>
  <tr>
    <td>-w</td><td>Output feature geometry in world coordinates, NIFTI qto_xyz matrix (default is voxel units).</td> 
  </tr>
  <tr>
    <td>-2+</td><td>Double input image size.</td>
  </tr>
  <tr>
    <td>-2-</td><td>Halve input image size.</td>
  </tr>
 </table>
 
 #### Output
 The program will output a .key file (with the same name as the input file), containing a list of features, with their coordinates, scale, orientation, and descriptor.
 
## FeatMatchMultiple
featMatchMultiple is the program, based on FLANN library, used to match features.

#### Usage
Volumetric Feature matching v1.1
Usage: featMatchMultiple [options] -f \<input filelist\>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input filelist>: Text file containing the list of .key files (from featExtract). 1 key file per line.
    
#### Option
 <table>
  <tr>
    <td>-n</td><td>Number of nearest neighbors. Default: 5.</td> 
  </tr>
 </table>

#### Output
The program will output different files:

 <table>
  <tr>
    <td>_command.txt</td><td>The complete command used to generate this results (for logging purpose).</td> 
  </tr>
  <tr>
    <td>_names.txt</td><td>List of the input image filename</td> 
  </tr>
  <tr>
    <td><b>matching_votes.txt</b></td><td>NxN matrix containing the accumulation of the weighted votes for each pair of image. <br><b>The most important file.</b></td> 
  </tr>
  <tr>
    <td>feature_count.txt</td><td>The number of features for each input file.</td> 
  </tr>
  <tr>
    <td>vote_count.txt</td><td>NxN matrix containing the accumulation of the non-weighted votes for each pair of image.</td> 
  </tr>
 </table>
