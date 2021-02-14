## Description


## Requirements

* Google Drive account

## Getting started

Open this link on a new tab:

https://github.com/NicolasGrimonpont/Machine-Learning-Playground/blob/main/notebooks/training-model.ipynb
    
Click on this image in the new window to get started:

<img src="https://camo.githubusercontent.com/52feade06f2fecbf006889a904d221e6a730c194/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667" alt="Open In Colab" data-canonical-src="https://colab.research.google.com/assets/colab-badge.svg">

Follow the instructions on the screen and enjoy !

## Pre-trained networks

Pre-trained networks are stored as `*.pkl` files that can be referenced using local filenames or URLs:

```.bash
# Generate curated MetFaces images without truncation (Fig.10 left)
python generate.py --outdir=out --trunc=1 --seeds=85,265,297,849 \
    --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/metfaces.pkl

# Generate uncurated MetFaces images with truncation (Fig.12 upper left)
python generate.py --outdir=out --trunc=0.7 --seeds=600-605 \
    --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/metfaces.pkl

# Generate class conditional CIFAR-10 images (Fig.17 left, Car)
python generate.py --outdir=out --trunc=1 --seeds=0-35 --class=1 \
    --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/cifar10.pkl
```

## Training new networks

In its most basic form, training new networks boils down to:

```.bash
python train.py --outdir=~/training-runs --gpus=1 --data=~/datasets/custom --dry-run
python train.py --outdir=~/training-runs --gpus=1 --data=~/datasets/custom
```

## Configuration

| Base config      | Description
| :----------      | :----------
| `auto` (default) | Automatically select reasonable defaults based on resolution and GPU count. Serves as a good starting point for new datasets, but does not necessarily lead to optimal results.
| `stylegan2`      | Reproduce results for StyleGAN2 config F at 1024x1024 using 1, 2, 4, or 8 GPUs.
| `paper256`       | Reproduce results for FFHQ and LSUN Cat at 256x256 using 1, 2, 4, or 8 GPUs.
| `paper512`       | Reproduce results for BreCaHAD and AFHQ at 512x512 using 1, 2, 4, or 8 GPUs.
| `paper1024`      | Reproduce results for MetFaces at 1024x1024 using 1, 2, 4, or 8 GPUs.
| `cifar`          | Reproduce results for CIFAR-10 (tuned configuration) using 1 or 2 GPUs.
| `cifarbaseline`  | Reproduce results for CIFAR-10 (baseline configuration) using 1 or 2 GPUs.

## Development

This is a research reference implementation and is treated as a
one-time code drop. As such, we do not accept outside code
contributions in the form of pull requests.

## License

This repository is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Acknowledgements

This work is made possible by the impressive [recent work](https://nvlabs.github.io/stylegan2/versions.html) of NVidia researchers and other [previous research](https://arxiv.org/abs/2006.06676).
