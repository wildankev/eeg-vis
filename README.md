# EEG Visualization Project

A comprehensive Jupyter notebook for downloading and visualizing EEG (Electroencephalography) data from the PhysioNet EEG During Mental Arithmetic Tasks Dataset.

## Overview

This project provides a complete pipeline for:
- Downloading EEG data from PhysioNet
- Loading and processing EDF files
- Visualizing EEG signals in multiple formats
- Analyzing frequency content and spatial distribution
- Creating topographic heatmaps of brain activity

**Note**: All data downloads and visualizations are displayed in the notebook output only. No files are saved locally to conserve disk space.

## Dataset

This project uses the **PhysioNet EEG During Mental Arithmetic Tasks Dataset**:
- **URL**: https://physionet.org/content/eegmat/1.0.0/
- **Subjects**: 36 volunteers
- **Channels**: 23 EEG channels (10/20 system)
- **Sampling Rate**: ~500 Hz (varies by subject)
- **Tasks**: 
  - **Condition 1**: Baseline/resting state EEG (60 seconds)
  - **Condition 2**: Mental arithmetic task - serial subtraction of 2-digit from 4-digit numbers (60 seconds)
- **Format**: EDF (European Data Format)
- **Frequency Band**: This analysis focuses on **Beta band (13-30 Hz)**, associated with active thinking and concentration

## Features

The project includes two notebooks:
- `visualize.ipynb`: The original visualization notebook.
- `visualize_revised.ipynb`: **Recommended**. A revised version with enhanced features including PLI connectivity analysis and PSD topoplots, using temporary storage to ensure no files are saved locally.

Key features in `visualize_revised.ipynb`:

1. **Automated Data Download**: Downloads EDF files directly from PhysioNet (stored in temporary directory)
2. **Time-Series Visualization**: Multi-channel plots showing EEG signals over time
3. **Single Channel Analysis**: Detailed view of individual channels with statistics
4. **Power Spectral Density (PSD)**: Frequency domain analysis focusing on beta band (13-30 Hz) associated with active thinking
5. **PSD Topoplot Heatmaps**: Spatial distribution of beta band power across the scalp
   - Baseline condition topoplot
   - Mental arithmetic task condition topoplot
   - Difference map (task vs. baseline)
6. **Phase Lag Index (PLI) Connectivity Analysis**: Functional connectivity heatmaps between brain regions (visualizing synchronization)
7. **Statistical Analysis**: Summary statistics for data quality assessment

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/wildankev/eeg-vis.git
   cd eeg-vis
   ```

2. **Install requirements**:

- Python 3.8 or higher
- pip package manager
- Jupyter Notebook or JupyterLab


1. Navigate to the project directory:
```bash
cd eeg-vis
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

### Dependencies

The project requires the following Python packages:
- `numpy` (≥1.21.0) - Numerical computing
- `scipy` (≥1.8.0) - Scientific computing
- `matplotlib` (≥3.4.0) - Plotting and visualization
- `mne` (≥1.0.0) - EEG/MEG data processing
- `requests` (≥2.26.0) - HTTP library for downloading data
- `jupyter` (≥1.0.0) - Jupyter notebook environment

## Usage

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open [visualize.ipynb](visualize.ipynb)

3. Run all cells sequentially (Cell → Run All)

The notebook will:
- Download sample EEG files from PhysioNet
- Load and process the data
- Generate multiple visualizations in the notebook output
- Display all results inline (no files saved to disk)

### Customization

You can modify the notebook to:
- **Change subject**: Edit the `SUBJECTS` list in the configuration cell
- **Adjust visualization parameters**: Modify duration, channels, time windows
- **Apply filters**: Adjust the beta band frequency range (default: 13-30 Hz)

## Output

The notebook generates several visualization types displayed in the output cells:

1. **Time-series plots**: Multi-channel EEG signals over time
2. **Detailed channel views**: Individual channel analysis with statistics
3. **Power spectral density plots**: Frequency analysis in beta band (13-30 Hz)
4. **PSD Topoplot Heatmaps**: Spatial distribution of beta band power
   - Baseline condition topoplot (resting state)
   - Mental arithmetic task condition topoplot
   - Difference map showing brain activity changes
5. **Statistical summaries**: Data quality assessment metrics

**Note**: All visualizations are displayed as notebook outputs only. No files are saved locally.

## Troubleshooting

### Download Issues

If you encounter network issues downloading from PhysioNet:
1. Check your internet connection
2. Verify the PhysioNet URL is accessible: https://physionet.org/content/eegmat/1.0.0/
3. Try running the download cell again

### Memory Issues

If you encounter memory issues:
- Reduce the number of subjects in the `SUBJECTS` list
- Restart the kernel and run cells sequentially

### Compatibility

The notebook includes fallback mechanisms for:
- Matplotlib style availability
- Missing electrode positions for topographic plots
- Interactive vs. static plotting environments

## Brain Wave Bands

The notebook analyzes EEG signals in standard frequency bands:

- **Delta (0.5-4 Hz)**: Deep sleep
- **Theta (4-8 Hz)**: Drowsiness, meditation
- **Alpha (8-13 Hz)**: Relaxed, eyes closed
- **Beta (13-30 Hz)**: Active thinking, focus
- **Gamma (30-50 Hz)**: High-level cognitive processing

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is open source. The PhysioNet dataset is subject to its own license terms.

## References

- [PhysioNet EEG During Mental Arithmetic Tasks Dataset](https://physionet.org/content/eegmat/1.0.0/)
- [MNE-Python Documentation](https://mne.tools/stable/index.html)
- Goldberger, A., et al. "PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals." Circulation 101.23 (2000): e215-e220.
- Zyma, I., et al. "Electroencephalograms during Mental Arithmetic Task Performance." Data 4.1 (2019): 14.

## Acknowledgments

- PhysioNet for providing the EEG dataset
- MNE-Python developers for the excellent EEG processing library
- The neuroscience community for open data initiatives
