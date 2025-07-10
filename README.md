# MNIST Delta Table Creator  
This project reads the MNIST handwritten digit dataset stored in image (PNG) format, processes a random subset of images for each digit (0–9), and stores the result as a Delta table.  

## 📁 Folder Structure  
mnist_delta/  
├── mnist_delta.ipynb   # Main notebook to process MNIST data  
├── data/               # Directory containing digit folders (0–9) with PNG images  
└── delta_output/       # Output folder for the Delta table  

## 📌 Features  
- Reads image data (28x28 grayscale PNG) from digit-labeled directories (0–9).  
- Randomly selects 5 images per digit.  
- Converts images into a Spark DataFrame with labels.  
- Saves the processed DataFrame as a **managed Delta table** (uncompressed).  

## 🧰 Technologies Used  
- Python  
- PySpark  
- Delta Lake  
- PIL (Python Imaging Library)  
- NumPy  

## 📦 Installation & Setup  
1. **Set up PySpark with Delta Lake:**  
`pip install pyspark delta-spark pillow numpy`  

2. **Clone the repository and navigate:**  
`git clone <your-repo-url>`  
`cd mnist_delta`  

3. **Prepare MNIST Data:**  
Ensure the following directory structure under the `data/` folder:  
data/  
├── 0/  
├── 1/  
├── 2/  
...  
├── 9/  
Each folder should contain the respective digit's PNG images.  

4. **Run the notebook:**  
Open and run `mnist_delta.ipynb` in Jupyter Notebook, VS Code, or any compatible environment.  

## 📊 Output  
The output Delta table will be stored in a folder named `delta_output/`, registered as a **managed table** in Spark.  

To view the data in Spark:  
```python  
spark.read.format("delta").load("delta_output/").show()  
