# 百度中文实体识别和实体消歧数据集.
面向中文短文本的实体识别与链指，简称ERL（Entity Recognition and Linking），是NLP领域的基础任务之一，即对于给定的一个中文短文本（如搜索Query、微博、用户对话内容、文章标题等）识别出其中的实体，并与给定知识库中的对应实体进行关联。ERL整个过程包括实体识别和实体链指两个子任务。 


传统的实体链指任务主要是针对长文档，长文档拥有在写的上下文信息能辅助实体的歧义消解并完成链指。相比之下，针对中文短文本的实体链指存在很大的挑战，主要原因如下：（1）口语化严重，导致实体歧义消解困难；（2）短文本上下文语境不丰富，须对上下文语境进行精准理解；（3）相比英文，中文由于语言自身的特点，在短文本的链指问题上更有挑战。
 

## 任务

### 输入： 输入文件包括若干行中文短文本。

### 输出： 输出文本每一行包括此中文短文本的实体识别与链指结果，需识别出文本中所有mention（包括实体与概念），每个mention包含信息如下：mention在给定知识库中的ID，mention名和在中文短文本中的位置偏移。

# kb_data 
知识库，共有40w条左右，示例如下。

```
{"alias": ["胜利"], "subject_id": "10001", "subject": "胜利", "type": ["Thing"], "data": [{"predicate": "摘要", "object": "英雄联盟胜利系列皮肤是拳头公司制作的具有纪念意义限定系列皮肤之一。拳头公司制作的具有纪念意义限定系列皮肤还包括英雄联盟冠军系列皮肤、MSI季中冠军赛征服者系列以及英雄联盟全球总决赛冠军系列皮肤。每到赛季结束时，拳头公司都会制作胜利系列皮肤作为赛季奖励来认可那些在排位赛中勇猛拼搏达到黄金段位的玩家。"}, {"predicate": "制作方", "object": "Riot Games"}, {"predicate": "外文名", "object": "Victorious"}, {"predicate": "来源", "object": "英雄联盟"}, {"predicate": "中文名", "object": "胜利"}, {"predicate": "属性", "object": "虚拟"}, {"predicate": "义项描述", "object": "游戏《英雄联盟》胜利系列限定皮肤"}]}
{"alias": ["张三的歌"], "subject_id": "10002", "subject": "张三的歌", "type": ["CreativeWork"], "data": [{"predicate": "摘要", "object": "《张三的歌》这首经典老歌，词曲作者是张子石。最早收录于李寿全的专辑《8又二分之一》当中。李寿全作为台湾民谣时代的推动人，在80年代中后期有着举足轻重的地位，而这首《张三的歌》出现在当时的背景之下，带来了无可比拟的社会效应，也为那个年代留下了无法抹去的回忆。随着时间的推移，陈翔、齐秦、吴宗宪、蔡琴、青鸟飞鱼等歌手都曾翻唱过。"}, {"predicate": "歌曲原唱", "object": "李寿全"}, {"predicate": "谱曲", "object": "张子石"}, {"predicate": "歌曲时长", "object": "3分58秒"}, {"predicate": "歌曲语言", "object": "普通话"}, {"predicate": "音乐风格", "object": "民谣"}, {"predicate": "唱片公司", "object": "飞碟唱片"}, {"predicate": "翻唱", "object": "齐秦、苏芮、南方二重唱等"}, {"predicate": "填词", "object": "张子石"}, {"predicate": "发行时间", "object": "1986-08-01"}, {"predicate": "中文名称", "object": "张三的歌"}, {"predicate": "所属专辑", "object": "8又二分之一"}, {"predicate": "义项描述", "object": "李寿全演唱歌曲"}, {"predicate": "标签", "object": "单曲"}, {"predicate": "标签", "object": "音乐作品"}]}
```

# train.json
实体识别数据集共有10w。示例如下

```
{"text_id": "1", "text": "南京南站:坐高铁在南京南站下。南京南站", "mention_data": [{"kb_id": "311223", "mention": "南京南站", "offset": "0"}, {"kb_id": "341096", "mention": "高铁", "offset": "6"}, {"kb_id": "311223", "mention": "南京南站", "offset": "9"}, {"kb_id": "311223", "mention": "南京南站", "offset": "15"}]}
{"text_id": "2", "text": "比特币吸粉无数,但央行的心另有所属|界面新闻 · jmedia", "mention_data": [{"kb_id": "278410", "mention": "比特币", "offset": "0"}, {"kb_id": "199602", "mention": "央行", "offset": "9"}, {"kb_id": "215472", "mention": "界面新闻", "offset": "18"}]}
{"text_id": "3", "text": "解读《万历十五年》", "mention_data": [{"kb_id": "131751", "mention": "万历十五年", "offset": "3"}]}
{"text_id": "4", "text": "《时间的针脚第一季》迅雷下载_完整版在线观看_美剧...", "mention_data": [{"kb_id": "NIL", "mention": "时间的针脚第一季", "offset": "1"}, {"kb_id": "57067", "mention": "迅雷", "offset": "10"}, {"kb_id": "394479", "mention": "美剧", "offset": "23"}]}
{"text_id": "5", "text": "毛泽东扮演者赵新月评《大秧歌》“大”在哪", "mention_data": [{"kb_id": "289026", "mention": "毛泽东", "offset": "0"}, {"kb_id": "NIL", "mention": "赵新月", "offset": "6"}, {"kb_id": "335162", "mention": "大秧歌", "offset": "11"}]}
```

# 数据下载方式
## 安装lfs 

参考教程 https://www.jianshu.com/p/493b81544f80

## 下载数据

```
git lfs clone https://github.com/zhusleep/ner_entity_linking
```

# 技术经验分享
4th solution
https://zhuanlan.zhihu.com/p/79389393

