## 14. 误差分析：查看开发集样本来评估想法

当你在使用你的猫咪分类App的时候，你注意到有几张狗的照片被错误分类成了猫。这些狗看起来也确实像猫。

![](https://raw.githubusercontent.com/AlbertHG/Machine-Learning-Yearning-Chinese-ver/master/md_images/7.jpg)

一个团队成员建议加入第三方软件，这样可以让系统更好的处理狗的图片。这个变动预计将耗费一个月的时间，同时团队的其他成员也很热衷于这个方案。你应该让他们继续下去吗？

在投入这一个月的时间来完成这项任务之前，我建议你应该首先评估下这个改变到底能提升多少系统准确率。然后，你才可以更加理性地决定是否值得为此花费一个月的开发时间，或者说不如用这一个月时间去完成一些其他的任务。

具体来说，你可以做以下事情：

1. 收集你系统误分类((Misclassified)的100个开发集样例，即系统发生错误的那些样本；
2. 人工检查这些样例，并记录它们中的狗图像的占比。

检查误分类样例的过程被称为：误差分析(Error Analysis)。在这个例子中，如果你发现在误分类的样本中狗的图片占比只有5%，那么无论你如何改进对狗的识别算法，都不可能降低5%以上的错误，换句话说，5%是预定的改进计划（加入第三方库）所能提升的“上限(Ceiling)”。因此，如果你的系统目前的准确率是90%（10%的误差），那么这个改进最多能将准确率提升到90.5% [1]。

> [1].译者注：上一段，说到的10%的误差应该指的是开发集误差。因为取出的100个误分类样例都来自10%的开发集误差样本里边，也就是如果你将这5%的错误全部消除，对于整个开发集来说，提升的性能也就只有0.5%（10%的5%=0.5%），即从90%->90.5%。

相反的，如果你发现在误分类的样本中有50%被误分类为狗，那么你可以坚信这个提议（引入第三方软件）会对系统准确率的提升有很大帮助。它可以把准确率从90%提升到95% [2]。

> [2].译者注：10%的开发集误差，里边有50%是被误分类为狗，假设完全修复这个bug可以提升5%（10%的50%=5%），也就是从90%->95%。

这种简单的误差分析计算过程为你提供了一种方法来评估为“修正误分类为狗”这个问题而加入第三方软件的潜在价值。它为决定是否将时间投入到这项工作提供了量化基础。

误差分析经常能帮助你弄清楚不同方向所隐藏的价值。我曾经常看到许多工程师都不愿意进行误差分析。相比于质疑某个想法是否值得花时间投入，直接扎入一个想法并行动更加让人感到刺激。这是一个常见的错误：这种习惯可能会导致你的团队花费了一个月的时间才发现它并不能为系统带来什么好处。

手动检查这100个误分类样例并不需要花费很长的时间。即使你每幅图片都花费1分钟，总的算下来也就是不到2小时的事情。而这短短的两个小时却能节省你一个月的精力。

*“误差分析”是指在开发集中检查被算法错误分类的那些样本以便理解错误根本原因的过程。它能够帮助你确定项目的优先顺序（如本例所示），并启发我们接下来将要考虑的新的方向。接下来的几节内容还将接着介绍一些误差分析的最佳实践。*