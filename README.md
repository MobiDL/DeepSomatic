# MobiDL DeepSomatic

**WDL workflow for short-read somatic variant calling using deepsomatic in capture-based panel sequencing.**

---

## 📌 Overview

WDL workflow for short-read variant calling using DeepSomatic.
It is designed to be modular, reproducible, and optimized for use in clinical settings.

---

## 🛠️ Requirements

### Software Dependencies

- [WDL](https://openwdl.org/) (Workflow Description Language)
- [Cromwell](https://cromwell.readthedocs.io/) (Workflow Execution Engine)
- [Apptainer](https://apptainer.org/) (for containerized tools)

### Apptainer images

This workflow is designed to be used on HPC cluster with apptainer images.
You could install images from this repo : https://github.com/MobiDL/apptainer-recipes

### Inputs

- **Sam/Bam/Cram file(s)**
- **Reference genome** (e.g., GRCh38)
- **Target regions** (BED file for panel definition)

---

## 🚀 Quick Start

⚠️ For maximum compatibility across Cromwell and cluster backends, all input and output paths must be absolute paths.

### 1. Clone the Repository

```bash
git clone --recursive https://github.com/MobiDL/DeepSomatic.git
cd DeepSomatic
```
### 2. Backend Configuration

Before running the workflow, adapt the backend configuration to match your HPC environment.

Common parameters to review include:
- `queue`
- `tmp_dir`
- `root_dir`
- `temporary-directory`
- `root`

These parameters are usually cluster-specific and may need to be adjusted depending on your scheduler and storage architecture.

### 3. Run the Test Dataset

A minimal test dataset is available in the `tests` directory.

Update the paths in `tests/test.json`, then run:

```bash
java cromwell run DeepSomatic.wdl \
  -Dconfig.file=backends.conf/slurm_apptainer.conf \
  -i tests/test.json
```

### 3. Configure Inputs

Edit the `inputs.json` file to specify your input files and parameters:

```json
{
  "DeepSomatic.reads": "path/to/sample1.bam",
  "DeepSomatic.reference": "path/to/reference.fa",
  "DeepSomatic.target_regions": "path/to/targets.bed"
}
```

### 4. Run the Workflow

```bash
java cromwell run DeepSomatic.wdl -Dconfig.file=backends.conf/slurm_apptainer.conf -i inputs.json
```

---

## 📂 Repository Structure

```
DeepSomatic/
├── backends.conf/           # Backends sub-repository
├── modules/                 # Modules sub-repository
├── tests/                   # tests directory containing minimal dataset
├── DeepSomatic.wdl          # Main workflow file
└── README.md                # This file
```

---

## ⚙️ Workflow Steps

<img height="840" alt="deepsomatic" src="https://github.com/user-attachments/assets/edb45e8a-f98b-47a1-9e02-f6b506260ff3" />


---

## 📊 Outputs

- **VCF files**: Variant Calling Format file(s)

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

---

## 🆘 Support

For any questions or issues, please open an issue in this repository or contact us.
