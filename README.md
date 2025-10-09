# Stable Diffusion WebUI Forge 整合包使用说明

## 简介

旧整合包已不适用日益更新的AI应用与50系显卡，为此我更新了新整合包环境，补充落后的webui生态。

新整合包修复了ADetailer修脸插件，wd1.4标签器等bug。

## ControlNet 模块说明

ControlNet模块不支持FLUX ControlNet模型。在此前我们尝试过让Forge环境支持FLUX ControlNet，但未能成功，无法与XL ControlNet张量同时兼容在一个插件内。由于对ControlNet的设计代码不是很了解，即使是参考哩布哩布平台也没有实现FLUX ControlNet模块。这个问题比较复杂，只能等技术大佬解决。

## 模型支持情况

最新更新的视频生成模型wan2.2，Qwen-Image等14B或20B参数量的模型应用环境倒是支持的，但是部署起来极其消耗显存。对于diffusion库的加载方式和配置要求优化确实不如ComfyUI。不过生图模型还是够用的，因为WebUI Forge使用的也是类似的ComfyUI优化策略。

对于ComfyUI复杂的节点连线式操作界面，对新手确实不太好学习。WebUI Forge更加易操作，好理解，适合入门，熟悉之后再接触ComfyUI更为合适。

## 下载地址

### 大陆国内用户
通过网盘分享的文件：更新环境库的webui Forge整合包  
链接: https://pan.baidu.com/s/1FL7WVbcdvHfMtGUs-QOTVg 提取码: jwmu

### 海外用户
更新的Forge环境（由于体积较大无法方便上传只能如此了）  
需要以下依赖：
```
diffusers==0.35.1
Torch 2.7.0 (CUDA 12.8)+ xFormers 0.0.30
transformers==4.53.1
huggingface-hub==0.34.4
可参考首页的requirements_versions.txt依赖文件

此整合包支持：
- 1.5模型
- XL模型 
- FLUX模型
- LoRA加载
- XL ControlNet等模块
- 不支持FLUX ControlNet


模型都在网盘中
<img width="1417" height="887" alt="Snipaste_2025-10-09_19-18-00" src="https://github.com/user-attachments/assets/c57b071e-b0e0-4973-a683-6da96740269d" />
使用7z压缩软件进行解压整合包

海外用户搜索模型名称下载
https://huggingface.co/yeqiu168182/flux1-dev-kontext_fp8_scaled.safetensors/tree/main

<img width="1613" height="455" alt="26" src="https://github.com/user-attachments/assets/4ef92d94-6229-4754-9f8c-4ff7fbac36c6" />



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



## 各类模型加载方式

### FLUX模型加载方式
需要以下模型文件：
- 主模型: `flux1-dev-fp8.safetensors`
- 文本编码模型: `t5xxl_fp8_e4m3fn.safetensors`
- CLIP模型: `clip_l.safetensors`
- VAE模型: `flux-ae.safetensors`
<img width="1600" height="95" alt="24" src="https://github.com/user-attachments/assets/c94d496a-ad36-4218-9803-8fdaa986677e" />

<img width="910" height="348" alt="123" src="https://github.com/user-attachments/assets/2f0b6081-ba91-454c-a4ef-8136f43a0373" />


### XL模型加载方式
- 主模型（约6GB)
- VAE模型: `sdxl_vae.safetensors`
<img width="1092" height="810" alt="25" src="https://github.com/user-attachments/assets/c52b9db3-fcc7-4c58-8434-adc0a306a6b6" />

### 1.5模型加载方式
- 主模型（约2.3GB)
- VAE模型: `vae-ft-mse-840000-ema-pruned.safetensors`


