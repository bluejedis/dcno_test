<div style="float: left; width: 64%; padding: 1%;">

### <span style="color: silver;">I/O端口<span style="color: deepskyblue;">编址</span>方式

<ul>

#### <span style="color: silver;"> <span style="color: Gold;">独立</span>~

<ul>

>pro：I/O指令的作用（2017）

- 特点
  - (<span style="color: LightSkyBlue;">I</span>/ <span style="color: Gold;">O</span> <span style="color: Gold;">映射</span>方式
  - I/O端口 <span style="color: GreenYellow;">单</span><span style="color: Gold;">独</span>编址
  - I/O端口地址空间 与 主存地址空间 <span style="color: Gold;">独立
- 优点
  - only need 少量地址线，译码简单
  - 寻址<span style="color: RoyalBlue;">速度</span> <span style="color: GreenYellow;">快</span>
  - 程序清晰易理解
- 缺点
  - I/O指令少，程序设计灵活性差
  - need 两组控制信号，增加控制复杂性

</ul>

#### <span style="color: silver;"><span style="color: gray;">统一</span>~

<ul>

- 特点
  - ( <span style="color: gray;">M</span>~方式
  - <span style="color: Gold;">主存</span><span style="color: DarkRed;">地址</span>空间分出部分 → I/O<span style="color: LightSkyBlue;">端口</span>
  - 使用统一的访存指令
- 优点
  - 无需专门I/O指令，操作灵活方便
  - 端口编址空间大
  - 可利用虚拟存储管理系统实现保护
- 缺点
  - 占用部分主存地址空间
  - 译码电路复杂，速度较慢

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
