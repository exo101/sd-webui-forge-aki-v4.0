# Stable Diffusion WebUI Forge

Stable Diffusion WebUI Forge is a platform on top of [Stable Diffusion WebUI](https://github.com/AUTOMATIC1111/stable-diffusion-webui) (based on [Gradio](https://www.gradio.app/) <a href='https://github.com/gradio-app/gradio'><img src='https://img.shields.io/github/stars/gradio-app/gradio'></a>) to make development easier, optimize resource management, speed up inference, and study experimental features.

The name "Forge" is inspired from "Minecraft Forge". This project is aimed at becoming SD WebUI's Forge.

Forge is currently based on SD-WebUI 1.10.1 at [this commit](https://github.com/AUTOMATIC1111/stable-diffusion-webui/commit/82a973c04367123ae98bd9abdf80d9eda9b910e2). (Because original SD-WebUI is almost static now, Forge will sync with original WebUI every 90 days, or when important fixes.)

News are moved to this link: [Click here to see the News section](https://github.com/lllyasviel/stable-diffusion-webui-forge/blob/main/NEWS.md)

# Quick List

[Gradio 4 UI Must Read (TLDR: You need to use RIGHT MOUSE BUTTON to move canvas!)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/853)

[Flux Tutorial (BitsandBytes Models, NF4, "GPU Weight", "Offload Location", "Offload Method", etc)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/981)

[Flux Tutorial 2 (Seperated Full Models, GGUF, Technically Correct Comparison between GGUF and NF4, etc)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1050)

[Forge Extension List and Extension Replacement List (Temporary)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1754)

[How to make LoRAs more precise on low-bit models; How to Skip" Patching LoRAs"; How to only load LoRA one time rather than each generation; How to report LoRAs that do not work](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1038)

[Report Flux Performance Problems (TLDR: DO NOT set "GPU Weight" too high! Lower "GPU Weight" solves 99% problems!)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1181)

[How to solve "Connection errored out" / "Press anykey to continue ..." / etc](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1474)

[(Save Flux BitsandBytes UNet/Checkpoint)](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1224#discussioncomment-10384104)

[LayerDiffuse Transparent Image Editing](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/854)

[Tell us what is missing in ControlNet Integrated](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/932)

[(Policy) Soft Advertisement Removal Policy](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/1286)

(Flux BNB NF4 / GGUF Q8_0/Q5_0/Q5_1/Q4_0/Q4_1 are all natively supported with GPU weight slider and Quene/Async Swap toggle and swap location toggle. All Flux BNB NF4 / GGUF Q8_0/Q5_0/Q4_0 have LoRA support.)

# Installing Forge

**Just use this one-click installation package (with git and python included).**

[>>> Click Here to Download One-Click Package (CUDA 12.1 + Pytorch 2.3.1) <<<](https://github.com/lllyasviel/stable-diffusion-webui-forge/releases/download/latest/webui_forge_cu121_torch231.7z)

Some other CUDA/Torch Versions:

[Forge with CUDA 12.1 + Pytorch 2.3.1](https://github.com/lllyasviel/stable-diffusion-webui-forge/releases/download/latest/webui_forge_cu121_torch231.7z) <- **Recommended**

[Forge with CUDA 12.4 + Pytorch 2.4](https://github.com/lllyasviel/stable-diffusion-webui-forge/releases/download/latest/webui_forge_cu124_torch24.7z) <- **Fastest**, but MSVC may be broken, xformers may not work

[Forge with CUDA 12.1 + Pytorch 2.1](https://github.com/lllyasviel/stable-diffusion-webui-forge/releases/download/latest/webui_forge_cu121_torch21.7z) <- the previously used old environments

After you download, you uncompress, use `update.bat` to update, and use `run.bat` to run.

Note that running `update.bat` is important, otherwise you may be using a previous version with potential bugs unfixed.

![image](https://github.com/lllyasviel/stable-diffusion-webui-forge/assets/19834515/c49bd60d-82bd-4086-9859-88d472582b94)

### Advanced Install

If you are proficient in Git and you want to install Forge as another branch of SD-WebUI, please see [here](https://github.com/continue-revolution/sd-webui-animatediff/blob/forge/master/docs/how-to-use.md#you-have-a1111-and-you-know-git). In this way, you can reuse all SD checkpoints and all extensions you installed previously in your OG SD-WebUI, but you should know what you are doing.

If you know what you are doing, you can also install Forge using same method as SD-WebUI. (Install Git, Python, Git Clone the forge repo `https://github.com/lllyasviel/stable-diffusion-webui-forge.git` and then run webui-user.bat).

### Previous Versions

You can download previous versions [here](https://github.com/lllyasviel/stable-diffusion-webui-forge/discussions/849).

# Forge Status

Based on manual test one-by-one:

| Component                                           | Status                                      | Last Test    |
|-----------------------------------------------------|---------------------------------------------|--------------|
| Basic Diffusion                                     | Normal                                      | 2024 Aug 26  |
| GPU Memory Management System                        | Normal                                      | 2024 Aug 26  |
| LoRAs                                               | Normal                                      | 2024 Aug 26  |
| All Preprocessors                                   | Normal                                      | 2024 Aug 26  |
| All ControlNets                                     | Normal                                      | 2024 Aug 26  |
| All IP-Adapters                                     | Normal                                      | 2024 Aug 26  |
| All Instant-IDs                                     | Normal                                      | 2024 July 27 |
| All Reference-only Methods                          | Normal                                      | 2024 July 27 |
| All Integrated Extensions                           | Normal                                      | 2024 July 27 |
| Popular Extensions (Adetailer, etc)                 | Normal                                      | 2024 July 27 |
| Gradio 4 UIs                                        | Normal                                      | 2024 July 27 |
| Gradio 4 Forge Canvas                               | Normal                                      | 2024 Aug 26  |
| LoRA/Checkpoint Selection UI for Gradio 4           | Normal                                      | 2024 July 27 |
| Photopea/OpenposeEditor/etc for ControlNet          | Normal                                      | 2024 July 27 |
| Wacom 128 level touch pressure support for Canvas   | Normal                                      | 2024 July 15 |
| Microsoft Surface touch pressure support for Canvas | Broken, pending fix                         | 2024 July 29 |
| ControlNets (Union)                                 | Not implemented yet, pending implementation | 2024 Aug 26  |
| ControlNets (Flux)                                  | Not implemented yet, pending implementation | 2024 Aug 26  |
| API endpoints (txt2img, img2img, etc)               | Normal, but pending improved Flux support   | 2024 Aug 29  |
| OFT LoRAs                                           | Broken, pending fix                         | 2024 Sep 9   |

Feel free to open issue if anything is broken and I will take a look every several days. If I do not update this "Forge Status" then it means I cannot reproduce any problem. In that case, fresh re-install should help most.

# UnetPatcher

Below are self-supported **single file** of all codes to implement FreeU V2.

See also `extension-builtin/sd_forge_freeu/scripts/forge_freeu.py`:

```python
import torch
import gradio as gr

from modules import scripts


def Fourier_filter(x, threshold, scale):
    # FFT
    x_freq = torch.fft.fftn(x.float(), dim=(-2, -1))
    x_freq = torch.fft.fftshift(x_freq, dim=(-2, -1))

    B, C, H, W = x_freq.shape
    mask = torch.ones((B, C, H, W), device=x.device)

    crow, ccol = H // 2, W // 2
    mask[..., crow - threshold:crow + threshold, ccol - threshold:ccol + threshold] = scale
    x_freq = x_freq * mask

    # IFFT
    x_freq = torch.fft.ifftshift(x_freq, dim=(-2, -1))
    x_filtered = torch.fft.ifftn(x_freq, dim=(-2, -1)).real

    return x_filtered.to(x.dtype)


def patch_freeu_v2(unet_patcher, b1, b2, s1, s2):
    model_channels = unet_patcher.model.diffusion_model.config["model_channels"]
    scale_dict = {model_channels * 4: (b1, s1), model_channels * 2: (b2, s2)}
    on_cpu_devices = {}

    def output_block_patch(h, hsp, transformer_options):
        scale = scale_dict.get(h.shape[1], None)
        if scale is not None:
            hidden_mean = h.mean(1).unsqueeze(1)
            B = hidden_mean.shape[0]
            hidden_max, _ = torch.max(hidden_mean.view(B, -1), dim=-1, keepdim=True)
            hidden_min, _ = torch.min(hidden_mean.view(B, -1), dim=-1, keepdim=True)
            hidden_mean = (hidden_mean - hidden_min.unsqueeze(2).unsqueeze(3)) / (hidden_max - hidden_min).unsqueeze(2).unsqueeze(3)

            h[:, :h.shape[1] // 2] = h[:, :h.shape[1] // 2] * ((scale[0] - 1) * hidden_mean + 1)

            if hsp.device not in on_cpu_devices:
                try:
                    hsp = Fourier_filter(hsp, threshold=1, scale=scale[1])
                except:
                    print("Device", hsp.device, "does not support the torch.fft.")
                    on_cpu_devices[hsp.device] = True
                    hsp = Fourier_filter(hsp.cpu(), threshold=1, scale=scale[1]).to(hsp.device)
            else:
                hsp = Fourier_filter(hsp.cpu(), threshold=1, scale=scale[1]).to(hsp.device)

        return h, hsp

    m = unet_patcher.clone()
    m.set_model_output_block_patch(output_block_patch)
    return m


class FreeUForForge(scripts.Script):
    sorting_priority = 12  # It will be the 12th item on UI.

    def title(self):
        return "FreeU Integrated"

    def show(self, is_img2img):
        # make this extension visible in both txt2img and img2img tab.
        return scripts.AlwaysVisible

    def ui(self, *args, **kwargs):
        with gr.Accordion(open=False, label=self.title()):
            freeu_enabled = gr.Checkbox(label='Enabled', value=False)
            freeu_b1 = gr.Slider(label='B1', minimum=0, maximum=2, step=0.01, value=1.01)
            freeu_b2 = gr.Slider(label='B2', minimum=0, maximum=2, step=0.01, value=1.02)
            freeu_s1 = gr.Slider(label='S1', minimum=0, maximum=4, step=0.01, value=0.99)
            freeu_s2 = gr.Slider(label='S2', minimum=0, maximum=4, step=0.01, value=0.95)

        return freeu_enabled, freeu_b1, freeu_b2, freeu_s1, freeu_s2

    def process_before_every_sampling(self, p, *script_args, **kwargs):
        # This will be called before every sampling.
        # If you use highres fix, this will be called twice.

        freeu_enabled, freeu_b1, freeu_b2, freeu_s1, freeu_s2 = script_args

        if not freeu_enabled:
            return

        unet = p.sd_model.forge_objects.unet

        unet = patch_freeu_v2(unet, freeu_b1, freeu_b2, freeu_s1, freeu_s2)

        p.sd_model.forge_objects.unet = unet

        # Below codes will add some logs to the texts below the image outputs on UI.
        # The extra_generation_params does not influence results.
        p.extra_generation_params.update(dict(
            freeu_enabled=freeu_enabled,
            freeu_b1=freeu_b1,
            freeu_b2=freeu_b2,
            freeu_s1=freeu_s1,
            freeu_s2=freeu_s2,
        ))

        return
```

See also [Forge's Unet Implementation](https://github.com/lllyasviel/stable-diffusion-webui-forge/blob/main/backend/nn/unet.py).

# Under Construction

WebUI Forge is now under some constructions, and docs / UI / functionality may change with updates.

```
# Stable Diffusion WebUI Forge 整合包使用说明

## 简介

旧整合包已不适用日益更新的AI应用与50系显卡，为此我们更新了新整合包环境，补充落后的webui生态。

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
```

可参考首页的requirements_versions.txt依赖文件

此整合包支持：
- 1.5模型
- XL模型 
- FLUX模型
- LoRA加载
- XL ControlNet等模块
- 不支持FLUX ControlNet

### 模型下载
海外用户可搜索模型名称下载:  
https://huggingface.co/yeqiu168182/flux1-dev-kontext_fp8_scaled.safetensors/tree/main

使用7z压缩软件进行解压整合包。

## 界面介绍

### GPU 显存管理
GPU Weights (MB)滑动条的数值就是显存的容量：
- 往左滑动是模型权重加载
- 往右是模型计算空间

正常情况下：
- 往右滑动过半，留出20%-40%的计算空间
- 如果模型权重预留的空间不足，模型会加载失败
- 如果模型计算空间不足，会生成时间变慢，程序崩溃爆显存

## 模型路径介绍

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

参数设置参考:
- 采样器: Euler a
- 步数: 20-30步
- CFG: 1-2

### XL模型加载方式
- 主模型（约6GB)
- VAE模型: `sdxl_vae.safetensors`

### 1.5模型加载方式
- 主模型（约2.3GB)
- VAE模型: `vae-ft-mse-840000-ema-pruned.safetensors`

