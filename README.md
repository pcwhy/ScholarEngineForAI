AI写Paper的四阶段法，每一个阶段结束前必须要AI写memo，写清楚做了啥，lesson Learned，为下一阶段打好基础。新阶段必须重新开一个对话，原因是目前的AI对于高质量学术研究-写作流程来说上下文窗口还是不够长，一旦信息过载就会触发数据有损压缩，表现就是AI变得傻到不行，也不积极干活。以下四阶段法在OpenAI Codex下跑通：

Phase I: 
I.1：喂好的种子文献，用arxiv-to-prompt或者arxiv2md，让AI知道你的Context，最重要的，说话方式，不然出来的结果就是课程大作业。这一步需要平时你有收藏好文献的习惯。

I.2：我想做的东西有没有学术价值，是不是大路货，初步确定哪块别人做的少；也可以从时效性（能蹭到啥热点不？）、故事性（跨领域降维打击解决痛点、新奇的发现、新的套路，反正就是网红套路），预期回答的问题有没价值（稀缺性或者是吸睛程度）、跨领域性、理论深度，几个方面让AI给你找并综合对比。要弄出一个计划，形成文档。要形成一个支撑足够的论文计划，一般来说IEEE 会议参考文献20个起，期刊可以到35个。这里要提醒一点，注意区分工程师跟科学家的思维差异：工程师：这个系统这么做就能work了（可以发EI论文，有概率能出SCI）；科学家：为啥别的系统没work，是不是有隐藏的pattern大家没来得及研究，或者数学模型呢，能不呢换个全新的角度审视这个问题，会不会就有更好的解决方案了，数学模型能不能揭示隐藏在表面现象之下的pattern呢？好像这个系统还不是太好，看看哪些情形它出问题，看看它底层的数学/数值模型/信号流啥的怎么说的，能不能换个角度完善或者试试直接从底层重建一个完全不一样的系统呢（专利或者好的SCI就要走到科学家的思维上了）。。。这个阶段必须要AI根据事实一步一步求证推导，不懂跟不确定就直接提出来。

Phase II：
II.1：根据Phase I的计划开始写代码实现，对结果进行画图处理，一定要指定是IEEE Style，生成论文初稿。这一阶段尽可能多的让AI去探索各种组合、技巧，得到充足的数据，这一点也要你平时多看文献跟新闻，知道痛点在哪。重要提示，AI写的程序必须要输出progress updates，不然会超时，然后AI给你改简单，你要让它尽量生成colab notebook，每个cell坚决不准超过300行代码，要用.py文件也要规定每个.py文件不许超过400行代码，并且一切都得严格用匈牙利命名法，不然你就会无法维护。图画的好不好体现了你平时有没收藏好文章，特别是nature跟science的。特别的如果要re-run一定要让AI记得update论文里的图！！！尽量让AI用Bookstab画表格，同时，还要让AI知道把实验结果跟Latex渲染放在两个不同stage里，不然每次更新论文格式要重新跑仿真会很崩溃。也可以一开始就把整个过程分成原始数据层（AI有很大可能会去爬取别的数据，让它保留好爬虫代码，并标注什么时候开发的），实验层、数据交互层（原始结果）、渲染层（论文、poster、Slides）

II.2：让AI通读论文，你要指出所有不专业的画图跟表达，让AI改好。特别是Introduction部分，五段式写法： a.大背景为啥要做这个，普适意义。b.前人做了啥有啥共同缺憾。c.这篇文章受了哪些启发。d.itemize这篇文章的学术贡献（一般来说不可以超过4点，特别的，贡献不是你做了啥工作（因为没人care），而是你发现了啥新奇的东西，回答了什么问题，你的理论突破/技术创新在哪）e. Organization Paragraph。 Introduction一页到一页半，不要过头。Abstract里头最多4行讲背景跟意义，其余是你的方法，亮点跟结果，我建议只挑两个最骄傲的结果或者最独特的发现放摘要里。Related work中有可能一定要把你的work跟别人的列表对比特点。Introduction中可以用Gemini Pro + NanoBanana生成一个提纲挈领的总图，方法是把全文的Latex Code给它并给个样式参考就行（你还得收藏文献，不然好的样式你找不到的）

II.3：AI去看出错/性能不好的地方，让它迭代完善你论文里的研究方案，并生成完整初稿。

II.4：让AI再通读一遍，不准在没有人类审核的情况下创造新概念，保证每个图跟表都在正文中提到了，没有Orphan Figures or Tables，去除冗余跟Self-Defensive expressions, Check whether it contains the pattern of saying something and then trying to emphasize its importance, if there is any then remove. Check all abbreviations, make sure they are defined at first appearance. 至少第一轮的技术报告是一个普通会议的水平，详细说明了系统是如何搭建的，性能如何，这一步也要你平时阅读文献，不然你看不出来水平如何。

II.5: 让AI把代码文档化，生成Markdown文档，如果有必要可以借助Doxygen，特别的要写清楚每个图、表是怎么生成的，并给每个图/表，也就是paper asset写一段文字说明，里头有啥，干啥用的，生成它代码在哪。特别的，要确保有这两项功能，并且verify，a）如何从新运行，update全部数据。b）如何update全部数据、图、表并重新生成论文PDF。

Phase III：

III.1：让AI重新审视这篇论文的代码跟表达，把一眼能看到的问题修掉。

III.2: 根据现有的数据跟结果，如何重新组织论文，从标题到Conclusion，做到Research Finding be valuable to the society/ or a good story，然后全文重写一遍。

III.3 去除Redundant，去除Self-Defensive的表达。

Phase IV：

IV.1: 这一步结束后人工通读精修一遍，消除假参考文献（配合 Sourcely，Paperpal， Elicit），车轱辘话与幻觉，给这篇论文赋予真正的烟火气。
