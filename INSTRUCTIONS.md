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

This step will likely take several minutes.

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
            pyflow \
            Flask \
            numpy==1.24.4
```

Install `cupy`:

```bash
conda install -n generative -c conda-forge cupy==12.2.0 -y
```

After you finish installing everything:
Go to your conda environment and then navigate to `lib/python3.10/site-packages/diffusers/utils/dynamic_modules_utils.py` and edit the file.
Scroll down until you see the line which reads `from huggingface_hub import cached_download, hf_hub_download, model_info`. Remove the `cached_download,` part.

---

## Codebase Notes

### Things We Wrote

- Web server logic in `main.ipynb`
- `static/` folder
- Modifications to the `get_image` function in the `utils/utils.py` file
- Creation of `testing_data_model_runs.ipynb`
- (Sample Outputs) Added 20 images of sample data and their video outputs from the model to `testing_data/`
- We also provide GIFs of the videos in the `testing_data/output/gifs/` folder

### Things We Added

- Downloaded the `pyflow` repository
- Sample outputs in the `static/` folder
- 
- **Note:** No original license was present in the repository

### Running our approach
0. We are assuming that you run our approach on one of Rose-Hulman's servers which has a GPU (such as gebru). If you are running the **web server** on your personal computer you may need to change Flask's **host** IP address to 127.0.0.1 (which would then use local host on your personal computer).
1. What you want to do is open the `main.ipynb` file (these steps assume you have installed all of the necessary files)
2. Run all blocks of code in `main.ipynb`.
3. The last block of code starts a **web server** which should run on port 5001, specifically the web server should be accessible at [text](http://gebru.csse.rose-hulman.edu:5001/). Please **note** that this might not be the url that works for you depending on which server you run this code or if you run on your personal computer.
 
### Outputs
Our GIF results can be found in **testing_data/output/gifs**
