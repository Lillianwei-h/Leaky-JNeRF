## 计算机图形学 Project 3 Leaky-JNeRF
This project is base on JNeRF. We have modified the model to achieve a significant improvement in performance with fewer training iterations.

### 1000 iterations training of Instant-NGP implemented by JNeRF

#### Baseline
<img src="docs/baseline.gif" width="300"/>

#### Ours
<img src="docs/ours.gif" width="300"/>

## Install
JNeRF environment requirements:

**Install the requirements & JNeRF**

```shell
git clone https://github.com/Jittor/JNeRF
cd JNeRF
conda create --name jnerf python=3.7
conda activate jnerf
python3.x -m pip install --user -e .
```

You may encounter errors, including but not limited to: g++ version does not support C++14, crypt.h not found, and many compilation errors. Please install gcc10 and g++10, and copy /usr/include/crypt.h to the python directory under the include directory of the current conda environment.

## Getting Started

### Datasets

We use blender lego datasets. 

#### Lego Dataset
You can download the lego dataset in nerf_example_data.zip at https://drive.google.com/drive/folders/128yBriW1IG_3NJ5Rp7APSTZsJqdJdfc1. And move `lego` folder to `./data/lego`.

### Config

We set the training iteration as 1000. You can change other configuratiions in `./projects/ngp/configs/ngp_base.py`.

### Train

```shell
python tools/run_net.py --config-file ./projects/ngp/configs/ngp_base.py
```

### Test with pre-trained model

After training, the ckpt file `params.pkl` will be automatically saved in `./logs/lego/`. And you can modify the ckpt file path by setting the `ckpt_path` in the config file. 

Set the `--task` of the command to `test` to test with pre-trained model:
```shell
python tools/run_net.py --config-file ./projects/ngp/configs/ngp_base.py --task test
```

### Render demo video

Set the `--task` of the command to `render` to render demo video `demo.mp4` with specified camera path based on pre-trained model:
```shell
python tools/run_net.py --config-file ./projects/ngp/configs/ngp_base.py --task render
```