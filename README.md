# Census of PubMed/MEDLINE Clinical Trial Publications

## Overview
This repository contains the data produced by [Durvasula, Eyuboglu, and Ritzwoller (2024)](arxivlink). The data provide a census of publications indexed in PubMed/MEDLINE that report the results prospective, interventional clinical trials that evaluate the effects of investgational or approved drugs in a setting with exclusively human subjects.

## Data Description
The repository includes a single file, sample.csv. 

This file has five fields:
- `pmid`: The unique identifier assigned to each publication by PubMed/MEDLINE.
- `prob`: Our ensemble, fine-tuned, language model outputs a number between 0 and 1. Large numbers indicates that the publication is more likely report the results of c clinical trial.
- `liberal, moderate, conservative`: We construct three samples by restricting attention to publications whose `prob` is above three thresholds. We refer to these samples as the `liberal` sample, the `moderate` sample, and the `conservative` sample. The thresholds associated with these samples are 0.0124, 0.221, and 0.494, respectively. The `liberal`, `moderate`, and `conservative` fields record binary variables indicating whether each publication is an element of the associated sample. 

The file has 1,810,510 entries. The entries correspond to the set of publications indexed by PubMed/MEDLINE that were published between 2010 and 2022 and who satisfy a set of sample restrictions enumerated in Appendix A.2 of Durvasula, Eyuboglu, and Ritzwoller (2024).

## Usage
The `conservative` sample has the lowest false positive rate, and will include the smallest number of publications that are not reporting the results of a clinical trial. The `liberal` sample has the largest true positive rate, and so will omit the smallest number of publications that are not reporting the results of a clinical trial.

## Acknowledgements
We gratefully acknowledge support from the National Science Foundation, the Knight Hennessy Scholars Program, the Stanford Law School John M. Olin Program in Law and Economics, the National Bureau of Economic Research Innovation Information Initiative Summer Fellows Program, and the OpenAI Researcher Access Program. 

