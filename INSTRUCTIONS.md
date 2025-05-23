## File Download and Setup

You need to download and unzip the following file into the `data/models` directory:

[Download the file](https://1drv.ms/u/s!AjGGQwItv34-bK738lmdo7wf2uk?e=cWvbXo)

After extracting, your directory structure should look like this:

```
data/models/unet/diffusion_pytorch_model.safetensors  
data/models/unet/config.json  
data/models/frame_synthesis.pth
```

---

## Environment Setup

> **Important:** Use a **Conda environment** with **Python 3.10.12**

First, we need to create our conda environment and register it with ipkernel so that juytper notebook can "see" it properly.
```bash
conda create -n generative python=3.10.12 -y
conda activate generative
pip install ipykernel
python -m ipykernel install --user --name=generative --display-name "Python (Generative Image Dynamics)"

```

Install required Python packages:

```bash
pip install torch==2.3.0 \
            torchvision==0.18.0 \
            diffusers==0.28.0 \
            torchmetrics==1.4.0 \
            opencv-python==4.8.0.74 \
            scipy==1.11.4 \
            matplotlib==3.7.1 \
            moviepy==1.0.3 \
            transformers==4.39.3 \
            cupy==12.2.0 \
            pyflow \
            numpy==1.24.4
```

Or via Conda (recommended for `cupy`):

```bash
conda install -n generative -c conda-forge cupy==12.2.0 -y
```

---

## Codebase Notes

### Things We Wrote

- Web server logic in `main.ipynb`
- `static/` folder
- Modifications to the `utils.py` file

### Things We Added

- Downloaded the `pyflow` repository
- Sample outputs in the `static/` folder
- **Note:** No original license was present in the repository
