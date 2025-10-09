# Stable Diffusion WebUI Forge 环境
旧整合包已不适用日益更新的AI应用与50系显卡，我为此更新了新整合包环境，补充落后的webui生态

新整合包修复了ADetailer修脸插件，wd1.4标签器等bug

ControlNet模块不支持FLUX ControlNet模型 在此之前去尝试过让Forge 环境支持FLUX ControlNet，努力无果，无法与XL ControlNet张量同时兼容在一个插件内 本人对 ControlNet的设计代码不是很了解，头一次尝试用ai辅助写的插件，包括哩布哩布平台也没有去做FLUX ControlNet模块 估计是不太好弄，只能等大佬解决了

最新更新的视频生成模型wan2.2，Qwen-Image等14B或20B参数量的模型应用环境倒是支持的，但是部署起来及其消耗显存，对于diffusion库的加载方式 配置要求优化确实不如comfyui，不过生图模型还是够用的，因为WebUI Forge使用的也是类似的comfyui优化策略，对于comfyui复杂的节点连线式操作界面，对新手确实不太好学习 WebUI Forge更加易操作，好理解，适合入门，熟悉之后再接触comfyui更为合适

大陆国内用户
通过网盘分享的文件：更新环境库的webui Forge整合包
链接: https://pan.baidu.com/s/1FL7WVbcdvHfMtGUs-QOTVg 提取码: jwmu

海外用户
更新的Forge环境（由于体积较大无法方便上传只能如此了）
需要以下依赖：
diffusers==0.35.1

Torch 2.7.0 (CUDA 12.8)+ xFormers 0.0.30

transformers==4.53.1

huggingface-hub==0.34.4
可参考首页的requirements_versions.txt依赖文件

此整合包支持，1.5 XL flux等模型。lora加载，XL ControlNet 等模块，不支持flux ControlNet 

修复了ADetailer插件
修复了WD 1.4标签器

模型都在网盘中
<img width="1417" height="887" alt="Snipaste_2025-10-09_19-18-00" src="https://github.com/user-attachments/assets/c57b071e-b0e0-4973-a683-6da96740269d" />
使用7z压缩软件进行解压整合包

海外用户搜索模型名称下载

https://huggingface.co/yeqiu168182/flux1-dev-kontext_fp8_scaled.safetensors/tree/main

<img width="1613" height="455" alt="26" src="https://github.com/user-attachments/assets/4ef92d94-6229-4754-9f8c-4ff7fbac36c6" />


模型路径介绍

主模型目录：sd-webui-forge-aki-v4.0\models\Stable-diffusion

lora模型目录：sd-webui-forge-aki-v4.0\models\Lora

vae模型目录：sd-webui-forge-aki-v4.0\models\VAE

高清放大模型目录：sd-webui-forge-aki-v4.0\models\RealESRGAN

ControlNet模型目录：sd-webui-forge-aki-v4.0\models\ControlNet

ControlNet预处理器目录：d-webui-forge-aki-v4.0\models\ControlNetPreprocessor

插件目录：sd-webui-forge-aki-v4.0\extensions

flux模型加载方式：主模型flux1-dev-fp8.safetensors，文本编码模型t5xxl_fp8_e4m3fn.safetensors，clip模型clip_l.safetensors，vae模型flux-ae.safetensors

<img width="1600" height="95" alt="24" src="https://github.com/user-attachments/assets/c94d496a-ad36-4218-9803-8fdaa986677e" />
参数设置
<img width="910" height="348" alt="123" src="https://github.com/user-attachments/assets/2f0b6081-ba91-454c-a4ef-8136f43a0373" />

XL模型加载方式：主模型（约6GB)，vae模型 sdxl_vae.safetensors
<img width="1092" height="810" alt="25" src="https://github.com/user-attachments/assets/c52b9db3-fcc7-4c58-8434-adc0a306a6b6" />

1.5模型加载方式：主模型（约2.3GB), vae模型 vae-ft-mse-840000-ema-pruned.safetensors
