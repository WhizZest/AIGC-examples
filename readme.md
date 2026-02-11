# 环境搭建

## 1. 创建并激活conda环境（推荐）
```
conda create -n aigc python=3.10
conda activate aigc
conda install ipykernel
```

## 2. 安装PyTorch（根据你的CUDA版本选择）
# torch + CUDA 11.8
```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118```
# torch + CUDA 12.1
```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121```
# torch + CUDA 12.4(推荐，兼容性更好，部分模型需要)
```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124```

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

### Stable Diffusion WebUI安装
1. 克隆仓库，由于主分支最后更新时间是两年前（2024年），dev分支最后更新时间是2025年12月18日，并且根据issue#17213和#17235的反馈，dev分支可以正常使用，因此选择dev分支。
```
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
git switch dev
git pull
```
或者
```
git clone -b dev https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
```
2. Python环境（二选一）
方案A：使用Conda（推荐，环境隔离）
```
conda create -n sd_webui python=3.10.6 -y
conda activate sd_webui
```
方案B：直接安装Python 3.10.6
下载：https://www.python.org/ftp/python/3.10.6/python-3.10.6-amd64.exe
安装时务必勾选"Add Python to PATH"

3. 执行安装脚本，这个过程会构建venv环境
windows: ```.\webui-user.bat```
linux/mac: ```./webui.sh```
4. 解决clip安装失败问题
如果遇到Clip安装失败：```Couldn't Install Clip```或```ERROR: Failed to build 'https://github.com/openai/CLIP/archive/d50d76daa670286dd6cacf3bcd80b5e4823fc8e1.zip'```，先修复venv环境的构建工具，再安装clip：
```
.\venv\Scripts\python.exe -m pip install wheel
.\venv\Scripts\Python.exe -m pip install "setuptools<70"
.\venv\Scripts\python.exe -m pip install --no-build-isolation git+https://github.com/openai/CLIP.git@d50d76daa670286dd6cacf3bcd80b5e4823fc8e1
```
5. 继续执行安装脚本
windows: ```.\webui-user.bat```
linux/mac: ```./webui.sh```

ps：没测试过linux/mac。



## 8. 安装ControlNet和IP-Adapter相关依赖
```pip install diffusers transformers accelerate controlnet_aux pillow opencv-python```

### 9. 安装TTS相关依赖
由于TTS的依赖版本与其他模型不同，因此需要单独创建环境并安装：
1. 创建并激活conda环境
```
conda create -n tts python=3.10
conda activate tts
```
2. 安装PyTorch（根据你的CUDA版本选择）同上
3. 安装TTS相关依赖（需要降级transformers，否则运行失败）
```
pip install transformers==4.35.2
pip install TTS[all]
```

### 10. Tramsformer相关依赖
1. 核心库
```
pip install transformers
```
2. 网络库
```
pip install requests
```
3. 其他
```
pip install accelerate  # 必须，用于模型加载
pip install protobuf    # ChatGLM需要
pip install sentencepiece  # 某些tokenizer需要
pip install peft        # 可选，用于模型微调
```