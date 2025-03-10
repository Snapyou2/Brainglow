# Brainglow : Brain regions intensity quantification and visualization

Brainglobe has been thought to help quantifying the intensity of brain regions from registered atlas on lightsheet microscopy, and provides visualizations using bar graphs and interactive sunburst diagrams.

![interactive sunburst charts](https://github.com/user-attachments/assets/ea4d10c8-181a-4e11-b631-c507b9d04040)

![bar graphs](https://github.com/user-attachments/assets/9c5ff741-5864-4634-b111-8d2c86700369)

## Usage

1. **Input Files:** Prepare the following input files after running brainreg on every channel for your brain (signal and autofluorescence channels):
    - `registered_atlas.tiff`: Allen atlas labels mask by brainreg, can be obtained using a reference image like autofluorescence at 561nm
    - `downsampled.tiff`: Brain image that contains your target channel intensity signal, with high SNR if possible.
    - `structures.csv`: Region names, IDs, acronyms, and parent structure, from the allen atlas project (included in this repo).
    - `volumes.csv`: Region volumes, computed by brainreg. Use the one detected in 561nm image if possible.

2. **Intensity Quantification:** Run the `quantification.ipynb` notebook. This notebook loads the input data, calculates the total intensity for each brain![bargraph](https://github.com/user-attachments/assets/98865dcf-78ff-4002-![bargraph](https://github.com/user-attachments/assets/00faa8df-d561-4570-8a30-8a1683270d1c)
96fb-a967e0a73b3e)
 region, and saves the results to `quanti.csv`.

3. **Visualization:**
    - Use `bar_graphs.ipynb` to create bar graph visualizations of the quantification results.
    - Use `sunburst.ipynb` to generate interactive sunburst diagrams for hierarchical exploration of the data.

## Output Files

- `quanti.csv`: Quantification results containing structure name, total intensity, volume, and intensity per volume.
- `xxx_sunburst.html` : Interactive sunburst charts based on the quanti.csv file to explore the data in html version (can be opened in any browser)
- Bar graphs can be saved easily in png format manually from the jupyter notebook preview if needed.

## Requirements

The required Python libraries are listed in `requirements.txt`. You can install them using:

```bash
pip install -r requirements.txt
```

## Hardware

Brainglow uses Dask to parallelize processing tasks and will extensively use your CPU. RAM usage can go up to 30 GB for region intensity calculation, with 10um atlas registration. Use an appropriate computer or server.
