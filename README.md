# FluxTrym
Dead simple web UI for training FLUX LoRA with LOW VRAM (12GB/16GB/20GB) support.

- **Frontend:**  The WebUI forked from FluxGym (Gradio UI created by https://github.com/cocktailpeanut/fluxgym/) but i customized it with my ideas
- **Backend:** The Training script powered by [Kohya Scripts](https://github.com/kohya-ss/sd-scripts)

## 2. Install Manually

First clone Fluxgym and kohya-ss/sd-scripts:

```
git clone https://github.com/laichaoyi/FluxTrym.git
cd FluxTrym
git clone -b sd3 https://github.com/kohya-ss/sd-scripts
```

Now activate a venv from the root `FluxTrym` folder:

If you're on Windows:

```
python -m venv env
env\Scripts\activate
```

If your're on Linux:

```
python -m venv env
source env/bin/activate
```

This will create an `env` folder right below the `FluxTrym` folder:

```
/FluxTrym
  app.py
  requirements.txt
  /sd-scripts
  /env
```

Now go to the `sd-scripts` folder and install dependencies to the activated environment:

```
cd sd-scripts
pip install -r requirements.txt
```

Now come back to the root folder and install the app dependencies:

```
cd ..
pip install -r requirements.txt
```

Finally, install pytorch Nightly:

```
pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu121
```

Now let's download the model checkpoints.

First, download the following models under the `models/clip` foder:

- https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true
- https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true

Second, download the following model under the `models/vae` folder:

- https://huggingface.co/cocktailpeanut/xulf-dev/resolve/main/ae.sft?download=true

Finally, donwload the following model under the `models/unet` folder:

- https://huggingface.co/cocktailpeanut/xulf-dev/resolve/main/flux1-dev.sft?download=true

The result file structure will be something like:

```
/models
  /clip
    clip_l.safetensors
    t5xxl_fp16.safetensors
  /unet
    flux1-dev.sft
  /vae
    ae.sft
/sd-scripts
/outputs
/env
app.py
requirements.txt
...
```

# Start

Go back to the root `fluxgym` folder, with the venv activated, run:

```
python app.py
```

> Make sure to have the venv activated before running `python app.py`.
>
> Windows: `env/Scripts/activate`
> Linux: `source env/bin/activate`

# Usage

The usage is pretty straightforward:

1. Enter the lora info
2. Upload images and caption them (using the trigger word)
3. Click "start".

That's all!
