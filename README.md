# Stable Diffusion WebUI Forge 整合包使用说明

## 简介

2025/10/12 更新多模态SD插件12版本
https://github.com/exo101/sd-webui-MultiModal/tree/main

一个为 Stable Diffusion WebUI Forge 设计的多功能集成插件

## 系统要求

- 显卡：最低推荐 NVIDIA RTX 3060 /中端NVIDIA RTX 4070/中高端NVIDIA RTX 5070ti
- 显存：至少 12GB
- 内存：推荐 32/64GB 
     
## 核心功能

- 📚 **资源汇总**: 集中管理各类资源和公告信息
- 🖼️ **图像识别与语言交互**: 支持多种视觉和语言模型，可进行图像描述、内容分析等
- ✂️ **智能抠图**: 基于 rembg 实现一键背景移除
- 🖌️ **图像分割**: 集成 Segment Anything Model (SAM) 进行精确图像分割
- 🧹 **图像清理**: 提供图像清理和修复功能
- 🎬 **视频关键帧提取**: 从视频中提取关键帧用于进一步处理
- 🤖 **数字人视频生成**: 基于 LatentSync 实现音频驱动的数字人视频生成
- 🔊 **TTS语音合成**: 集成 Index-TTS 实现高质量文本转语音
- 🌟 **FLUX.1 图像编辑**: 集成 FLUX.1-Kontext 进行上下文感知的图像编辑
- 🌟 **Qwen-Image复杂文本渲染和qwen-image-edit-2509精确图像编辑 

旧整合包已不适用日益更新的AI应用与50系显卡，为此我更新了新整合包环境，补充落后的webui生态。

新整合包修复了ADetailer修脸插件，wd1.4标签器等bug。

## ControlNet 模块说明

ControlNet模块不支持FLUX ControlNet模型。在此前我们尝试过让Forge环境支持FLUX ControlNet，但未能成功，无法与XL ControlNet张量同时兼容在一个插件内。由于对ControlNet的设计代码不是很了解，即使是参考哩布哩布平台也没有实现FLUX ControlNet模块。这个问题比较复杂

后续可更根据量化库更新，FLUX ControlNet，Qwen-Image ControlNet

对于ComfyUI复杂的节点连线式操作界面，对新手确实不太好学习。WebUI Forge更加易操作，好理解，适合入门，熟悉之后再接触ComfyUI更为合适。

## 下载地址可查看个人主页视频简介下方：

[https://www.bilibili.com/video/BV1BCHXzJE1C/?spm_id_from=333.788.videopod.sections&vd_source=343e49b703fb5b4137cd6c1987846f37](https://www.bilibili.com/video/BV1FWtBzbEiR?spm_id_from=333.788.player.switch&vd_source=343e49b703fb5b4137cd6c1987846f37&trackid=web_related_0.router-related-2206419-r6wc2.1760535637914.805)

diffusers==0.36.0.dev0
Torch 2.7.0 (CUDA 12.8)+ xFormers 0.0.30
transformers==4.53.1
huggingface-hub==0.34.4
可参考首页的requirements_versions.txt依赖文件

此整合包支持：
- qwen-image-edit
- qwen-image
- qwenVL
- Index-TTS2
- LatentSync
- Ollama,deepseek
- Segment Anything
- FLUX.1-Kontext
- FLUX
- 1.5
- XL
- LoRA
- XL ControlNet
- 不支持FLUX ControlNet

## 界面介绍

### GPU 显存管理
GPU Weights (MB)滑动条的数值就是显存的容量：
- 往左滑动是模型权重加载
- 往右是模型计算空间
正常情况下：
- 往右滑动过半，留出20%-40%的计算空间
- 如果模型权重预留的空间不足，模型会加载失败
- 如果模型计算空间不足，会生成时间变慢，程序崩溃爆显存

<img width="1720" height="165" alt="11" src="https://github.com/user-attachments/assets/45008dd6-cb33-41f4-b9a2-a312d388cc61" />

| 模型类型 | 目录路径 |
|---------|---------|
| 主模型 | `sd-webui-forge-aki-v4.0\models\Stable-diffusion` |
| LoRA模型 | `sd-webui-forge-aki-v4.0\models\Lora` |
| VAE模型 | `sd-webui-forge-aki-v4.0\models\VAE` |
| 高清放大模型 | `sd-webui-forge-aki-v4.0\models\RealESRGAN` |
| ControlNet模型 | `sd-webui-forge-aki-v4.0\models\ControlNet` |
| ControlNet预处理器 | `sd-webui-forge-aki-v4.0\models\ControlNetPreprocessor` |
| 插件目录 | `sd-webui-forge-aki-v4.0\extensions` |

模型都在网盘中
使用7z压缩软件进行解压整合包

## 各类模型加载方式

### FLUX模型加载方式
需要以下模型文件：
- 主模型: `flux1-dev-fp8.safetensors`
- 文本编码模型: `t5xxl_fp8_e4m3fn.safetensors`
- CLIP模型: `clip_l.safetensors`
- VAE模型: `flux-ae.safetensors`
- flux参数设置：采样方法Euler，调度器Simple， CFG引导数3.5，迭代步数20-35
<img width="1600" height="95" alt="24" src="https://github.com/user-attachments/assets/c94d496a-ad36-4218-9803-8fdaa986677e" />

<img width="910" height="348" alt="123" src="https://github.com/user-attachments/assets/2f0b6081-ba91-454c-a4ef-8136f43a0373" />


### XL模型加载方式
- 主模型（约6GB)
- VAE模型: `sdxl_vae.safetensors`
- XL参数设置：采样方法DPM++ 2M SDE，调度器Karras， CFG引导数7，迭代步数20-35
<img width="1092" height="810" alt="25" src="https://github.com/user-attachments/assets/c52b9db3-fcc7-4c58-8434-adc0a306a6b6" />

