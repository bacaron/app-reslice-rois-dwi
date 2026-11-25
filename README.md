[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-brainlife.app.522-blue.svg)](https://doi.org/https://doi.org/10.25663/brainlife.app.)

# Reslice ROIS to match input DWI

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Reslices a collection of ROIs onto the voxel grid of a DWI image with FreeSurfer mri_vol2vol (header registration, nearest-neighbour interpolation).**

Runs mri_vol2vol --regheader with nearest-neighbour interpolation on every ROI so that it matches the voxel size and grid of the DWI. Use it when ROIs were made on a different voxel grid (for example T1w resolution) but are already aligned to the DWI; it does not register the images. Needs a FreeSurfer license.

| | |
|---|---|
| 📥 **Inputs** | `neuro/dwi` · `neuro/rois` |
| 📤 **Outputs** | `neuro/rois` |
| 🐳 **Container** | `brainlife/freesurfer:6.0.0` |
| ⚙️ **Resources** | 1 CPUs · 1 h walltime |
| 🔑 **Requires** | `FREESURFER_LICENSE` |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.671](https://doi.org/10.25663/brainlife.app.671) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `dwi` | `neuro/dwi` | yes | DWI image whose voxel grid is the target. |
| `rois` | `neuro/rois` | yes | Collection of ROI NIfTI files already aligned (in world coordinates) to the DWI. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `neuro/rois` | The ROIs resliced to the DWI voxel grid. |

📚 **References used by this App:**
- Dale AM, Fischl B, Sereno MI. Cortical surface-based analysis. I. Segmentation and surface reconstruction. NeuroImage 9:179-194 (1999).

<!-- brainlife-app:end -->

This app will This app will reslice ROIs to match the voxel size and spacing of an input diffusion dwi image. This may need to be done if the ROIs were generated in a different space (i.e. voxel grid). This app uses Freesurfer's mri_vol2vol to reslice the data. Assumes that the space the ROIs are in are registered to the diffusion dwi image.

### Authors

- Brad Caron (bacaron@utexas.edu)

### Contributors 

- Soichi Hayashi (shayashi@iu.edu)

### Funding Acknowledgement

brainlife.io is publicly funded and for the sustainability of the project it is helpful to Acknowledge the use of the platform. We kindly ask that you acknowledge the funding below in your publications and code reusing this code.

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

### Citations

We kindly ask that you cite the following articles when publishing papers and code using this code.

1. Dale, A.M., Fischl, B., Sereno, M.I., 1999. Cortical surface-based analysis. I. Segmentation and surface reconstruction. Neuroimage 9, 179-194.

#### MIT Copyright (c) 2020 brainlife.io The University of Texas at Austin and Indiana University

## Running the App

### On Brainlife.io

You can submit this App online at [https://doi.org/https://doi.org/10.25663/brainlife.app.522](https://doi.org/https://doi.org/10.25663/brainlife.app.) via the 'Execute' tab.

### Running Locally (on your machine)

1. git clone this repo

2. Inside the cloned directory, create `config.json` with something like the following content with paths to your input files.

```json
{
	"dwi": "/input/dwi/dwi.nii.gz",
	"rois": "/input/rois/rois"
}
```

### Sample Datasets

You can download sample datasets from Brainlife using [Brainlife CLI](https://github.com/brain-life/cli).

```
npm install -g brainlife
bl login
mkdir input
bl dataset download
```

3. Launch the App by executing 'main'

```bash
./main
```

## Output

The main output of this App is a rois datatype.

#### Product.json

The secondary output of this app is `product.json`. This file allows web interfaces, DB and API calls on the results of the processing.

### Dependencies

This App only requires [singularity](https://www.sylabs.io/singularity/) to run. If you don't have singularity, you will need to install following dependencies.   

- Freesurfer: https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferWiki

#### MIT Copyright (c) 2020 brainlife.io The University of Texas at Austin and Indiana University

