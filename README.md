# 陈子豪的简历  

### 陈子豪 · 算法工程师    

6年工作经验&#124;本科&#124;28岁&#124;男&#124;[cs1994726@outlook.com](mailto:cs1994726@outlook.com)&#124;+86 18501995729   

### 工作经历

2021.08-至今  
**北京欧珀通信有限公司（oppo）**  
职位：高级数据挖掘工程师  
* 使用各种深度视觉相关技术提升oppo内容理解平台的效果  
* 基于内容理解平台，对oppo内部的信息流建设提供帮助等

2020.09-2021.08  
**北京希瑞亚斯科技有限公司（MOKA招聘）**  
职位：算法工程师  
* 使用各种OCR的检测和识别技术提升图片简历内容解析的准确率和速度
* 为通用简历内容解析提供视觉语义上的支持，比如简历内嵌图片语义理解，简历块视觉编码提取等

2017.07-2020.09  
**北京墨迹风云科技股份有限公司（墨迹天气）**  
职位：算法工程师  
- 使用各种算法提升短时降水预报和空气质量预报的准确率
- 为客户端提供各种有趣实用的算法产品，比如观云识天、灾害识别、过敏预报等
- 参与到一部分气象数据分析工作和气象业务化工作

### 教育经历

2013-2017  
**郑州大学**  
计算机科学与技术 / 本科  

### 项目经历  
**OPPO内容挖掘** 算法负责

- 计算机视觉 人脸检测与识别 视频封面生成 图像质量评估等
- nlp 搜索意图理解 大规模搜索预训练 迁移学习等
- llm 标准化prompt探索 生成式在业务场景中的应用探索等

**图片简历OCR** 主要负责  
从moka开始提供招聘服务开始，对于图片简历，系统内部只能使用第三方的OCR服务来进行处理。考虑到通用OCR服务和我们内部的数据分布一致性很差，所以在19年初，moka的AI部门尝试开始搭建自己的图片简历解析服务，整个服务的算法内核分为两部分，首先对整页简历内容基于 目标检测 技术提取出候选区域，再使用 卷积循环神经网络 对候选区域的文字内容做识别，最终提取出整页图片上的有效信息。

- 基于深度学习的文字区域检测算法，主要使用了CTPN、[DBNET](https://github.com/chencodeX/DB)等网络结构。
- 基于CRNN的图片文字识别算法，主要使用了resnet、mobilenet、bidirectional LSTM，CTC Loss等结构。
- 基于libtorch和dynamic RNN等技术，对图片简历解析模型进行加速。

**解析效果** 目前对简历文字块的识别准确率F值从72.9%提升到91.1%，单帧简历识别速度从1000毫秒降低到350。

------

**简历视觉信息提取** 主要负责   
简历解析过程中，对于图文混排简历，其图片数据可以帮助我们分享整体的简历组织结构。所以我们设计了两种方法来帮助简历解析提供更多的视觉信息。

- 对简历内嵌图片进行分类和识别，主要使用了resnet、RoIAlign等结构。
- 对简历解析已经提取出的区域，提取其视觉信息的编码表示，主要使用了自监督视觉特征学习的技术。
- 基于torchvision的cuda接口，对服务进行加速。

------

**短时预报** 主要负责  
**短时预报** 从 16 年到 20 年已经被认为是最有关 meteo , AI 的研究与应用方向。这个方向使用了 气象雷达 进行降水因子观测，对观测到的雷达回波使用基于深度学习的 图像语义分割 技术进行雷达回波去噪，对去噪后的雷达回波基于 循环神经网络 技术进行外推（预报）。呈现给用户一个分钟级，百米级的未来两小时降水预报产品。

- 基于全卷积神经网络的雷达回波数据去噪算法，主要使用了FCN、deeplab、Unet等网络。
- 基于RNN的雷达时序数据预测算法，主要使用了ConvLSTM、[ConvGRU](https://github.com/chencodeX/RNN_Pytorch)等网络结构。
- 基于GPU的快速降水推送算法，主要使用了pytorch、kafka等技术框架。

**预报效果** 目前对雷达噪声的识别准确率保持在95%以上，外推 (预报) 一小时准确率TS评分均值为51%。

------

**观云识天及灾害天气识别** 主要负责   
一种基于UGC数据的再分析工作。它数据来源是墨迹天气的用户实景社区。它是国内最丰富的气象要素强相关社会观测资料库。使用了 图像识别和目标检测 的技术，检测实景中可能包含的天气灾害或者天气过程。

- 观云识天产品可以检测出用户上传的照片中云的位置和云的类别，为用户提供该云类型对应下雨的可能性。
- 灾害天气识别检测用户实时上传的图像中是否有灾害天气的发生。
- 任务本身样本极不均衡，使用了ResNet、[BCNN](https://github.com/chencodeX/Bilinear_CNN_dog_classifi)、[triplet loss](https://github.com/chencodeX/triplet-loss-pytorch)、多级分类器等技术。

**产品效果** 目前支持四种天气过程和四种灾害类型，平均识别精确率为 91.5% ; 支持13种类型的云图细粒度分类，准确率为85%。

------

**空气质量预报项目** 参与  
基于全球数值模式预报数据和空气质量实况数据，为用户提供未来5天的逐小时空气质量预报。

- 调研空气污染扩散条件，构建算法特征，基于SVR构建回归模型预报空气质量数据。
- 针对站点数据缺失问题，基于GBDT构建回归模型，补充站点数据。

------

**用户反馈** 参与  
一种重要的 UGC 内容，在方方面面参与到目前气象数据加工和预报环节当中。最初它基于一定的时空范围内的用户反馈数据，通过 贝叶斯推断 的方式为短时提供实时有效高质量的反馈数据。在19年，添加了用户置信度的分级系统，对不同置信度用户按照不同策略进行采纳。它使得用户反馈的采纳率和可靠性都大幅提高。

### 自我描述

能够使用python/c++解决各种业务化问题，能够使用kafka、[flask](https://github.com/chencodeX/XianYun)、rpc等技术构建高效稳定的线上服务。  
熟悉linux系统的使用，熟悉pytorch,libtorch深度学习框架，有caffe和tensorflow的使用经验。  
了解分类回归等机器学习基本理论，熟悉数据清洗特征工程，有sklearn使用经验。  
了解常用的数字图像处理技术，熟练使用opencv、numpy、pandas等数据处理工具。  
熟悉一些常用的CNN、RNN算法模型，了解图像的识别、检测、语义分割等相关算法。  
喜欢有挑战的编程工作，对新技术抱有好奇心，动手能力强。  
优秀的策略游戏玩家，反曲弓入门爱好者。  
GitHub: <https://github.com/chencodeX> 