

Javac有10万行以上的源代码实现，并且代码的逻辑密度非常大，这是一个巨大的工程，作为一个使用java多年的程序员，整明白这10万行代码其中的逻辑，我想后半辈子找一份工作还是不成问题的吧。



# 1.编译器也分前后端

## 什么是编译器的前端

Javac命令可以将Java源代码转换为虚拟机能够识别的Class文件形式，以class作为文件存储格式。能够进行这种转换的编译器一般也称为编译器的前端。

将Class文件中存储的字节码变为机器码，这是编译器后端需要完成的工作，如JIT编译器（Just In Time Compiler）。

### 前端编译器工作原理，也就是Javac的工作原理

![前端编译器工作原理](https://tva1.sinaimg.cn/large/007S8ZIlly1gif3dkiscuj30px053mxi.jpg)

### Token流

![image-20200904222243461](https://tva1.sinaimg.cn/large/007S8ZIlly1giezfyyo1sj30qk03sq3t.jpg)

**像这样的每一块都是一个 token**。

在我要实现的解释器中，每一个 token 有四个属性他们分别是：`type`、`lexeme`、`literal`、`line`什么是Token流



### 语法分析

词法分析的主要作用就是将Java源代码转换为Token流

<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gif3nir03lj30f507vwet.jpg" alt="image-20200905004825036" style="zoom:150%;" />

经过语法分析生成Token流

![image-20200905004906796](https://tva1.sinaimg.cn/large/007S8ZIlly1gif3o91evhj30jo0983zv.jpg)

经过Javac的词法分析阶段后转换为Token流，图中的每个小方格表示一个具体的Token。图中可以看到，词法分析将Java源代码按照Java关键字、自定义标识符和符号等分解为可识别的Token流。（identifier：标识符）







