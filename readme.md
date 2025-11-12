# StyleGAN2-ADA 环境搭建

## 1. 创建并激活conda环境（推荐）
conda create -n stylegan python=3.10
conda activate stylegan

## 2. 安装PyTorch（根据你的CUDA版本选择）
# 对于CUDA 11.8
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

## 或者对于没有GPU的机器
pip install torch torchvision torchaudio

## 3. 安装StyleGAN2-ADA-PyTorch和相关依赖
pip install click requests tqdm pyspng ninja imageio-ffmpeg==0.4.3
pip install pillow matplotlib opencv-python

## 4. 安装其他有用的库
pip install jupyterlab ipywidgets