# FMRI
 _Studying resources and introduction to fMRI_
## Important resource
Following book and videos will lead and cover the entire studying of fMRI:
- Textbook: _Handbook of Functional MRI Data Analysis_
- [Videos][Martin]: _Principles of fMRI_

Meanwhile, **AFNI**, as one of the leading softwares for the analysis and display of multiple MRI modalities will be widely used in the lab. [Click here][afni] to learn more and follow the instruction to install it on your local computer.

## Practice example
This plan will use a recent study of our lab as practices in fMRI data preprocessing, analysis and visualization. The study,
[Distributed and Multifaceted Effects of Threat and Safety][Murty], also named as **MAX**, aims to examine how anxious apprehension is processed in the human brain. 
Details of data and models can be found at our [github page][MAX].

**All data require access permission to Bwift@UMD.eud**
Raw data:
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/dataset/raw/MAX???
```
Stimulus timing files
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/stim_times_neutral/
```

## Study plan


### 1. Introduction to fMRI
- Charpter 1-2 in Textbook
- Module 1-12 of Part 1 in [Videos][Martin]

```{admonition} Key points
---
class: important
---
- Physical and chemical principle of MRI scan
- What are structural and functional MRI images? What's the difference?
- BOLD signal and its features
- Artifacts and noise of fMRI
- Different types of experiment design
```

Addition to above readings and videos, here are some complementary contents which would be useful in this charpter:
```{seealso}
- [_Functional Magnetic Resonance Imaging_][Scott], Charpter 1-9, 11
- [_What we can do and what we cannot do with fMRI_][Nikos]
```


### 2. Preprocessing of fMRI data
- Charpter 3-4 in Textbook
- Module 13-14 of Part 1 in [Videos][Martin]

```{admonition} Key points
---
class: important
---
- Why we can't use fMRI images directly gained from scanner?
- What're the general steps in preprocessing? What's the meaning of each step?
```

The scripts for preprocessing:
```{code-block}
data/bswift-1/Pessoa_Lab/MAX/scripts/all_preproc.sh
```

```{caution}
The real fMRI preprocessing will be quite time consuming for just one subject
```

The proprocessed data(for neutral runs):
- Smooth:
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/dataset/preproc/MAX???/func_neutral/MAX???_EP_Main_TR_MNI_2mm_SI_denoised.nii.gz
```
- Unsmooth:
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/dataset/preproc/MAX???/func_neutral/MAX???_EP_Main_TR_MNI_2mm_I_denoised.nii.gz
```

Complementary contents:
```{seealso}
- [_Functional Magnetic Resonance Imaging_][Scott], Charpter 10
- An introdution PDF created by Kelly
```


### 3. First level analysis
Before dive into this charpter, one should at least have some systemic awareness of **probability and statistics**. Thus, complete courses are recommended. However, here are some good textbooks and YouTube channels for quick reviewing and reinforcement:
```{seealso} 
- [Statistical Inference][Casella]
- [R in Action][Robert]
- YouTube channel: [StatQuest!!!][statquest]
- YouTube channel: [Brandon Foltz][Brandon]
```

There are a lot of excellent resources other than above list. Please be free to search, ask and learn. 

For fMRI related analysis:
- Textbook: Charpter 5
- Module 15-22 of Part 1 in [Videos][Martin]

```{admonition} Key points
---
class: important
---
- The details of general linear regression and univariate approach for voxels/region of interest in a fMRI brain map
- The choice of independent variables in the model
- What is hemodynamic response function(HRF)? Why deconvolution?
- The pros and cons of assumed and unassumed shape HRF
- Multicollinearity
```

The scripts for first-level analysis:
- voxel-wise
```{code-block}
data/bswift-1/Pessoa_Lab/MAX/scripts/Murty_Final/voxelwise_analysis/condition_level/MAX_fMRI_Analysis_neutral_deconv_reducedRuns.sh
```
- ROI-wise
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/scripts/Murty_Final/ROI_analysis/condition_level/FNSandFNT/MAX_fMRI_Analysis_neutral_deconv_reducedRuns.sh
```

Reults of first-level analysis:
- voxel-wise
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/dataset/first_level/voxelwise/neutral_runs_conditionLevel_FNSandFNT/MAX???/
```
- ROI-wise
```{code-block}
/data/bswift-1/Pessoa_Lab/MAX/dataset/first_level/ROI/neutral_runs_conditionLevel_FNSandFNT/MAX_ROIs_final_gm_85/MAX???/
```

ROI-wise responses visualization
```{code-block}
https://github.com/LCE-UMD/mood-anxiety/blob/main/01-final_gm_85/01-data_preprocessing.ipynb
```

### 4. Group level analysis
- Charpter 6-7, 10 in Textbook
- Module 23-29 of Part 1 in [Videos][Martin] 

```{admonition} Key points
---
class: important
---
- Why group level analysis?
- Generalized linear model, including parametric ones like t-test, ANOVA, ANCOVA, mixed effect model and non-parametric ones like permutation test, rank test etc.
- P-value and types of errors
- Correction for multipule comparsion
```

```{admonition} Useful AFNI program
---
class: seealso
---
- Data manipulate: [3dbucket][3dbucket_afni]
- Data calculator: [3dcalc][3dcalc_afni]
- (Multiple) T-test or more: [3dttest++][3dttest_afni]
- AN(C)OVA: [3dMVM][3dMVM_afni]
- Linear mixed effect model: [3dLME][3dLME_afni]
- and [more][afni_program]...
```

### 5. What' more
Apart from above standard approach for fMRI analysis, more interesting contents such as brain connectivity, selection bias, graph theory etc. are just around the corner. The remaining part of Textbook and Part 2 of [Videos][Martin] have more details for them. 
Moreover, in addition to analyze fMRI images from frequentist point of view, Bayesian approach is gradually becoming popular. Here is a good [notebook][bayes] about practical Bayesian model in fMRI

Have fun in learning!
## License

**LCE@UMD**

[//]: # (Reference links)

   [Martin]: <https://www.youtube.com/channel/UC_BIby85hZmcItMrkAlc8eA/videos?view=0&sort=da&flow=grid>
   [afni]: <https://afni.nimh.nih.gov/pub/dist/doc/htmldoc/index.html#>
   [Scott]: <https://radktob.files.wordpress.com/2017/05/scott_a-_huettel_allen_w-_song_gregory_mccarthybookzz-org1.pdf>
   [Nikos]: <https://www.nature.com/articles/nature06976>
   [Casella]: <https://mybiostats.files.wordpress.com/2015/03/casella-berger.pdf>
   [Robert]: <https://books-library.net/files/books-library.net-10271851Vx7V9.pdf>
   [statquest]: <https://www.youtube.com/c/joshstarmer>
   [Brandon]: <https://www.youtube.com/c/BrandonFoltz/playlists>
   [bayes]: <https://bookdown.org/content/3890/>
   [Murty]: <https://direct-mit-edu.proxy-um.researchport.umd.edu/jocn/article/34/3/495/108894/Distributed-and-Multifaceted-Effects-of-Threat-and>
   [MAX]: <https://github.com/LCE-UMD/mood-anxiety>
   [3dbucket_afni]: <https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dbucket.html>
   [3dcalc_afni]: <https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dcalc.html>
   [3dttest_afni]: <https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dttest++.html>
   [3dMVM_afni]: <https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dMVM.html>
   [3dLME_afni]: <https://afni.nimh.nih.gov/pub/dist/doc/program_help/3dLME.html>
   [afni_program]: <https://afni.nimh.nih.gov/pub/dist/doc/htmldoc/statistics/main_toc.html>
