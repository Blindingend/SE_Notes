## 数字部件设计

------

### 课本 第一章：二进制

- 字：微处理器处理的一块数据称为字，字的大小取决于微处理器的结构

- 二进制数：有原码和补码两种表示形式

- 缓冲器：一种单输入逻辑门，仅仅将输入复制到输出，符号是一个三角形

- 逻辑电平：将连续变量映射到离散的二进制变量。两个门第一个是驱动源，第二个是接收端，驱动源的输出连接到接收端的输入；由于噪声或部件错误，接收端输入电压存在禁止区域；NMH和NML是噪声容限

  ![1546348914888](http://ww2.sinaimg.cn/large/006tNc79ly1g4bbns90j8j30fq0a2tc2.jpg)

- 直流电压传输特性：一种选择逻辑电平的合理方法是选择在传输特征曲线斜率dv(Y)/dv(A) = -1的位置，这两个位置成为单位增益点。在单位增益点选择逻辑电平可以最大化噪声容限

- 静态约束：对于给定的有效逻辑输入，每个电路元件应该能产生有效的逻辑输出

- ![1546349316440](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd8tidbpj30or05dgn1.jpg)

- nMOS和pMOS

  ![1546349433795](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd98x20xj30ha09wgms.jpg)

- nMOS晶体管能很好的导通低电平，但导通高电平的能力较弱；pMOS晶体管导通高电平的能力较好，但导通低电平的能力较弱。所以，nMOS晶体管在栅极为低电平时OFF，高电平时ON，pMOS晶体管在栅极低电平时ON，高电平时OFF

- CMOS：互补性MOS，同时提供两种类型晶体管的工艺

- CMOS逻辑门

  以非门为例。A=0时P1导通，N1截止，所以Y连到电源两端，输出Y=1

  ![1546349786498](http://ww2.sinaimg.cn/large/006tNc79ly1g4b9hjekqhj306p05474b.jpg) ![1546349805310](http://ww3.sinaimg.cn/large/006tNc79ly1g4bd962ripj308h059t8v.jpg)

- 浮空状态：如果上拉网络和下拉网络同时截止，那么输出既不连接到电源，也不连接到地，电压不确定

- 传输门/使能信号：理想的开关，很好的通过0和1

- 类nMOS逻辑：上拉网络中的pMOS晶体管替换为单个始终导通的弱pMOS晶体管，实现多输入快速或非门，但是电源和地之间有短路，会持续消耗能量

- 静态功耗和动态功耗：静态功耗正比与漏电流IDD和电压VDD，动态功耗正比于电容C、电压VDD和电容电压切换的频率f

  ![1546350339074](http://ww4.sinaimg.cn/large/006tNc79ly1g4ba9897t0j305h01it8j.jpg)![1546350348394](http://ww2.sinaimg.cn/large/006tNc79ly1g4batn0u8cj304h01et8i.jpg)

* 

------

### 课本 第二章：组合逻辑设计

- 组合电路：输出仅仅取决于输入的值，没有记忆

- **组合逻辑需要满足以下条件**

  - **每个电路元件是组合电路**
  - **每个电路节点或是一个电路输入，或是连接到外部电路的一个输出端**
  - **电路不包含回路**
  - ![1547044058092](http://ww4.sinaimg.cn/large/006tNc79ly1g4b9h8psbkj30ni0f60vx.jpg)

- 布尔表达式：与或式和或与式

- 德摩根定理：一个与非门等效于一个带逆变器输入的或门

- 推气泡法来分析电路  ![1546350987263](http://ww4.sinaimg.cn/large/006tNc79ly1g4bd8r1s3mj309h09mwex.jpg)

- 非法值和浮空值/高Z态：竞争，三态缓冲器（图为低电平使能有效）![1546351136772](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd98f513j30ai075jri.jpg)

- 卡诺图  ![1546351355124](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hm8agwj30dc0653yt.jpg)

- 做题流程：应用场景 -> 真值表 -> 卡诺图化简 -> 电路原理图

- 多路复用器：多路复用器可以用于实现各种门逻辑和查找表![1546351519496](http://ww3.sinaimg.cn/large/006tNc79ly1g4bat5b3v3j30nz0cxdh8.jpg)

- ![1546352002208](http://ww4.sinaimg.cn/large/006tNc79ly1g4babm04cgj30no05dt9d.jpg)

- 译码器：译码器的输出成为独热，因为在给定时间恰好只有一个输出为高电平

  ![1546352145225](http://ww2.sinaimg.cn/large/006tNc79ly1g4b9hlpzslj306t08awep.jpg)

- 传播延迟和最小延迟：传播延迟tpd是当输入改变直到所有输出达到最终值所经历的最长时间，最小延迟tcd是当一个输入发生变化直到任何一个输出开始改变的最短时间

- 关键路径和最短路径

  ![1546352416508](http://ww1.sinaimg.cn/large/006tNc79ly1g4ba9tf7efj309a06ojrl.jpg)

- 毛刺和冒险：一个输入信号的改变导致多个输出信号的改变，能够通过在卡诺图中增加多余蕴含项来盖住这些边缘以避免毛刺

  ![1546352544021](http://ww3.sinaimg.cn/large/006tNc79ly1g4baady6w7j30ic06vdgh.jpg)

* 

------

### 课本 第三章：时序逻辑设计

- 双稳态：存储器件的基本模块是一个双稳态元件，该元件有两个稳定状态

  ![1546352754411](http://ww4.sinaimg.cn/large/006tNc79ly1g4bd96zwauj309u05umxf.jpg)

- SR锁存器：与交叉耦合反相器类似，可以设置S和复位R。但SR同时有效时输出不确定，Q和非Q同时为0

  ![1546352852621](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd9c648sj306w04ymx8.jpg)![1546352861922](http://ww4.sinaimg.cn/large/006tNc79ly1g4b9i1nm93j307p04o0su.jpg)![1546352869292](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hktxgkj306q03tdfr.jpg)

- D锁存器：避免了S和R同时有效的奇怪情况

  ![1546352982631](http://ww2.sinaimg.cn/large/006tNc79ly1g4ban211igj30ma053t9b.jpg)

- D触发器：在时钟上升沿将D复制到Q，在其他时间保持原来的状态

  ![1546353027504](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9h7p6ssj30f706wjrx.jpg)

- 逻辑电路与晶体管

  - 与非门/或非门：4个晶体管
  - 非门：2个晶体管
  - 与门/或门：由与非门和非门/或非门和非门组成，6个晶体管
  - SR锁存器：2个或非门，即8个晶体管
  - D锁存器：1个SR锁存器，2个与门，一个非门，即22个晶体管
  - D触发器：2个D锁存器，1个非门，即46个晶体管
  - 寄存器：1以公共CLK输入和一排N个D触发器

- D锁存器和D触发器的区别

  ![1546353537296](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd94mxoxj30qx07qdgh.jpg)

- 带使能和带复位的D触发器

  ![1546353690169](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd9cn5psj30fy084js4.jpg)

  ![1546353700385](http://ww3.sinaimg.cn/large/006tNc79ly1g4bd8s053pj30gk05p0t5.jpg)

- **同步时序电路需要满足以下条件**

  - **每一个电路元件或者是寄存器或者是组合电路**
  - **至少有一个电路元件是寄存器，不能有单独的锁存器**
  - **所有寄存器都接受同一个时钟信号（没有延迟）**
  - **每个环路至少包含一个寄存器**
  - ![1547044146372](http://ww4.sinaimg.cn/large/006tNc79ly1g4ba9rxabmj30nl0h4q6k.jpg)

- 非同步的时序电路称为异步电路

- 有限状态机：Moore型有限状态机和Mealy型有限状态机

  ![1546434918788](http://ww4.sinaimg.cn/large/006tNc79ly1g4bd8txi96j30an07laal.jpg)

  ![1546434941784](http://ww2.sinaimg.cn/large/006tNc79ly1g4b9h40qarj30dq04eglw.jpg)

- 由电路图导出状态机

  - 检查电路，标明输入、输出和状态位
  - 写出下一个状态和输出等式
  - 创建下一个状态和输出表
  - 删除不可达状态来简化下一个状态表
  - 给每个有效状态位组合指定状态名称
  - 用状态名称重写下一个状态和输出表
  - 划出状态转换图
  - 使用文字阐述有限状态机的功能

- 时序逻辑的时序

  - 动态约束：同步时序电路的输入必须在时钟沿附近的建立和维持孔径内保持稳定
  - 系统时序
  - 时钟偏移：时钟并不总是在同一时刻到达各个寄存器
  - 亚稳态
  - 同步器

* 

------

### 复习课 第一讲：计算机组成原理与系统结构中的相关基础

- 计算机的功能：数据运算，数据存储，数据传送，控制

- 有极电容和无极电容

  - 有极性电容大多采用电解质做介质材料，通常同体积的电容有极性电容容量大
  - 有极性电容的耐压值相对要比无极性电容的耐压要低

- 超级电容

  - 功率密度大，但能量密度小

- 电容

  - 公式：Q=CV=∫Idt，E=1/2CV^2，Xc=1/2πfc
  - 通高频阻低频，通交流隔直流
  - 低通滤波器![1546762358421](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hkbyf1j30dx06q74g.jpg)

- 电感

  - 公式：φ=Li，u=Ldi/d，XL=2πLf，E=1/2Li^2

  - 通低频阻高频，通直流阻交流

  - 高通滤波器

    ![1546762652615](http://ww2.sinaimg.cn/large/006tNc79ly1g4ba97ccacj306905v3yj.jpg)

- 晶体二极管

  - ![1546764574470](http://ww3.sinaimg.cn/large/006tNc79ly1g4b9hbw1hnj30h90atdgl.jpg)
- 晶体三极管
  - 发射结面积小于集电结面积
  - 由三极管可构成共射、共基、共集三种放大电路
    - 共射放大电路：电压放大倍数大，输出电压和输入电压反向，电流放大倍数大，输入电阻和输出电阻大小适中，多用于多级放大器的中间级
    - 共集放大电路：电压放大倍数总小于1接近1，输出电压与输入电压同相，电流放大倍数大，可以放大电流和功率，输入电阻大，输出电阻小，多用于多级放大电路的输入级、隔离级和输出级
    - 共基放大电路：电压放大倍数大，输出电压和输入电压同相，电流放大倍数总小于1，不能放大电流，输入电阻小，输出电阻大小适中，频率响应特性好，常用于宽带和高频放大电路
    - ![1546764479120](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd94bzptj30nb0fe0v0.jpg)
  - Uce一般取反向击穿电压UBRCEO的1/2-2/3
  - ![1546764606158](http://ww3.sinaimg.cn/large/006tNc79ly1g4bd97zf8ej30pi0bfgmw.jpg)

- 场效应管
  - 是多数载流子导电，只有一种极性的载流子，所以称为单极型晶体管；三极管被称为双极型晶体管
  - 最大优点是输入端电流几乎为0，具有极高的输入电阻，能满足高内阻的微弱信号源对放大器输入阻抗的要求
  - 体积小，重量轻，噪声低，耗电省，热稳定性好，制造工艺简单，容易集成化
  - ![1546765138008](http://ww1.sinaimg.cn/large/006tNc79ly1g4babobf4xj30ot0aoq47.jpg)
  - ![1546767593903](http://ww1.sinaimg.cn/large/006tNc79ly1g4ba9uck7zj30l906fdgk.jpg)
  - ![1546765353001](http://ww4.sinaimg.cn/large/006tNc79ly1g4b9h9mkmuj30d007gdgh.jpg)
  - 公式1：id = Ido(Ugs/Ugsth -1 )^2 对于N沟道增强型MOS
    - Ido是Ugs=2Ugsth时的id值，Ugsth为开启电压
  - 公式2：低频跨导gm = δid/δUgs 当Ugs=常数
  - ![1546765683398](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hleu2wj30p10e9acm.jpg)
  - ![1546765692669](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd99dtd7j30ox0f8acv.jpg)
- 运算放大器
  - **Vout = （V+ - V-）*A （A≥100000，趋向于无穷大）**
  - 虚短和虚断
    - 运放两个输入端的电压差非常接近于0，但两者之间没有短路
    - 流入运放两个输入端的电流通常可以视为0，但并非断开
  - ![1546766336247](http://ww1.sinaimg.cn/large/006tNc79ly1g4baaefswpj30ia0hen0k.jpg)
- 三态门
  - 指输出既可以是一般逻辑电路的正常高电平或者低电平，又可以是保持特有的高阻抗Z状态，处于高阻抗状态输出电阻很大，相当于开路，没有任何逻辑控制功能
  - 三态门都有一个EN控制使能端来控制门电路的通断。当EN有效时，三态电路呈现正常的0或1输出，当EN无效时，三态电路给出高阻态输出

- 冯诺依曼结构

  - 核心思想：存储程序的概念
  - 计算机由控制器、运算器、存储器、输入、输出五大部件组成
  - 指令和数据都用二进制代码表示，代替十进制
  - 指令和数据都以同等地位存放在同一存储器内，并可按地址寻访
  - 指令是由操作码和地址码组成，操作码用来表示操作的性质，地址码用来表示操作数所在存储器中的位置
  - 指令在存储器内是顺序存放的，按顺序串行执行
  - 以运算器为核心，输入输出设备与存储器的数据传送通过运算器

- 哈佛结构

  - 将程序指令存储和数据存储分开的存储器结构
  - 可以使指令和数据有不同的数据宽度，处理器无法自行初始化

- 计算机体系结构的变化

  - 基于冯诺依曼结构的改进

    ![1546773122880](http://ww1.sinaimg.cn/large/006tNc79ly1g4bat7wkr3j30le091412.jpg)

  - 完全不同的结构：数据流计算机，推理机，神经网络计算机

- 指令集系统结构 ISA

  - 硬件部分：processor, memory, IO system, data path&control, digital design, circuit design, transistors 
  - 软件部分：assembler, compiler, operating system, application

- 噪声容限

  - 逻辑电平是将连续变量映射到离散的二进制变量。两个门第一个是驱动源，第二个是接收端，驱动源的输出连接到接收端的输入；由于噪声或部件错误，接收端输入电压存在禁止区域；NMH和NML是噪声容限![1546348914888](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd97gj43j30fq0a2q41.jpg)

- CMOS和TTL
  - TTL是Transistor-Transistor Logic的缩写，主要由BJT（Bipolar Junction Transistor 即双极结型晶体管），晶体三极管和电阻构成，具有速度快的特点。
  - TTL电平是输出高电平>2.4V，输出低电平<0.4V，噪声容限是0.4V；CMOS电平是逻辑电平电压接近于电源电压，0逻辑电平接近于0V，具有很宽的噪声容限；因为TTL和CMOS的高低电平的值不一样 所以互相连接时需要电平的转换 
  - TTL电路是电流控制器件 CMOS电路是电压控制器件
  - TTL电路的速度快，传输延迟时间短(5-10ns)， 但是功耗大，CMOS电路的速度慢，传输延迟时间长(25-50ns) ，但功耗低。CMOS电路本身的功耗与输入信号的脉冲频率有关，频率越高芯片越热
  - TTL的主要作用：
  - CMOS的主要作用：一是用于计算机信息保存，二是在数字影像领域，三是在更加专业的集成电路设计与制造领域。

* 

------

### 复习课 第二讲：计算机组成原理与系统结构中的相关基础

- 汇编语言

  - 优点：充分利用机器的硬件功能和结构特点，加快程序执行速度，减少目标程序所占用的存储存储空间；常用来编写实时控制程序，实时通信程序，有时也用来编制某些系统软件程序
  - 缺点：编程效率低，与机器硬件的具体结构联系过于紧密

- 高级语言的特点

  - 利于程序员按照接近自然语言的风格思考和表达程序
  - 易于提高程序编制效率
  - 高级语言编写的程序能够较好的独立于计算机硬件，亦即具有较好的可移植性

- 系统软件

  - 分类：操作系统，编译系统，网络系统，工具软件，中间件
  - 处于核心地位的：操作系统和编译器
  - 操作系统是用户程序与硬件的接口
    - 处理基础输入输出操作
    - 分配存储空间及内存
    - 为多个程序同时使用计算机提供支持
  - 编译器：将高级语言翻译成硬件能够执行的语言

- 计算机的分类（按照计算机的规模和运行速度）

  - 巨型计算机
  - 大型主机
  - 小型计算机
  - 工作站：是一种微型化的功能很强的计算机系统，其速度快，内存大，且具有很强的图像处理能力，并且集成有其他的必要的仪器设备，特别适用于工程应用领域的数据处理
  - 单板机
  - 单片机：又称微控制器和嵌入式计算机，是一种把构成一个微型计算机的多个功能部件集成在一块芯片之中的计算机

- 微型计算机主要组装部件：主机系统板；电源和机箱；显示器和键盘；磁盘驱动器；光盘驱动器；各种适配卡

- 功能部件分类

  - Processor/CPU

    - 组成1：Control Unit 控制单元（对执行进行译码，送出控制信号）
    - 组成2：Data path 数据通路（完成指令的执行）：ALU + Register + Multiplexor

  - 存储器

    - 组成1：Primary memory 内存：cache + MM主存
    - 组成2：Secondary memory 外存：Magnetic disk, Optical disk, Tape

  - 输入输出

    - 组成1：IO Controller 控制外设，完成于主机侧，外设侧的通信
    - 组成2：IO device 键盘，鼠标，打印机，显示器

  - 总线：用于互联各功能部件（每条总线上的东西速度最好差不多）

    ![1546772937710](http://ww4.sinaimg.cn/large/006tNc79ly1g4bab8x31tj30nd0etabe.jpg)

    - 优势：具有高度的灵活性，允许将模块插入总线以形成各种配置。从而节省器件，体积小，价格便宜
    - 高速设备和慢速设备连在一条总线上会导致利用率不高，因此会有层级结构

* 

------

### 复习课 第三讲：计算机组成原理与系统结构中的相关基础

- 计算机系统的可靠性
  - **模块可用性 = MTTF / (MTTF+MTTR)**
- 计算机的性能的基本评价指标
  - time to do the task
    - 响应时间 response time
    - 执行时间 execution time
    - 等待时间或时延 latency
  - tasks per day/hour
    - 吞吐率 throughput
    - 带宽 bandwidth
  - 性能发展趋势：带宽优于时延
  - 性能 Performance = 1 / Execution time
  - 响应时间又分为：CPU时间（用户CPU时间，系统CPU时间），其他时间
  - 系统性能：系统响应时间，与CPU外的其他部分也都有关系
  - CPU性能：用户CPU时间，即CPU真正用在用户程序执行上的时间
  - **CPU 时间 = 指令数 * CPI / clock rate = 指令数 * CPI * clock cycle time**
    - CPU时钟速率 clock rate：主频
    - CPI：每条指令的平均周期数
    - CPI = (CPU 时间 * 时钟频率) / 指令条数 = 总时钟周期数 / 指令条数
    - 单靠CPI不能反映CPU的性能，单周期出处理器CPI = 1，但是性能超差
  - MIPS：每秒处理的百万级的机器语言指令数
    - **MIPS = 1 / CPI*时钟周期 = 主频 / CPI**
  - MFLOPS：每秒处理的百万级浮点操作数
- 计算机的内部结构
  - PS2串行数据结构（11位）
    - 起始位1位，数据位8位，校验位1位，结束位1位
  - 触摸屏的类型：电阻式 电容感应式 红外线式 表面声波式
    - 常用的是电容感应式（试试看倒点水）
  - 显存frame buffer
    - VGA信号产生器/控制器：垂直同步，水平同步
    - VGA显示键盘字符过程：键盘 -> 键盘接口控制器 -> 字符显示缓冲区 -> 字模表 -> VGD接口控制器 -> VGD显示器
    - LCD液晶屏
  - 磁盘内圈磁道和外圈磁道。零磁道是在最外圈，这里会放核心的数据

* 

------

### 复习课 第四讲：计算机组成原理与系统结构中的相关基础

- 对现代计算机技术影响最为深远的四种实现技术

  - 集成电路技术
  - 半导体DRAM 动态随机存储器
  - 磁盘技术
  - 网络实现技术

- 晶体管的功率

  - **动态功率 Power dynamic = 1/2 * Capacitive-load * Voltage^2 * Frequency-switch**
    - 晶体管的电容性负载（与扇出和工艺有关）；晶体管的工作电压；晶体管的开关频率（与主频有关）
  - **静态功率 Power static = 泄露电流 * Voltage**

- 关于主频

  - 5G主频的一个clock周期为0.2ns
  - 处理器性能的改进不能再只依赖于指令级并行（ILP），而应更加关注线程级并行（TLP）或数据级并行
  - 多核追求更高的吞吐率，甚至响应时间
  - **主频 = 1 / 时钟周期**

- 处理器性能发展减缓的原因

  - 风冷芯片的最大功耗
  - 所剩无几的可以有效挖掘的指令集并行
  - 难以降低的存储器延迟
  - 无限提高主频并不能一直提高性能

- 集成电路的制造过程

  - 先对一个晶圆进行测试，然后把晶圆切分成晶片，再对每个晶片进行封装
  - 单晶硅锭 - 切片机 - 圆形薄片/硅抛光片/晶圆 - 加工后的晶圆 - 切块机 - 晶片 - 封装 - 芯片

- 集成电路的成本

  - 集成电路成本 = 晶片成本+晶片测试成本+封装成本/最终成品数量

  - 晶片成本 = 晶圆成本/每片晶圆的晶片数*晶片的成品率

  - 每片晶圆的晶片数 = (π*晶圆半径^2)/晶片面积 - (π *晶圆直径)/(根号(2 *晶片面积)

    - 晶圆直径300mm，晶片1.5cm
    - ![1546774710234](http://ww2.sinaimg.cn/large/006tNc79ly1g4bd8rnb72j30jm05o74s.jpg)

  - 晶片的成品率

    ![1546774768040](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hmooaej30o902rjro.jpg)

- Amdahl定律

  - 定义：通过使用某种较快的执行方式所获得的性能提高，受限于可使用这种较快执行方式的时间所占的比例

  - 加速比：![1546775297989](http://ww4.sinaimg.cn/large/006tNc79ly1g4bd95muvjj30js02dq3i.jpg)

  - 新的执行时间

    ![1546775368275](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9hjvrtej30ow05ajsf.jpg)

    ![1546775393440](http://ww4.sinaimg.cn/large/006tNc79ly1g4ba9ts8kkj30n003waao.jpg)

* 

------

### 复习课 第五讲：指令系统 计算机的语言

- 计算机发展简史
  - ABC 1939年 爱荷华州立大学 阿塔纳索夫-贝利计算机 “计算机之父”
  - ENIAC 美国宾夕法尼亚大学 莫奇利和艾克特 40万美元
  - IAS计算机 冯诺依曼结构 存储结构 1946年
  - Cray-1 巨型机 第三代晶体管
  - IBM360系列大型机 兼容机 1964年，8-bit bytes，32-bit words
  - DEC DP8 小型机 首次引入总线结构 1965年
  - PDP-8/E 计算机系统
  - LSI/VLSI/ULSI 1972年 第四代机
  - 真空管 -> 电子管 -> 晶体管 -> 微处理/半导体存储器 -> 神经网络/量子计算机
- 第四代机的特点：以微处理器和半导体存储器技术为核心，特点是共享存储器，分布式存储器及大规模并行处理系统。使得计算机以PC的形式走向用户
- 计算机发展的阶段：电子管，晶体管，集成电路，大规模及超大规模集成电路
- 嵌入式计算机：针对某个特定应用的专用计算机
- ARM体系的特点
  - ARM7是冯诺依曼结构，指令和数据存在于同一存储器空间
  - ARM9是哈佛体系结构，指令和数据各有单独的存储器
  - 应用最广泛的RISC指令集
  - 大多数指令都可以条件执行
  - 灵活的地址自增自减，代码密度高

- MIPS架构：采取精简指令集（RISC）的处理器架构，和龙芯处理器有过知识产权纠纷

- ARM架构：32位精简指令集（RISC）处理器架构，广泛地使用在许多嵌入式系统设计

- 硬件操作数的来源：运算操作数可来自于多处，但计算机硬件只选择有限的集中方式；寄存器是位于CPU内，距离运算器最近、具有最快访问速度的存储器

  - MIPS的操作数设计为只能来自于寄存器，MIPS架构有32个32bit寄存器
  - x86的操作数可直接来自于内存，ARM架构有16个32bit寄存器

- 指令集设计原理

  - 简单即规整，simplicity favors regularity
  - 少即快，smaller is faster
  - 加快经常性事件，make the common case fast
  - 良好的设计即是合理的折衷

- 大端法和小端法：0x12345678

  ![1545869820869](http://ww3.sinaimg.cn/large/006tNc79ly1g4b9h14hwsj30lw070wgc.jpg)

  x86、ARM是小端，MIPS、Power PC是大端

- Intel - IA-32指令系统发展史

  - 典型程序中，大约80%的语句仅仅使用处理机中的20%的指令
  - 执行频率高的简单指令，因复杂指令的存在，在实现中也难以提高其执行速度

- 内存操作数：MIPS不像x86那样有内存操作数

- **RISC的主要特征**

  - 选用频度较高的一些简单指令来构成指令集，复杂指令的功能通过由简单指令的组合来实现
  - 指令长度固定，指令格式种类少，寻址方式少
  - 只有load/store指令访存
  - CPU中有多个通用寄存器
  - 采用流水技术，一个时钟周期完成一条执行
  - 采用组合逻辑的实现控制器
  - 采用优化的编译程序
  - 更能充分利用VLSI芯片的面积
  - 便于设计，可降低成本，提高可靠性

- **CISC的主要特征**

  - 指令系统复杂庞大，各种指令使用频度相差大
  - 指令长度不固定，指令格式种类多，寻址方式多
  - 访存指令不受限制
  - CPU多为专用寄存器
  - 大多数指令需要多个时钟周期才能执行完毕
  - 采用微程序控制器实现控制
  - 难以采用优化编译程序生成高效的目标代码

- 一些RISC与CISC微处理器的特征

  ![1546776454113](http://ww3.sinaimg.cn/large/006tNc79ly1g4b9guozq8j30r40fwjtl.jpg)

- RISC和CISC的现状：近年来两者的争端已经减少许多，原因在于两种技术已经逐渐融合。芯片集成度和硬件速度的增大使得RISC系统也越来越复杂，CISC设计也增加了通用寄存器数量、更强调指令流水线设计。80x86就是一个非常成功的融合系统结构

- 过程/函数/子程序的机器语言级实现过程

  - ![1546777798752](http://ww2.sinaimg.cn/large/006tNc79ly1g4baaguab2j30nl0ihn1l.jpg)

- MIPS的寄存器

  - ![1546777720245](http://ww3.sinaimg.cn/large/006tNc79ly1g4bd95527rj30rw0gxjuo.jpg)

* 

------

### 特别篇：MIPS指令翻译

- MIPS部分指令编码

  ![1546778771345](http://ww3.sinaimg.cn/large/006tNc79ly1g4batq69mwj30s20gdq72.jpg)

  ![1546778782520](http://ww2.sinaimg.cn/large/006tNc79ly1g4ba97scqjj30sb0fsdjg.jpg)

- MIPS寄存器集

  ![1546778200780](http://ww4.sinaimg.cn/large/006tNc79ly1g4bd8siui4j30mh068t9o.jpg)

- R类型指令

  ![1546778247098](http://ww4.sinaimg.cn/large/006tNc79ly1g4b9gyc444j30mi0acad2.jpg)

- I类型指令

  ![1546778262981](http://ww2.sinaimg.cn/large/006tNc79ly1g4ba96w3usj30me077wg9.jpg)

- J类型指令

  ![1546778284520](http://ww1.sinaimg.cn/large/006tNc79ly1g4b9h0a0h0j30mq058jsc.jpg)

- 函数调用时的栈

  ![1546778431777](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd96iqiuj30f009y751.jpg)

- 寻址方式

  ![1546778502080](http://ww1.sinaimg.cn/large/006tNc79ly1g4bd9bqhmdj30mg09wtax.jpg)

- MIPS和x86的主要差异

  ![1546778560952](http://ww2.sinaimg.cn/large/006tNc79ly1g4baadhsbsj30m306gjse.jpg)

- 真值表

  ![1546778622482](http://ww4.sinaimg.cn/large/006tNc79ly1g4b9h3ics3j30m7069dgn.jpg)

![1546779013545](http://ww3.sinaimg.cn/large/006tNc79ly1g4bd8t5m8lj315y0hrgse.jpg)

- 单周期CPU

  ![1546778828222](http://ww2.sinaimg.cn/large/006tNc79ly1g4baad4mp0j30s20g8gop.jpg)

- 流水线CPU

  ![1546778858073](http://ww4.sinaimg.cn/large/006tNc79ly1g4ba9swpo2j30sk0hidka.jpg)

