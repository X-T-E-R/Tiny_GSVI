---
app_file: app.py
colorFrom: indigo
colorTo: blue
emoji: "\U0001F4A1"
license: Apache License 2.0
pinned: false
sdk: gradio
sdk_version: 4.19.2
title: GSVI Tiny 
---

## 概述

这是一个便捷的项目用于快速将您的GPT-soVITS模型上传到 modelscope 或者 Hugging Face 或任意支持gradio的空间 ，让所有人可以免费体验。



## 优点

1. 推理速度较快（核心代码使用fast_inference_分支）
2. 引入缓存机制，切换参考音频需要时间约为0
3. 模型以文件夹形式存在，方便分享
4. 可以自行指定角色和情绪



## 如何使用

### 使用一键上传整合包

到地址下载整合包（地址待修改），按照其提示运行bat即可

### 手动上传到各种空间

1. 将模型放到trained文件夹下
2. 将预训练模型放到pretrained_models文件夹下
3. 删去.gitignore的`trained` / `pretrained_models`这两行
4. 书写`Information.md`
5. 修改`Readme.md` （本文件）: 一般推荐只需要修改`title`和`emoji`
6. 然后通过git工具上传到各种空间

## 参数与要求

### 空间要求

#### Hugging Face

能使用，无特别要求

#### 创空间（modelscope）

要求选择`ubuntu22.04-py310-torch2.1.0-tf2.14.0-modelscope1.10.0`这一个镜像版本

### 调整参数

在`config.json` ，您可以重点关注：

    "locale": "zh_CN",
    "max_text_length": 70,
    "save_prompt_cache": "true",

- locale代表您选择的语言，当您想使用中文时可以切换成zh_CN
- max_text_length仅仅限制输入框的最大字数（英文按词算，中日文按字算），因为免费的空间实在是太卡了
- save_prompt_cache代表是否保存参考音频的向量到磁盘，会显著加速，建议开启

## 模型需求

对于模型，整体来说，您需要把从一个到一连串的文件夹放置在`trained`文件夹内

#### 1. 文件夹名称

文件夹名称就是角色名称

#### 2. 文件夹内容

里面应该至少有3个文件，以`pth`/`ckpt`/`wav`后缀名结尾

wav文件请命名成它包含的提示文本，时长在3-10s内。

#### 3. json文件

您可以通过模型管理界面或文本编辑器来编辑`infer_config.json`，里面的内容是参考音频配置。

更多参考音频与情绪配置相关请参见[参考音频说明 (yuque.com)](https://www.yuque.com/xter/zibxlp/mkglfgl8kaal8aor)



## 有关代码与引用

1. 内部的 `Adapters/gsv_fast` 文件夹、`i18n`来自[GPT-soVITS](https://github.com/RVC-Boss/GPT-SoVITS)项目的`fast_inference_`分支

2. app.py 主要来自原项目的一个fork [GSVI](https://github.com/X-T-E-R/GPT-SoVITS-Inference)

3. 架构形式来自：[Uni-TTS-API](https://github.com/X-T-E-R/Uni-TTS-API) ，把GPT-soVITS作为一个适配器，可以更通用的使用各种语音项目


## 请我喝奶茶

打个广告，觉得我写的内容好的可以在爱发电请我一杯奶茶！ https://afdian.net/a/xter123

## Credits

This repo is mainly based on the `fast_inference_` branch of [GPT-soVITS](https://github.com/RVC-Boss/GPT-SoVITS) project

Special thanks to the following projects and contributors:

### Theoretical
- [ar-vits](https://github.com/innnky/ar-vits)
- [SoundStorm](https://github.com/yangdongchao/SoundStorm/tree/master/soundstorm/s1/AR)
- [vits](https://github.com/jaywalnut310/vits)
- [TransferTTS](https://github.com/hcy71o/TransferTTS/blob/master/models.py#L556)
- [contentvec](https://github.com/auspicious3000/contentvec/)
- [hifi-gan](https://github.com/jik876/hifi-gan)
- [fish-speech](https://github.com/fishaudio/fish-speech/blob/main/tools/llama/generate.py#L41)
### Pretrained Models
- [Chinese Speech Pretrain](https://github.com/TencentGameMate/chinese_speech_pretrain)
- [Chinese-Roberta-WWM-Ext-Large](https://huggingface.co/hfl/chinese-roberta-wwm-ext-large)
### Text Frontend for Inference
- [paddlespeech zh_normalization](https://github.com/PaddlePaddle/PaddleSpeech/tree/develop/paddlespeech/t2s/frontend/zh_normalization)
- [LangSegment](https://github.com/juntaosun/LangSegment)
### WebUI Tools
- [ultimatevocalremovergui](https://github.com/Anjok07/ultimatevocalremovergui)
- [audio-slicer](https://github.com/openvpi/audio-slicer)
- [SubFix](https://github.com/cronrpc/SubFix)
- [FFmpeg](https://github.com/FFmpeg/FFmpeg)
- [gradio](https://github.com/gradio-app/gradio)
- [faster-whisper](https://github.com/SYSTRAN/faster-whisper)
- [FunASR](https://github.com/alibaba-damo-academy/FunASR)
  
## Thanks to all contributors for their efforts

