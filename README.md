# Myelin map

Myelin mapping is a method for "myelin" quantification (Glass et al., however see Uddin et al., who suggest it does not represent myelin specifically, but can still be used to examine white matter microstructure [aka you can still use the method to tell if there's something going down in the white matter]).

The method is simple: 
1. Get t1w & t2w images in the same space. 
2. t1w / t2w
3. Myelin map

This notebook outlines the steps to calculate myelin maps using Nibabel, Advanced Normalization Tools (ANTs), scipy stats and some numpy tinkering. 

The pipeline expands on the simple method by using the method outlined by Ganzetti et al.:

1. Warping MNI template to subj space
2. Warping MNI eye + temporal bone + brain masks from MNI to subj space
3. T2 registered to T1 image through rigid registration
4. N4 bias correction on T1 and T2 images
5. Linear intensity adjustment of subj space t1 & t2 images w/ eye + bone masks.
6. Creation of myelin map (co-registered, bias corrected, intensity adjusted t1w image / co-registered, bias corrected, intensity adjusted t2w image)
7. Warping of myelin map from subj space to MNI.

**NOTE:** Nipype script will be available soon.

Refs:

Ganzetti et al. (2014). Whole brain myelin mapping using T1- and T2-weighted MR imaging data

Glass & Van Essen (2011). Mapping human cortical areas in vivo based on myelin content as revealed by T1- and T2-weighted MRI

Uddin et al (2018). Can T1w T2w ratio be used as a myelin‐specific measure in subcortical structures? Comparisons between FSE‐based T1wT2w ratios, GRASE‐based T1w T2w ratios and multi‐echo GRASE‐based myelin water fractions
