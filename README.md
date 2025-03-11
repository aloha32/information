# Pytorch模型训练实用教程
[Pytorch模型训练实用教程](https://github.com/TingsongYu/PyTorch_Tutorial)
# 《Pytorch实用教程》第二版
[第二版](https://tingsongyu.github.io/PyTorch-Tutorial-2nd/)
# Windows 下安装 CUDA 和 Pytorch 跑深度学习
[李沐(CUDA、pytorch)](https://www.bilibili.com/video/BV18K411w7Vs/)

[larry(CUDA、pytorch、pycharm)](https://www.bilibili.com/video/BV1VZ421a7rh/)
# 深度学习缝模块
[larry](https://www.bilibili.com/video/BV1yx421C7MS/)
# 动手学深度学习 PyTorch版（强推！！！）
[李沐，沐神亲自授课，全面且专业，还配备电子书](https://space.bilibili.com/1567748478/channel/seriesdetail?sid=358497)

# 学术启蒙（[bilibili视频](https://www.bilibili.com/list/watchlater?oid=113504577197887&bvid=BV1dhUxYtEvY)）
## 如何找学术论文
1. [首推Google scholar](https://scholar.google.com/)
- 可根据时间线、关键词搜索
- follow 学术大牛
- 关键词为大领域时，看好文章（顶会、顶刊）。小领域或紧相关工作时，主要看小同行们现在都在哪个方向努力，哪种技术路线热门。

2. [从数据集找论文（papers with code）](https://paperswithcode.com/)
- 查询最新公开数据集的最新文章

3. follow 重点课题组

## 识别是否值得精读
- 会议等级查询
  
  1. [会伴 Conference Partner](https://www.myhuiban.com/?lang=zh_cn)

- 期刊等级查询

  1. 中科院/JCR分区:
      1. [官网，个人推荐扫码免费查询](https://www.fenqubiao.com/)
      2. [中科院分区和JCR分区查询](https://blog.csdn.net/xingmeng416/article/details/105921968)
      3. [LetPub:影响因子、投稿经验、分区](https://www.letpub.com.cn/index.php?page=./journalapp)
      4. [easyscholar插件-edge版](https://microsoftedge.microsoft.com/addons/detail/easyscholar/bpepicgagmdchlkjjeeiekpoafehpagm?hl=zh-CN)

## 如何精读论文
论文一般分为四个部分，introduction、related work、method 、experiment 。

introduction部分一般主要关注研究难点、技术难点、本文主要贡献。
- 研究难点：从研究背景提炼
- 技术难点：从技术路线提炼
- 本文主要贡献

experiment部分一般主要关注对比试验、消融实验、（参数实验、效率实验）、case study。

决定这篇论文写的好不好的关键：
1. 从introduction提炼出的点有没有反馈到related work以及case studey中
2. 本文的主要贡献有没有对应到method和对比试验的小章节中去。

## 如何做组会报告
- 关注文章出处、作者团队
- 关注文章的问题引入：研究难点、有没有举例
- 文章的创新点有没有对应到研究难点或技术难点中去。（决定文章是否有逻辑性）
- 模型结构，具体的方法
- 实验部分关注：
  1. 数据集的选择
  2. 基本实验结果（对比试验、消融实验）
  3. 有没有其他的实验（例如参数实验，对应说明自己的创新点的有效性等等）
  4. 有没有case study（举出实际应用效果来说明自己方法的有效性）
- 预判导师提问：
  1. 你觉得这篇文章对你有什么启发？
  2. 对你以后的工作有什么参考价值？
- 做ppt注意事项：
  1. 不要动画，具体关注内容
  2. 图文并茂，文字较少，想说的可以写到备注里。
## 如何入门
1. 站在课题组已有课题的肩膀上
2. 多读论文

## typora激活教程
[2024/12/25亲测可用，CSDN牛逼](https://blog.csdn.net/weixin_68811816/article/details/142185341)

## 如何通过api使用AI大模型
[datawhale(前半小时即可)](https://www.bilibili.com/video/BV1oek1YvE74/)

## 如何选刊
### [如何选到接受率高-速度快-适合自己的期刊](https://www.bilibili.com/video/BV1Xt421G7S8/)
- [PubMed](https://pubmed.ncbi.nlm.nih.gov/):收录了来自 MEDLINE、生命科学期刊和在线书籍的超过 3700 万篇生物医学文献引用。引文可能包括来自 PubMed Central 和出版商网站的全文内容的链接。
- **[jane](https://jane.biosemantics.org/)**:输入论文标题或摘要即可自动匹配

### [文章写完了怎么找合适的期刊？](https://www.bilibili.com/video/BV1TN4y1f73p/)
- [LetPub](https://www.letpub.com.cn/index.php?page=journalapp):输入期刊名或者ISSN可以详细查看影响因子、自引率等。**自引率增长或过高可能会成为预警。**是否OA开发此项不准，应去官网自行查看。年文章数过少不宜投稿。面文章数过高同时自引率高会容易预警。
- [爱科学]([https://www.iikx.com/sci/](https://www.iikx.com/sci/list.html?classid=18&orderby=IF2024&ph=1&jcr21=%E8%AE%A1%E7%AE%97%E6%9C%BA%EF%BC%9A%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD))：必须输入期刊名。好像只有JCR分区。
- [梅斯](https://www.medsci.cn/sci/index.do?big_class_id=6&bigclass=%E5%B7%A5%E7%A8%8B%E6%8A%80%E6%9C%AF&page=1&type=sci&small_class_id=445&smallclass=%E8%AE%A1%E7%AE%97%E6%9C%BA%EF%BC%9A%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD)：投稿命中率及审稿周期需要会员才能看。出版周期也可以参考，越频繁越好。流氓网站，不登记信息不给用。
- [根哥学术](https://www.geenmedical.com/login)：需要账号。似乎很久未更新。优点：提供国人发稿量
- [爱思维尔](https://journalfinder.elsevier.com/)：同Jane，可以通过标题，摘要，关键字进行推荐，需要进行自我甄别，有可能有无关期刊混入。这里的推荐期刊大部分都是既可以OA也可以非OA。Jane比爱思维尔好一点。
- [journal guide](https://www.journalguide.com/)：输入标题，摘要。影响因子、是否开源不准。
- [ijournal](https://ijournal.topeditsci.com/home)
- [维普期刊查询系统](https://datauthor.com/)：中英文均可，输入标题，摘要，关键词。需要登陆。提供的信息和letpub、爱科学差不多。
- [科研兔](https://researchrabbitapp.com/home)：可以通过查看谁引用了目标文章，总而找到类似的期刊。