### 1.5模型
- 主模型（约2.3GB)参数与XL无差别
- VAE模型: `vae-ft-mse-840000-ema-pruned.safetensors`
  
### 高清放大模型参数设置
低配置用户需要调低基础尺寸，开启放大2倍，如果基础尺寸很大，放大倍数就要调低，模型参数越大放大的尺寸需要的显存压力也会越大
<img width="880" height="187" alt="22" src="https://github.com/user-attachments/assets/d9936900-fea9-43e8-928d-bf1ef6721582" />

### PS AI插件
- ps 2023最为稳定
- 由两个包组成才行完成运行
- 1.整合包ps插件的部分Auto-Photoshop-StableDiffusion-Plugin,已安装在整合包当中无需再下载安装
- 2.PS插件部分放置ps2023\Adobe Photoshop 2023\Plug-ins
-<img width="671" height="312" alt="Snipaste_2025-10-11_11-45-18" src="https://github.com/user-attachments/assets/a57b5787-120c-42af-9df1-1a2b677e2348" />

- 地址 Auto.Photoshop.SD.plugin_v1.4.1 https://github.com/AbdullahAlfaraj/Auto-Photoshop-StableDiffusion-Plugin/releases/tag/v1.4.1
 <img width="691" height="493" alt="88" src="https://github.com/user-attachments/assets/19f0cc5a-68f7-42d0-89ef-8fbedf995cda" />
 <img width="1860" height="1024" alt="33" src="https://github.com/user-attachments/assets/9f9ec311-7a3d-4d12-bc45-5a3a317e0ddb" />

- 插件设置：可同时链接Webui与comfyui，Automatic111就是Webui的链接后端，zh_CN设置为中文
- <img width="614" height="804" alt="55" src="https://github.com/user-attachments/assets/dce00245-cdb3-49ca-a421-6d9cf348f585" />
- 功能演示教程请看此视频https://www.bilibili.com/video/BV1ybv4ehEAP?spm_id_from=333.788.videopod.sections&vd_source=343e49b703fb5b4137cd6c1987846f37

### wd1.4标签器插件
- 选择模型wd14-vit-v2-git
- <img width="879" height="428" alt="66" src="https://github.com/user-attachments/assets/ec5cac8f-6ec7-434a-857a-1066908320ef" />
- <img width="1805" height="759" alt="77" src="https://github.com/user-attachments/assets/2b2caba2-a8e7-4327-a9c5-cc349a13a530" />
- 整合自带的标签器识别的提示词远不如Qwen-VL、LLaMA-Vision等视觉模型来的提示词质量与丰富，准确率很低，只方便与快速识别与制作二次元动漫人物
- 高质量提示词请使用多模态插件 https://github.com/exo101/sd-webui-MultiModal

