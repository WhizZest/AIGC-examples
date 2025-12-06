# 环境搭建

## 1. 创建并激活conda环境（推荐）
```
conda create -n aigc python=3.10
conda activate aigc
```

## 2. 安装PyTorch（根据你的CUDA版本选择）
# 对于CUDA 11.8
```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118```
# 对于CUDA 12.1
```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121```

## 或者对于没有GPU的机器
pip install torch torchvision torchaudio

## 3. 安装StyleGAN2-ADA-PyTorch和相关依赖
```
pip install click requests tqdm pyspng ninja imageio-ffmpeg==0.4.3
pip install pillow matplotlib opencv-python
```

## 4. 安装其他有用的库
```pip install jupyterlab ipywidgets```

## 5. 安装DDPM相关依赖
```pip install diffusers transformers accelerate```

## 6. 安装CLIP相关依赖
```pip install clip```

## 7. 安装Stable Diffusion相关依赖
```pip install diffusers transformers accelerate xformers```

- diffusers: 提供扩散模型的核心实现和管道。

- transformers: 提供文本编码器（CLIP）。

- accelerate: 用于优化推理速度。

- xformers: (可选) 可以进一步加速推理并减少内存占用。

## 8. 安装ControlNet和IP-Adapter相关依赖
```pip install diffusers transformers accelerate controlnet_aux pillow opencv-python```