# a geospatial approach to identifying optimal adolescent mental health service locations in toronto

DOI: [10.17975/sfj-2025-014](https://doi.org/10.17975/sfj-2025-014)

**Usage**
- **Purpose**: This repository contains preprocessing and clustering scripts and Jupyter notebooks used to identify prioritized neighborhoods for adolescent mental health services in Toronto.

**Setup**
- **Create virtual environment (PowerShell)**:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

- **Alternative (conda recommended for geopandas)**:

```powershell
conda create -n geog python=3.10 -y
conda activate geog
conda install -c conda-forge geopandas jupyter scikit-learn folium -y
pip install -r requirements.txt
```

**How to run**
- **Jupyter Notebooks**: Open `Jupyter Notebooks/Clustering_and_Radius_Search.ipynb` and `Jupyter Notebooks/Preprocessing.ipynb` in Jupyter or JupyterLab and run cells interactively.
- **Python scripts**:
	- `Python Files\preprocessing.py`: performs shapefile loading, clipping, and heatmap generation.
	- `Python Files\clustering_and_radius_search.py`: computes normalized neighborhood scores, runs DBSCAN clustering, and searches potential facility locations.

Run a script from PowerShell (after activating the venv):

```powershell
python "Python Files\preprocessing.py"
python "Python Files\clustering_and_radius_search.py"
```

**Working with Google Drive / Colab**
- To run the notebooks in Google Colab with your data stored in Google Drive:
	1. Upload the folder `Mental Health Location BDC 2024 Datafiles` (the same folder structure used in the notebooks) to your Google Drive root.
	2. Open the notebook in Colab. In the first cells you can uncomment the `drive.mount(...)` call to mount Drive.
	3. Set `DATA_DIR = '/content/drive/MyDrive'` or keep the default `DATA_DIR` and ensure `DATA_ROOT = f"{DATA_DIR}/Mental Health Location BDC 2024 Datafiles"` points to the folder you uploaded.

- When running the Python scripts locally, place the `Mental Health Location BDC 2024 Datafiles` folder under a `data/` directory in the repo (so files are at `data/Mental Health Location BDC 2024 Datafiles/...`).

**Script arguments**
- Both `preprocessing.py` and `clustering_and_radius_search.py` accept a `--data-dir` argument (defaults to `data`) and `clustering_and_radius_search.py` also accepts `--output-dir` (defaults to `output`). Example:

```powershell
python "Python Files\preprocessing.py" --data-dir "data"
python "Python Files\clustering_and_radius_search.py" --data-dir "data" --output-dir "output"
```

If you prefer Colab, you can mount Drive and set `DATA_DIR='/content/drive/MyDrive'`.