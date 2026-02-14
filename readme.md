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

## 运行方式

```bash
jupyter lab
```

启动后按需打开对应 notebook。

---

## 说明

- 本仓库重点是学习与实验，不同 notebook 对显存/算力要求不同。
- 若某个 notebook 报缺包，按报错信息补装即可。
- 原 README 中的 Stable Diffusion WebUI 安装内容已移除，避免与本仓库 notebook 主线混杂；如有需要建议参考其官方仓库文档。
