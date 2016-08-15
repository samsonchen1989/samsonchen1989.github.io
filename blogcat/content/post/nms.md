+++
date = "2016-08-15T18:49:00+08:00"
title = "也谈No Man's Sky"

+++

如果二十年前有人说自己的游戏里面可以有18,446,744,073,709,551,616（其实就是**2^64**）颗不同的星球，每个星球有自己独特的地貌、环境、生物甚至独特的食物链，你一定会觉得他是被那些节奏诡异闪着《电子世界争霸战》癫狂游离光线的游戏闪傻了。不过2年前《No Man's Sky》在E3上展出的时候，没有人觉得这个是玩笑，只是有点将信将疑——这个当时还只有4个人的工作室**Hello Games**会把这款号称无限可能的游戏推到什么样的高度。

《No Man's Sky》初始版本才3.4个G，但丝毫不影响他模拟星球的能力。在强大的硬件机能支撑下，Procedural Generation变得离玩家越来越近。随着Rougelike类型游戏的流行，很多游戏中的关卡不再是一成不变只要背板就能通过，而是每次随机生成确保每次游戏都有独一无二的体验，比较典型的像《以撒的结合》关卡，但严格意义上来说市面上大部分的Rougelike游戏并不算纯粹的程序生成。依然需要关卡设计师来创造一些基本的地图，然后用伪随机的方式（参见以撒中的Seed）选取地图和怪物进行拼接和配置。

Unity里一种伪随机数的实现方式：
```csharp
    // Unity params
    public bool useRandomSeed;

    // When use pseudo random
    if (useRandomSeed) {
        seed = Time.time.ToString();
    }

    System.Random pseudoRandom = new System.Random(seed.GetHashCode());
    // In a loop
    for () {
        pseudoRandom.Next(0,100)
    }
```

《No Man's Sky》把Procedural Generation在游戏中的应用又提升到一个新的高度，大到星球的地表，小到生物的音效，全部都是由程序按照一定的规则生成。在大部分的Procedural Generation实验里，这些规则都是无序或者散乱的，但是在无人深空里，这套规则，按照制作组的野心，就是尽量模拟靠近宇宙自然的规则，从气候->资源->地形->食物链->生物，一层以一层为基础迭代而来，这才形成了一个独一无二的星球。

当然，野心归野心，从技术角度，NMS的完成度是比较高和有先驱性的，但是作为一个游戏，把所有的生成交给电脑，玩家会有意外的惊喜，但也容易被可能重复的内容磨掉兴趣，让他们觉得“都是套路”。毕竟规则是有限的，有很多人喜欢设计出的惊喜和设计出的情绪调动，而不喜欢冷冰冰的电脑。

从目前的评测来看，NMS的Procedural Generation主要集中在图形和音效上，但在系统和AI上没有什么建树，贸易系统和NPC系统都很初级，喜欢玩太空4X类游戏的人估计也没法再这个游戏里找到自己的点，因为他只有eXplore和eXploit，却没有eXpand和eXterminate。

说到底，这个游戏只是一个程序员们的自然模拟实验，被过于放在聚光灯和舆论中曝光了。战斗，交易，飞船只是附属品，这个游戏的核心在于探索，但大部分人并不在意自己能发现啥，也没有耐心细细地探索每个世界。这个游戏并不适合所有的玩家，这个纯粹由程序和数学构建的游戏，没有刻意的包装和讨好，就像一杯纯净水，拥有无限的形态和可能性，但不可口。

按照现在3A游戏的开发成本和已经不像以前那样饥不择食的玩家，纯PVE和关卡设计的游戏越来越捉襟见肘~~如果能达到像Limbo和Inside那种设计高度当我没说~~PVP（守望屁股），Rougelike（以撒），类Minecraft和Procedural Generation（无人深空）类型的游戏更容易脱颖而出。很多人说NMS吹牛吹破了天，我倒觉得从4个人到20个人，Hello Game小作坊能花三年做到这样的完成度，已经很了不起了。在技术的实验探索上，也不知道比国内某些冷嘲热讽的开发者高到哪里去。

这里有一篇比较专业的评测，有兴趣可以看看：[No Man’s Sky and the Future of Procedural Games](http://www.makeuseof.com/tag/no-mans-sky-future-procedural-games/)

这位大哥受无人深空启发，做了一个[2D的星球版画生成器](https://marian42.github.io/proceduralart/)。