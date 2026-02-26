# TreeDetection

A Python tool for processing large GeoTIFF images by slicing them into smaller tiles, running YOLO object detection, and generating both a stitched output image and a shapefile of detections.

## Overview

This tool is designed to handle large GeoTIFF images by breaking them down into manageable tiles, running YOLO object detection on each tile, and then reassembling them into a complete image. It also generates a shapefile containing the geographic coordinates of all detections. The tool can be used either through a command-line interface or a web interface.

## Features

- Slice large GeoTIFF images into smaller tiles
- Run YOLO object detection on each tile
- Draw detection boxes on the processed images
- Generate a shapefile of detection coordinates
- Preserve original GeoTIFF metadata and coordinate system
- Web interface for easy file upload and processing
- Command-line interface for batch processing

## Requirements

- Python 3.10
- Required packages:
  - numpy
  - PIL (Python Imaging Library)
  - rasterio
  - fiona
  - shapely
  - ultralytics (YOLO)
  - flask (for web interface)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ConservationDronesAI/TreeDetection.git
   cd TreeDetection
   ```

### Using Conda

1. Create a new conda environment:
   ```bash
   conda create -n TreeDetection python=3.10
   ```

2. Activate the environment:
   ```bash
   conda activate TreeDetection
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Web Interface

1. Start the web server:
   ```bash
   python webapp.py
   ```

2. Open your web browser and navigate to `http://localhost:5000`
3. Upload a GeoTIFF file through the web interface
4. The tool will process the image and provide download links for:
   - The stitched GeoTIFF with detection boxes
   - The shapefile containing detection coordinates

### Command Line Interface

The main script `EndToEnd.py` provides a complete pipeline for image processing:

```python
from EndToEnd import run_end_to_end

run_end_to_end(
    original_tiff_path='path/to/input.tif',
    sliced_dir='sliced_tiles',
    detected_dir='detected_tiles',
    output_tiff_path='outputs/stitched_output.tif',
    output_shp_path='outputs/detections.shp',
    tile_size=(512, 512),  # Optional: customize tile size
    model_path='best.pt',  # Optional: specify YOLO model
    conf=0.3  # Optional: detection confidence threshold
)
```

## File Structure

- `EndToEnd.py`: Main processing script
- `webapp.py`: Web interface implementation
- `best.pt`: YOLO model weights
- `uploads/`: Directory for uploaded files
- `outputs/`: Directory for final output files
- `sliced_tiles/`: Directory for intermediate sliced tiles
- `detected_tiles/`: Directory for processed tiles with detections

## Output Files

1. **Stitched GeoTIFF**: Contains the original image with detection boxes drawn on it
   - Preserves all original GeoTIFF metadata
   - Maintains the original coordinate system
   - Detection boxes are drawn in red

2. **Shapefile**: Contains the geographic coordinates of all detections
   - Includes .shp, .shx, .dbf, and .prj files
   - Uses the same coordinate system as the input GeoTIFF
   - Each detection is stored as a polygon feature

## Notes

- The tool uses YOLO for object detection, which requires a trained model (provided as `best.pt`)
- Make sure to have sufficient disk space for the intermediate files
- The web interface is intended for development/testing; for production use, consider adding proper security measures
- The shapefile output requires all associated files (.shp, .shx, .dbf, .prj) to be used properly in GIS software

## License: TBD

## Add a funny joke below here


| Name / Nom | Joke in Malagasy / Blague en Malagasy | Translation / Traduction |
|------------|---------------------------------------|--------------------------|
| Steven Longmore | Nahoana ny lemur no tsy mampiasa ordinatera? Satria matahotra ny "mouse" izy! | Why don't lemurs use computers? Because they're afraid of the mouse! |
| RAOELIARIMANANA | Rehefa manao régime hono dia tsy mihinana intsony… fa manandrana tsiro fotsiny impiry impiry isan’andro| |
| NahojRavelo | “Anaka, inona no tianao hatao rehefa lehibe ianao ?” “Te ho mpamily fiara aho dada.” “Fa maninona ?” “Satria na tara aza dia mbola lazaina hoe ‘tonga ara-potoana’ ” “Ahoana izany ?” “Satria hoe : tonga ihany!” | |
| Tahiana | Mpampianatra : Iza no mahay miteny ahy hoe inona no atao hoe “Fahanginana” Mpianatra : Tsy haiko, Ramose… fa rehefa mangina izahay dia ianao no tsy mangina | |
| MikaRandrianasolo | Rabofy: Fa aiza le télé sy le frigo teto ? Za efa aty am La Résidence Ankerana miaraka am drone manatrika anle atelier | |
| Tsiky | “Fa maninona ianao no mihomehy irery?” “Satria lafo be ny data, ka aleoko mihomehy irery toy izay hizara vazivazy!” | |
| Fabrice | Miangavy an'i Steeve mba handihy eo ampovoany | |
| LazaHarifetra | Mpampianatra : Manome inona ny Omby? Soa : Manome ronono madama, Mpampianatra: manome inona ny akoho, Soa : manome atody madama......, Mpampianatra: manome inona ny Kisoa, Soa: Manome devoir madama | |
| Angelo | Lohateny: Fampandrosoana haingana sy maharitra, Nifampiresaka izy mianaka (D/Z), Z: Dada ah, ividiano caca pigeon aho., D: Hay ianao tia caca pigeon be?, Z: Eny ry Dada, D: Aleo fa hividianako pigeon ianao ary! | |
| Tojo | Mety ingenieur civil angamba ny Tompo satria nataony nifanakaiky ny kilalao sy fanariam-pako | |
| MamitianaRaks | Inona no mahasamy hafa ny olona adala sy ny ny tsy adala, satria ny olona adala iany tsy miheritreritra hoe adala izy, fa ny olona tsy adala mieritreritra foana hoe sao dia ho lasa adala. Le taikalahy ty, Hingaiko ny rambon'omby dia ianao no hitako ao, | |
| Maneva | Zaza: "Dada ô, nahoana isika no tsy manan-karena?" Dada: "Satria isika tsy manana vola, anaka." Zaza: "Fa nahoana isika no tsy manana vola?" Dada: "Satria isika tsy manan-karena!" | |
| Rindra | Very ny la clé anefa ny andro efa ariva, Poly: Inona lesy izany alaon'ialahy izany ry JeanBA, JeanBA: Very lesy ny la clé ako ah, Poly: Fa taiza no very , JeanBA: Tery @maizina tery fa eto no mazava dia eto ah no mitady azy | |

ampoule 

