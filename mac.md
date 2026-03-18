Qwen-tts


### 参考：
> https://www.bilibili.com/video/BV1wA6gBYELq/
> https://lingshunlab.com/ai/qwen3-tts-on-mac-mini-m4-the-ultimate-installation-optimization-guide

```shell
brew install portaudio ffmpeg sox

# Create and activate the environment
conda create -n qwen3-tts python=3.12 -y
conda activate qwen3-tts

# Install the core inference library
pip install -U qwen-tts

# Clone the repository for local modifications
git clone https://github.com/QwenLM/Qwen3-TTS.git .
# cd Qwen3-TTS
pip install -e .
```


```shell
(qwen3-tts) peakchao@zhangzhichaodeMac-mini Qwen3-TTS % python
Python 3.12.12 | packaged by Anaconda, Inc. | (main, Oct 21 2025, 20:07:49) [Clang 20.1.8 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> print(torch.backends.mps.is_available())
True
>>> print(torch.backends.mps.is_built())
True
>>> exit()
```

#demo

```shell
# 克隆音色
python -m qwen_tts.cli.demo Qwen/Qwen3-TTS-12Hz-1.7B-Base --device mps --dtype bfloat16 --no-flash-attn --port 9000 --ip 127.0.0.1
# 可音色参数（如音高、语速、情感、性别）生成的定制化语音
python -m qwen_tts.cli.demo Qwen/Qwen3-TTS-12Hz-1.7B-VoiceDesign --device mps --dtype bfloat16 --no-flash-attn --port 9000 --ip 127.0.0.1
# 模型内置的通用音色 可控制语气
python -m qwen_tts.cli.demo Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice --device mps --dtype bfloat16 --no-flash-attn --port 9000 --ip 127.0.0.1
```
