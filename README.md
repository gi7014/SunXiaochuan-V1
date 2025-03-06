---
license: mit
library_name: transformers
---
# SunXiaochuan-V1-3B
<!-- markdownlint-disable first-line-h1 -->
<!-- markdownlint-disable html -->
<!-- markdownlint-disable no-duplicate-header -->

<div align="center">
  <img src="https://github.com/deepseek-ai/DeepSeek-V2/blob/main/figures/logo.svg?raw=true" width="60%" alt="SunXiaochuan-V1-3B" />
</div>
<hr>
<div align="center" style="line-height: 1;">
  <a href="https://huggingface.co/Hanversion" target="_blank" style="margin: 2px;">
    <img alt="Hugging Face" src="https://img.shields.io/badge/HuggingFace-SunXiaochuan-yellow?logo=huggingface" style="display: inline-block; vertical-align: middle;"/>
  </a>
  <a href="https://github.com/gi7014" target="_blank" style="margin: 2px;">
    <img alt="Github" src="https://img.shields.io/badge/Github-SunXiaochuan-white?logo=github" style="display: inline-block; vertical-align: middle;"/>
  </a>
</div>

<div align="center" style="line-height: 1;">
  <a href="https://github.com/deepseek-ai/DeepSeek-R1/blob/main/LICENSE" style="margin: 2px;">
    <img alt="License" src="https://img.shields.io/badge/License-Apache2-f5de53?&color=f5de53" style="display: inline-block; vertical-align: middle;"/>
  </a>
</div>



## 1. 介绍

本模型基于Qwen2.5-3B-Instruct并使用Lora进行模型微调获得。数据集的使用来自 [孙笑川吧](https://tieba.baidu.com/f?kw=%E5%AD%99%E7%AC%91%E5%B7%9D) 某些帖子中的回复及楼中楼回复，由于未对数据进行全面清理，故数据集质量与数量并不高。数据集可以从我的 [HuggingFace数据集]([hf-mirror.com/datasets/Hanversion/Tieba-SomeInteresting](https://hf-mirror.com/datasets/Hanversion/Tieba-SomeInteresting)) 中获得。除孙笑川吧数据外，还包括 [弱智吧]() 、 [中国人口吧]() 以及 [航空母舰吧]() 的部分数据，数据来源日期为 2025-03-05。数据格式如下：

* question：帖子标题
* answer：帖子最热门的回复
* think：DeepSeek-V3所生成的思考链

本模型仅供学习使用，不保证模型真实性及有效性。


## 2. 训练介绍

本模型的训练使用了 [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) 作为微调工具，训练集样本大小为3000条数据，并且修改梯度累计为2，Lora秩为16，Lora+为16等，设备使用单卡4090训练1小时得到。具体训练Loss曲线如下：

![Loss训练曲线](https://github.com/gi7014/SunXiaochuan-V1/blob/main/training_loss.png)

同时，模型训练完成后，用其他500条数据进行数据预测和模型评估，得到如下结果：

```json
{
    "predict_bleu-4": 2.2241416,
    "predict_model_preparation_time": 0.0043,
    "predict_rouge-1": 13.033509999999998,
    "predict_rouge-2": 1.3886417999999998,
    "predict_rouge-l": 10.5493132,
    "predict_runtime": 610.2644,
    "predict_samples_per_second": 0.819,
    "predict_steps_per_second": 0.41
}
```

## 3. 模型介绍

### SunXiaochuan-V1


| **模型名称** | **#总参数** | **#微调参数** | **上下文长度** | **下载** |
| :------------: | :------------: | :------------: | :------------: | :------------: |
| SunXiaochuan-V1-3B | 3B | 0.5B | 128K   | [🤗 HuggingFace](https://huggingface.co/Hanversion/SunXiaochuan-V1-3B) |

使用 Qwen2.5 进行训练，无思考推理过程

### SunXiaochuan-R

|          **模型名称**          | **#总参数** | **#微调参数** | **上下文长度** |                           **下载**                           |
| :----------------------------: | :---------: | :-----------: | :------------: | :----------------------------------------------------------: |
| DeepShit-R1-1.5B-Sunba-Distill |    1.5B     |      1B       |      128K      | [🤗 HuggingFace](https://huggingface.co/Hanversion/DeepShit-R1-1.5B-Sunba-Distill) |
|   MAGA-T1-Tieba-1.5B-Distill   |    1.5B     |      2B       |      128K      | [🤗 HuggingFace](https://huggingface.co/Hanversion/MAGA-T1-Tieba-1.5B-Distill) |

基于 DeepSeek-R1 进行训练，加入思考推理过程

## 5. 联系

欢迎与我进行讨论，联系方式如下：

* Github：[Hanversion](https://github.com/gi7014)
* Email：hanversion@outlook.com
