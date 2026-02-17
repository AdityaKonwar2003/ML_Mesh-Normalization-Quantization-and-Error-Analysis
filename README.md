 Mesh Normalization, Quantization, and Error Analysis

This assignment focuses on fundamental data preprocessing techniques for 3D meshes, which are essential for AI systems like SeamGPT. Before any machine learning model can process 3D geometry, the data must be properly normalized and quantized to ensure consistency across different mesh scales and formats
## How to Run
1. Upload your mesh ZIP file (e.g., `8samples.zip`) to the Colab environment.
2. Run the notebook cells **top to bottom** in order:
   -  Install dependencies (`trimesh`, `open3d`, `matplotlib`, `numpy`, `plyfile`)
   -  Upload and extract the `.zip` file containing `.obj` meshes.
   -  Run Task 1–3 code blocks to process and analyze all meshes.
   -  Visualize normalized and quantized meshes (Min–Max and Unit Sphere).
  

3. All output files are saved in the `processed/` folder:
   - Normalized meshes: `*_minmax_normalized.npy`, `*_unitsphere_normalized.npy`
   - Quantized meshes: `*_minmax_quantized.npy`, `*_unitsphere_quantized.npy`
   - Reconstructed visualizations: `*_quant_recon.ply`
   - Plots and screenshots can be saved as `.png` for the report.
4. Zip the folder for submission using:
!zip -r processed_output.zip processed



---

## Tasks Overview

### **Task 1 – Load and Inspect the Mesh**
- Loads `.obj` meshes using `trimesh`
- Displays number of vertices and statistics (min, max, mean, std per axis)
- Optional: Visualize original mesh

**Output:** Printed stats + optional 3D view

---

### **Task 2 – Normalize and Quantize**
- Applies **two normalization methods**:
- Min–Max normalization → [0, 1] range
- Unit Sphere normalization → centered & scaled to unit radius
- Quantizes each normalized mesh into **1024 bins**
- Saves both normalized and quantized results

**Output:**
- Two normalized meshes  
- Two quantized meshes  
- Visualization plots (Original, Normalized, Quantized)

**Observation:**
> Both methods preserve structure, but **Unit Sphere normalization** provides more consistent scaling across different meshes.  
> **Min–Max normalization** can slightly distort meshes when one axis has smaller range.  
> Visual inspection shows minimal geometric change after quantization.

---

### **Task 3 – Dequantize, Denormalize & Measure Error**
- Reconstructs original meshes from quantized data
- Computes **Mean Squared Error (MSE)** and **Mean Absolute Error (MAE)**
- Plots error per axis

**Output:**
- Error plots for each normalization method
- Numerical results printed in notebook
- Reconstructed `.ply` meshes for viewing

**Observation:**
> The reconstruction errors are very small (close to zero), showing that quantization with 1024 bins preserves almost all geometric detail.  
> Unit Sphere normalization gave slightly lower MSE overall.


