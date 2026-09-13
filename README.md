# CTM Dataset

本仓库收录前端组件源码、交叉索引树人工参考标注和去组件化样本。

## 数据内容

- 来自15个开源项目的100个Vue 3单文件组件；
- 与100个Vue组件一一对应的人工参考标注；
- 根据真实父子组件关系构造的50个去组件化样本；
- 样本来源、固定提交版本、项目内路径及许可证信息。

## 目录结构

```text
ctm-dataset/
├── samples/                 # 100个原始Vue组件及对应人工参考标注
│   ├── 001/
│   │   ├── *.vue
│   │   ├── meta.json
│   │   └── annotation.json
│   └── ...
├── decomponentized/         # 50个去组件化样本
├── selected-files.json      # 原始样本来源信息
├── dataset-summary.json     # 数据集规模信息
└── THIRD_PARTY_NOTICES.md   # 第三方项目许可说明
```

## 原始Vue组件与人工参考标注

`samples/`保存编号为001—100的样本目录。每个目录包含原始Vue 3单文件组件、来源元信息`meta.json`和对应的人工参考标注`annotation.json`。

人工参考标注包括用户界面、脚本和样式结构，源码锚点，语义关系以及外部资源。`selected-files.json`记录每个原始样本的来源项目、固定提交版本、项目内路径和数据集路径。

## 去组件化样本

`decomponentized/samples/`保存编号为001—050的去组件化Vue文件。每个样本由真实父子组件关系构造，将父组件调用的一个子组件合并回父组件，并记录原父子组件、原调用位置及合并区域的源码范围。样本信息汇总于[decomponentized/manifest.json](decomponentized/manifest.json)。

## 数据来源与许可

Vue源码来自公开的第三方开源项目。使用或再分发相关源码时，应遵守对应项目的许可证，具体信息见[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
