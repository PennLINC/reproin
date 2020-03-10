# reproin
reproin repository for UPENN_MRI. Using the reproin specification allows you to automatically curate your imaging data on Flywheel without the need for writing a heuristic, by instead pulling information from the sequence names in the DICOMs. This is done using a simple parser that follows a specification outlined below. The parser is flexible enough to be able to include many different configurations, but the sequence name **must** follow the specification below.

# Specification

In general, your sequence name should follow the form below:

`<BIDS FOLDER>-<FILETYPE SUFFIX>_<YOUR BIDS KEY>-<YOUR VALUE>__<OTHER INFORMATION>`
  
The `BIDS FOLDER` tells the heuristic what folder the file will fall under, e.g. `fmap` for BOLD data, or `anat` for T1w.

The `FILETYPE SUFFIX` tells the heuristic what to append to the filename, e.g. `T1w.nii`, `FLAIR.nii`, `dwi.nii`.

These two pieces are **mandatory**.

Following this, you may include as many BIDS-valid key-value pairs as you wish, following the [BIDS specification](https://bids-specification.readthedocs.io/en/stable/04-modality-specific-files/01-magnetic-resonance-imaging-data.html).

For any non-BIDS valid information you want to include, please separate this from the BIDS key-value pairs by placing it after a double underscore `__` (dunder). This will automatically be parsed out of the name.

# Examples

`fmap-epi_acq-dwi_dir-PA__ABCD`

`anat-FLAIR_acq-NAIMS__ND`

`anat-T1w_acq-vNavBC_ABCD`
