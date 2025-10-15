<h1 align="center">
LIBERO-Plus: In-depth Robustness Analysis of Vision-Language-Action Models
</h1>

<p align="center">
  📄 <a href="https://github.com/sylvestf/LIBERO-plus"><strong>Paper</strong></a> |   
  🏗️ <a href="https://huggingface.co/datasets/Sylvest/LIBERO-plus/tree/main"><strong>Assets</strong></a> | 
  🌐 <a href="https://sylvestf.github.io/LIBERO-plus"><strong>Website</strong></a>
</p>


## 🔥 Overview
This repository contains the official implementation and benchmark for our paper "In-depth Robustness Analysis for Vision-Language-Action Models". We systematically expose the hidden vulnerabilities of contemporary VLA models through comprehensive robustness evaluation across seven perturbation dimensions. You can simply replace the original `libero` with a `pip install -e .` without modifying your code.

## 🚀 Key Findings
- **Significant Fragility**: VLA models exhibit extreme sensitivity to camera viewpoints and robot initial states, with performance dropping from 95% to below 30% under modest perturbations
- **Language Ignorance**: Models largely ignore language instructions, functioning more like Vision-Action models
- **Negative Compositional Generalization**: Combined perturbations reveal complex interaction effects beyond independent factors

## 📊 LIBERO-plus Benchmark

### 7 Perturbation Dimensions
We introduce **LIBERO-plus**, a comprehensive benchmark with 10,030 tasks spanning:

1. **Objects Layout** - Confounding objects and target object displacement
2. **Camera Viewpoints** - Position, orientation, and field-of-view changes
3. **Robot Initial States** - Manipulator initial pose variations
4. **Language Instructions** - LLM-based instruction rewriting
5. **Light Conditions** - Intensity, direction, color, and shadow variations
6. **Background Textures** - Scene and surface appearance changes
7. **Sensor Noise** - Photometric distortions and image degradation

### Evaluated Models
- OpenVLA and variants (OFT, OFT_w, OFT_m)
- π₀ and π₀-fast
- Nora, WorldVLA, UniVLA, RIPT-VLA

## 🛠️ Installation
The usage of this project is identical to [LIBERO](https://github.com/Lifelong-Robot-Learning/LIBERO). Simply replace the originally installed LIBERO repository with our repository without modifying your code.

```bash
# Clone our repository
git clone https://github.com/sylvestf/LIBERO-plus.git
cd LIBERO-plus
```

If you have LIBERO installed, please uninstall or remove it first. Please verify if the repo path in the following configuration file needs to be updated to path_to_liberoplus_repo.
Here are the default paths for the configuration files: `/root/.libero/config.yaml`. You can check your `libero_config_path` at `path_to_your_LIBERO_repo/libero/libero/__init__.py`.

Then install our new LIBERO repository
```bash
# Install the new LIBERO package
pip install -e .

# New dependencies installed on top of LIBERO
apt install libexpat1
apt install libfontconfig1-dev
apt install libpython3-stdlib
apt-get install libmagickwand-dev
pip install -r extra_requirements.txt
```

Please download our assets from [LIBERO-plus](https://huggingface.co/datasets/Sylvest/LIBERO-plus/tree/main), including hundreds of new objects, textures, and other required assets. Please unzip the `assets.zip` file to `/LIBERO-plus/libero/libero` path.
The extracted directory structure should look like:

```text
LIBERO-plus/
└── libero/
    └── libero/
        └── assets/
            ├── articulated_objects/
            ├── new_objects/
            ├── scenes/
            ├── stable_hope_objects/
            ├── stable_scanned_objects/
            ├── textures/
            ├── turbosquid_objects/
            ├── serving_region.xml
            ├── wall_frames.stl
            └── wall.xml
```


## 🔧 Evaluation
The evaluation method is almost identical to `LIBERO`. The only required modification is adjusting `num_trials_per_task` from 50 to 1 in your configuration.

## Citation
If you find this work useful for your research, please cite our paper:
```bibtex
@misc{ ,
      title={WIn-depth Robustness Analysis for Vision-Language-Action Models}, 
      author={ },
      year={2025},
      eprint={ },
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={ }, 
}
```
