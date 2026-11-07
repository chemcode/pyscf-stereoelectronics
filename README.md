### GPU-Accelerated PySCF Workflow for Fluorinated Pyran Systems

A minimal, high-performance pipeline for geometry optimization and electronic structure analysis of neutral and protonated heterocycles using PySCF and the geomeTRIC solver environment. This repository provides standard, out-of-the-box notebooks optimized for GPU acceleration, seamlessly exporting standard .molden and .xyz files for downstream quantum chemical analysis. 

### 🚀 Repository Structure

The workflow is split into two hyper-focused notebooks to prevent environment clutter: 

* **notebook1.ipynb**: Baseline gas-phase workflow. Handles neutral systems using a high-quality triple-zeta basis set with GPU acceleration.
* **notebook2.ipynb**: Cationic/protonated complex workflow. Integrates a custom analytical solvent force gradient loop (IEF-PCM) mapped directly onto the GPU solver framework.

### 🛠️ Computational Methods & Specifications

* **Functional/Dispersion**: CAM-B3LYP-D3(BJ)
* **Basis Set**: def2-tzvpd (Triple-zeta with diffuse and polarization functions)
* **Optimization Engine**: geomeTRIC solver backend
* **Solvation (Aqueous Notebook)**: IEF-PCM (Water, ε = 78.35) with a dense lebedev_order = 29 angular grid mesh to eliminate numerical noise during relaxation.

### 📥 Downstream Interoperability

The scripts automatically output two universally accepted file formats: 

1. **Strict .xyz Format**: Coordinates are converted from Bohr back to Angstroms, with the final converged energy cleanly tracked in the standard second-line comment header to prevent parsing errors in strict visualizers.
2. **Standard .molden Format**: Contains the molecular geometry, basis specifications, and molecular orbital (MO) coefficients.

### Downstream Analysis Packages

The generated .molden file acts as a direct bridge into major post-processing ecosystems without requiring manual formatting tweaks: 

* **NBO / Firefly**: Ready for secondary-perturbation donor-acceptor energy analysis (ideal for tracking stereoelectronic interactions, hyperconjugation, and anomeric effects). Solvent perturbations (e.g., CH₂Cl₂) can be evaluated via single-point calculations on the optimized structures.
* **Wavefunction Topology (QTAIM)**: Seamlessly ingests into topology suites (like Multiwfn) for calculating bond critical points, electron density, and Laplacian (∇²ρ) distribution maps.
* **Visualizers**: Fully compliant with modern visualizers such as Avogadro, VMD, and Chemcraft for rendering journal-quality molecular orbital surfaces.

### 📋 Prerequisites

To run these notebooks in a GPU-enabled cloud environment (such as Google Colab), ensure the following core stacks are initialized: 

* pyscf (with GPU-accelerated modules)
* geometric
* numpy

## 📊 Data Availability

The final optimized `.xyz` coordinates, `.molden` wavefunction files, and useful logs for these pyran systems are permanently archived on Zenodo. 

DOI: [https://doi.org/10.5281/zenodo.24044748](https://doi.org/10.5281/zenodo.24044748)

## ⚙️ Administrative Note on .XYZ File Headers

To preserve the raw, unmanipulated spatial output of the geometric relaxation loops, the accompanying `.xyz` coordinate files maintain the default, software-generated text headers. 

* **The Coordinates:** The Cartesian array matrices ($X, Y, Z$) are completely untouched and remain 100% identical down to the last decimal place across all `.xyz` structural dumps, `.molden` wavefunctions, and input decks.
* **The Energy Placeholder:** Because the native file-writer outputs a static `0.000000 Hartree` comment line by default (but optional for total energy in another code cell), the true, converged total electronic energies (CAM-B3LYP-D3(BJ)/def2-TZVPD/PCM) are archived separately in the master data tables of the manuscript and the automated summary printouts. 
* **Custom Baking Option:** For users who require the explicit total energy strings baked directly into the second row of the `.xyz` file headers for third-party script parsing, an optional cleanup/patching code cell is provided in the notebook.

# 🔬 Independent Research & Data Science

> "My current independent research weaponizes automated computational chemistry pipelines to decode the exact quantum mechanical engines and real-space topological curvatures driving stereoelectronic effects that I previously exploited pragmatically at the bench during my doctoral work in complex synthetic organic methodology."

---

### 🎓 Academic & Professional Profile
* **Pedigree:** Hybrid Synthetic Organic Chemist & Open-Source Computational Developer.
* **Current Focus:** High-velocity open-science pipelines utilizing GPU-accelerated electronic structure engines (**pySCF-GPU**), localized matrix perturbations (**Firefly/GAMESS/NBO 5.9**), and real-space quantum chemical topology (**Multiwfn**).
* **Industrial Post-Doctoral Specialisation:** Industrially sponsored post-doctoral fellowship focused on **mercaptofuran synthetic chemistry**. This extensive hand-on development of complex organosulfur methodology directly informs my active research interests in mapping the distinct electronic, polarisability, and stereoelectronic anomalies of third-row heterocycles.
* **Foundational Hub:** PhD in Synthetic Organic Chemistry 
  * *Focus:* Complex heterocyclic synthesis, methodology development, and pragmatic bench-scale application of anomeric and stereoelectronic control elements.
  * *Thesis Registry:* [View Historical Dissertation Repository Link]

---

### 📂 Active Production Suites
* 📦 **Volume 1 Repository:** Automated extraction workflows mapping the deactivation and masking of the classical *exo*-anomeric engine.
* 💾 **Permanent Open Data Vault:** Complete, uncorrupted electronic fingerprints (`.molden`, `.47`, `.log`, and `.xyz` coordinates) archived transparently on Zenodo.
* 📜 **Preprint Stream:** Main text data matrices published openly on ChemRxiv.


## 📄 Preprint & Citation

A detailed discussion of the stereoelectronic effects, NBO interactions, and QTAIM topology of these substituted pyran/thiane variants can be found in the preprint on ChemRxiv:

👉 **[Read the Preprint on ChemRxiv](https://doi.org)**

If you use these notebooks or workflows in your research, please cite:
```text
Author, A. B.; Author, C. D. Title of Your Manuscript. ChemRxiv. 2026. 
DOI: 10.26434/chemrxiv.YOUR_PREPRINT_ID
```

### 🎯 The Complete Public Research Loop
By adding this, you have locked down the perfect modern open-science triangle:
1. **GitHub** hosts the reproducible workflow recipe (the notebooks).
2. **Harvard Dataverse** preserves the heavy raw ingredients (the `.molden` and `.xyz` data).
3. **ChemRxiv** delivers the final scientific discussions (the manuscript).


### 📄 License

This project is licensed under the MIT License - feel free to fork and adapt for your own molecular systems.
