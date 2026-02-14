# AIGC Examples

这是一个以 **Jupyter Notebook** 为主的 AIGC 学习仓库，涵盖从经典生成模型到扩散模型、视觉理解与语音合成的示例。

## 仓库内容

### 图像生成与编辑
- `DeepDream.ipynb`：DeepDream 可视化与特征放大
- `NeuralStyleTransfer.ipynb`：神经风格迁移
- `StyleGAN2-ADA.ipynb`：StyleGAN2-ADA 训练/推理实践
- `vae_mnist.ipynb`：VAE 在 MNIST 上的基础示例
- `DDPM.ipynb`：DDPM 扩散模型示例
- `StableDiffusion.ipynb`：Stable Diffusion 基础推理
- `StableDiffusion&ControlNet&IP-Adapter.ipynb`：ControlNet 与 IP-Adapter 条件生成

### 多模态与文本
- `clip.ipynb`：CLIP 图文对齐示例
- `text.ipynb`：Transformer/文本任务相关实验

### 语音
- `xtts_eg.ipynb`：XTTS 语音合成示例

---

## 快速开始（推荐）

### 1) 创建基础环境
```bash
conda create -n aigc python=3.10 -y
conda activate aigc
pip install jupyterlab ipykernel ipywidgets
```

### 2) 安装 PyTorch（二选一）

GPU（按 CUDA 版本选择）：
```bash
# CUDA 11.8
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# CUDA 12.1
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# CUDA 12.4
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124
```

CPU：
```bash
pip install torch torchvision torchaudio
```

### 3) 安装通用依赖
```bash
pip install pillow matplotlib opencv-python requests tqdm
pip install diffusers transformers accelerate
```

> 说明：大多数 notebook 在以上依赖基础上即可运行。

---

## 按主题补充依赖

### StyleGAN2-ADA
```bash
pip install click pyspng ninja imageio-ffmpeg==0.4.3
```

### Stable Diffusion（可选加速）
```bash
pip install xformers
```

### ControlNet / IP-Adapter
```bash
pip install controlnet_aux
```

### CLIP
```bash
pip install clip
```

---

## XTTS（建议独立环境）

TTS 依赖与常见图像任务存在版本冲突，建议单独环境：

```bash
conda create -n tts python=3.10 -y
conda activate tts
# 先安装与你设备匹配的 torch
pip install transformers==4.35.2
pip install "TTS[all]"
```

---

## 附录：Stable Diffusion WebUI 安装（可选）

> 该部分与本仓库 notebook 主线相对独立，仅供需要 WebUI 工作流的同学参考。

1) 克隆 `stable-diffusion-webui`（建议 `dev` 分支）

```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
git switch dev
git pull
```

或：

```bash
git clone -b dev https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
```

2) Python 环境（二选一）

- 方案 A（推荐）：Conda

```bash
conda create -n sd_webui python=3.10.6 -y
conda activate sd_webui
```

- 方案 B：直接安装 Python 3.10.6  
  下载：https://www.python.org/ftp/python/3.10.6/python-3.10.6-amd64.exe  
  安装时勾选 `Add Python to PATH`

3) 执行安装脚本（会自动构建 venv）

- Windows：`./webui-user.bat`
- Linux/macOS：`./webui.sh`

4) 若遇到 CLIP 安装失败（`Couldn't Install Clip` 或类似 `Failed to build ... CLIP ... zip`）

先修复 venv 内构建工具，再安装指定 CLIP 版本：

```bash
.\venv\Scripts\python.exe -m pip install wheel
.\venv\Scripts\Python.exe -m pip install "setuptools<70"
.\venv\Scripts\python.exe -m pip install --no-build-isolation git+https://github.com/openai/CLIP.git@d50d76daa670286dd6cacf3bcd80b5e4823fc8e1
```

5) 继续执行安装脚本

- Windows：`./webui-user.bat`
- Linux/macOS：`./webui.sh`

> 备注：以上流程主要在 Windows 侧更常见，Linux/macOS 请结合官方文档排查。

---

## 运行方式

```bash
jupyter lab
```

启动后按需打开对应 notebook。

---

## 说明

- 本仓库重点是学习与实验，不同 notebook 对显存/算力要求不同。
- 若某个 notebook 报缺包，按报错信息补装即可。
- WebUI 内容已迁移到“附录”章节，既保留信息，也避免干扰 notebook 主线。
