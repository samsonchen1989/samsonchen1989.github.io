+++
date = "2016-08-02T20:56:09+08:00"
title = "有关音乐音效"

+++

国内的公司对音效音乐啥的不怎么重视，可能一个稍微大点的公司里只有一个人来负责音效音乐的……嗯，外包接洽工作，而那些无良的外包公司七拼八凑一些音效就扔给你。一个活例子就是我们找了家特便宜的音效外包，结果直到老外玩家给了差评才发现，给过来的战斗胜利音效竟然和COC一模一样。

相反，去KS上筹钱的项目里，四五个人的团队介绍里面总会有一个妹子或者花臂大哥，title是音乐音效指导，作曲家。Steam上很多游戏的唯一DLC就是Soundtrack原声包，还价格不菲。

没办法，这就是做方便面和担仔面，批发调料包和自己炖浇头的区别。之所以想到这个比方是因为上周去大悦城吃了一家叫“度小月”台湾面，味道还不错，就是量太少了，一碗根本不够吃。这也或许是为啥玩家还是会对各种流水线商业游戏趋之若鹜，按照Limbo和Inside这家工作室的开发速度，艺术游戏和精良的个人游戏是喂不饱疯狂的~~特别闲的~~玩家的。

为了证明上面的问题，拆了COC的包，顺便看了看它的音乐文件格式：

平台 | 音乐文件格式 | 音效文件格式
---|---|---|
Android | **.mp3**(比特率**64kbps**) | **.ogg**(比特率**32~42kbps**)
iOS|**.mp3**(比特率**64kbps**)|**.caf**(比特率**32kbps**)

一般现在的游戏引擎都会把音乐和音效的播放分开，音乐同一时间只能播放一个，音效可以同时播放多个，但也有例外，比如针对三星的一些Android机型，同时播放多个音效文件会造成明显的卡顿，所以需要一个计时器来限定下单位时间内播放音效的次数。

```lua
AudioManager.repeatSfx = {}

local function limitSoundPlay(sfx_name)
  if AudioManager.repeatSfx[sfx_name] or table.nums(AudioManager.repeatSfx) > 2 then
    return true
  end

  AudioManager.repeatSfx[sfx_name] = scheduler.performWithDelayGlobal(function()
    AudioManager.repeatSfx[sfx_name] = nil
  end,0.3)

  return false
end
```
