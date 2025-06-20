# README

## Overview
This script allows the user to manually inspect ICA components (GICs), define thresholds to detect spike-like activity, and generate binary spike trains for each selected component. It includes options to repeat or split components that may contain multiple neurons by assigning multiple thresholds.

---

## Features
- Visual inspection of each selected ICA component.
- Manual threshold selection for spike detection.
- **Supports multiple thresholds** per component to detect spikes from multiple neurons.
- Automatically **excludes previously detected spikes** when applying a second, lower threshold.
- Saves all spike trains and threshold data for further analysis.

---

## Requirements
- MATLAB (R2022a or later recommended).
- Variables required in the **workspace**:
  - `possible_gics`: vector of indices of candidate ICs to evaluate.
  - `components`: matrix where each row is a signal trace of one ICA component.

---

## Input
- **Manual threshold(s)** entered interactively by the user.
- User interaction options:
  - Omit a component.
  - Repeat the previous GIC.
  - Add a second, lower threshold to detect smaller peaks (e.g., from a second neuron).
  - End the analysis.

---

## Output
When saving is enabled, the script creates `binary_matrix.mat`, containing:
- `binary_matrix`: a matrix of binary spike trains (rows = GICs, 1 = spike).
- `temp_good_gics`: list of selected GIC indices.
- `thresh`: list of thresholds applied (one or more per GIC).

Additionally, the script generates plots:
- Original signal trace with threshold(s).
- Corresponding binary spike train.

---

## Usage
1. Load the data (ensure `possible_gics` and `components` are available in the workspace).
   - Or modify the script to load a `.mat` file at the beginning.
2. Open and run `ManualThreshold_BinarySpikeDetection.m` in MATLAB.
3. Follow the on-screen prompts:
   - Assign threshold(s), repeat or skip GICs, and save results.
4. (Optional) Uncomment the last line to save the output:
   ```matlab
   save('binary_matrix.mat', 'binary_matrix', 'temp_good_gics', 'thresh');

## Notes
- When applying a second threshold to the same component, previously detected spikes will be masked to avoid duplication.

 
