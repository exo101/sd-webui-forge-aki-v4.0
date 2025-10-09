# sd-webui-forge-aki-v4.0
为更新只支持50系显卡与众多ai应用的整合包

此整合包支持，1.5 XL flux等模型。lora加载，XL ControlNet 等模块，不支持flux ControlNet 

修复了ADetailer插件
修复了WD 1.4标签器

模型路径介绍

主模型目录：sd-webui-forge-aki-v4.0\models\Stable-diffusion
lora模型目录：sd-webui-forge-aki-v4.0\models\Lora
vae模型目录：sd-webui-forge-aki-v4.0\models\VAE
高清放大模型目录：sd-webui-forge-aki-v4.0\models\RealESRGAN
ControlNet模型目录：sd-webui-forge-aki-v4.0\models\ControlNet
ControlNet预处理器目录：d-webui-forge-aki-v4.0\models\ControlNetPreprocessor
插件目录：sd-webui-forge-aki-v4.0\extensions

flux模型加载方式：主模型flux1-dev-fp8.safetensors，文本编码模型t5xxl_fp8_e4m3fn.safetensors，clip模型clip_l.safetensors，vae模型flux-ae.safetensors，
<img width="1600" height="95" alt="24" src="https://github.com/user-attachments/assets/c94d496a-ad36-4218-9803-8fdaa986677e" />
参数设置
<img width="910" height="348" alt="123" src="https://github.com/user-attachments/assets/2f0b6081-ba91-454c-a4ef-8136f43a0373" />

XL模型加载方式：主模型（约6GB)，vae模型 sdxl_vae.safetensors
<img width="1092" height="810" alt="25" src="https://github.com/user-attachments/assets/c52b9db3-fcc7-4c58-8434-adc0a306a6b6" />

1.5模型加载方式：主模型（约2.3GB), vae模型 vae-ft-mse-840000-ema-pruned.safetensors
