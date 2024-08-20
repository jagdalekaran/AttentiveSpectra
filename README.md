**Step 1: Reading and Inspecting Mosaic Files**
Script: read_inspect_mosaic

Purpose:
This script reads the .dmt mosaic files, inspects the metadata, and provides an initial visualization of the hyperspectral tiles. This step is crucial for understanding the structure of the mosaic and verifying the integrity of the data.

How to Run:

1)Open the script read_inspect_mosaic.py.

2)Set the root_directory variable to the path of raw folder containing folders within which .dmt files are placed.

3)Run the script to read and inspect each .dmt file.

Output:
The script prints out the metadata of the .dmt files and provides a visual representation of the combined mosaic image.




**Step 2: Creating Mosaic Hypercubes**
Script: create_mosaic_hypercube

Purpose:
This script stitches the individual tiles from the mosaic into a single hypercube and saves the resulting data in an HDF5 (.h5) file format. The hypercube represents the entire mosaic of spectral data.

How to Run:

1)Open the script create_mosaic_hypercube.py.

2)Set the root_directory, save_path, and save_path_image variables to the appropriate directories for input and output.

3)Run the script to generate the hypercube and save it in .h5 format.

Output:
The script produces .h5 files for each mosaic, representing the full spectral data in a single hypercube.
An enhanced TIFF image of the combined mosaic is saved for visual inspection.




**Step 3: Detecting and Extracting Individual Tissue Cores**
Script: detect_create_individual_hypercubes

Purpose:
This script detects individual tissue cores within the mosaic hypercube and extracts them as separate hypercubes. Each core is saved as an individual .h5 file.

How to Run:

1)Use the .h5 files generated in the previous step.

2)Open the script detect_create_individual_hypercubes.py.

2)Set the directory_path to the folder containing the hypercubes and save_directory to where the extracted cores should be saved.

3)Run the script to detect cores and save them as separate .h5 files.

Output:
The script produces individual .h5 files for each detected tissue core.




**Step 4: Identifying and Renaming Hypercubes**
Script: hypercube_identifier

Purpose:
This script compares the extracted cores against reference images, identifies them, and renames the hypercubes accordingly.

How to Run:

1)Ensure that your reference images are in place and that the extracted hypercubes are saved.

2)Open the script hypercube_identifier.py.

3)Set the paths for the reference images, query images, and the output CSV file.

4)Run the script to match the extracted cores with their corresponding references.

4)Once the matching process is complete, use the script to rename the hypercubes based on the identified matches.

Output:
A CSV file mapping the original hypercube names to their identified reference names.
The extracted hypercubes are renamed accordingly and saved in the specified output directory.




**Step 5: Training the CNN-Spectral Attention Model**
Script: cnn_spectral_attention

Purpose:
This script builds and trains the CNN-RNN hybrid model with a Global Spectral Attention Mechanism using the preprocessed hypercubes. The model is then evaluated on the test set.

How to Run:

1)Ensure that your training and validation data (extracted hypercubes) are ready.

2)Open the script cnn_spectral_attention.py.

3)Set the paths for the training and testing directories.

4)Run the script to start the training process.

The script will automatically save the best model and produce plots for accuracy, loss, and attention weights.

Output:
A trained model saved in .keras format.
Plots showing the training history and attention weights.
Evaluation metrics such as accuracy, confusion matrix, and classification report.

**Link to the dataset: https://zenodo.org/records/4986399**
All the .7z folders need to be downloaded individually and then extracted into a one single folder. 

To make use of GPU while training the model, make sure the Tensorflow version is compatible with the cuda version.
Eg For Tensorflow 2.17.0 you need Cuda 12.3 and cuDNN 8.9 with Python 3.9-3.12
You can chekc the compatiblity here : https://www.tensorflow.org/install/source#gpu
