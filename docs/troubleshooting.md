# Overview

This section addresses some common issues with the analysis workflows at GNPS. If you run into any of these common issues, hopefully this page will give you actionable steps to address them. If this page cannot help you, please refer to the [forum](https://groups.google.com/forum/#!forum/molecular_networking_bug_reports) to help answer your questions.

## GNPS Jobs

???+ "There was an error transferring this workflow's input files to computation storage"
    This error generally means there was a server error and not a user one. Please try re-running. If repeatedly it errors out, please send an email to system administrators (ccms-web@cs.ucsd.edu). 

## Molecular Networking

### Failed Molecular Networking Job

???+ "Empty MS/MS"
    This means that your input data has no MS/MS spectra. This could mean one of several things

    1. The file format input is incorrect. Please make sure it is a [supported file format](fileconversion.md) for GNPS.
    1. The mass spectrometry files do not contain MS/MS spectra. These files cannot be analyzed by GNPS.
    1. The filtering criteria are too aggressive. Please use an appropriate preset for your data.

???+ "spectral library search exceeded memory"
    This means that the spectral library search step used too much memory and had to be terminated. This is likely caused by changing the set of spectral libraries used in search. It is not recommended to change the set of libraries included unless you are an advanced users. Please remove all libraries except for the default "speclibs" and rerun.

???+ "Missing filename in Metadata"
    The metadata file included for networking is formatted incorrectly. Please refer to metadata formatting to correct this.

### Results Incorrect

???+ "No attributes or groups in output"
    Verify that file names match between metadata and data.

    Make sure the metadata file includes the appropriate columns and attributes are prefixed with ATTRIBUTE_ and that the metadata file is a tab separated text file.

    Avoid using special characters in metadata or file names.

## Library Search (Dereplication)

???+ "No Results"
    1. Check that the parameters are correct
    2. Make sure you have the right format for input
    3. Make sure you have MS/MS spectra in your data, this is summarized in the file summary link. 

## MASST (Single Spectrum Search)

???+ "Error: m/z and intensity not separated properly" 
    A common error is missing intensities for masses. Simply masses are insufficient, intensities are also required.

## Qiime2 errors

???+ "Page not found output in qiime2 view for Emperor plots"
    You could have:
    
    1. Duplicate file names
    1. A column called “sample_name” in your metadata, this column should be removed. 
    1. Your filenames in the metadata do not align with the input data
    1. In cases of feature-based molecular networking, there can be negative values in quant table somehow. These cause error while calculating sample distances.

## Page Contributors

{{ git_page_authors }}
