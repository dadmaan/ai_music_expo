# Running Riffusion Locally

You can experiment with [Riffusion](https://riffusion.com/about) model at `riffusion.com`, but you can also play with it on your local machine using the original source code or Stable Difussion `AUTOMATIC1111` web UI.

### Source Code
1. Clone the [Riffusion](https://github.com/riffusion/riffusion) here and rename it to "repo".
2. Open a terminal and run `docker compose up --build -d`
3. You can access the Streamlit interface on `localhost:8501` on your browser.

### AUTOMATIC1111
1. Run following to clone Stable Diffusion WebUI Docker `git clone https://github.com/AbdBarho/stable-diffusion-webui-docker`
2. Move to the repo. directory and run `docker compose --profile download up --build`
3. Then run the following to start the AUTOMATIC1111 UI `docker compose --profile auto up --build`
4. Now, either clone the [sd-webui-riffusion](https://github.com/enlyth/sd-webui-riffusion) inside  `./data/config/auto/extensions` directory, or use the Install from URL functionality in the UI.
5. Download the model's checkpoints from [here](https://huggingface.co/riffusion/riffusion-model-v1/tree/main) and put them in the `./data/models/Stable-Diffusion` directory.
6. For generation, select `Riffusion Audio Generator` script to use riffusion model. You can also convert a whole folder of images to audio in the `Riffusion` tab.

### Notes:
1. If you received `ERROR: InverseMelScale unexpected argument`, follow the instruction [here](https://github.com/enlyth/sd-webui-riffusion/issues/34).
2. If you want to prompt travel in the latent space as described by the authors, install this [extension](https://github.com/Kahsolt/stable-diffusion-webui-prompt-travel). It will output the results of runs in the `<SD>/outputs/(txt|img)2img-images/prompt_travel/` directory. You can use the convert folder to audio functionality in the `Riffusion` tab to generate a single stitched-together audio file alongside the individual ones.