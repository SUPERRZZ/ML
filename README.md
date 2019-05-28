# Machine Learning   
1. 决策树   
2. Bayes   
3. SVM   
4. KNN   
5. K-Means   
6. EM   
7. 关联规则挖掘   

# TensorFlow     
1. TensorFlow 计算模型 --- 计算图（tf.Graph）      
*TensorFlow中的所有计算都会被转化为计算图上的节点。*     
**计算图的概念：**      
Tensor（张量，数据结构），在TensorFlow中，张量可以被简单的理解为多维数组。     
Flow（直观地表达了张量之间通过计算相互转化的过程，数据模型）     
TensorFlow是一个通过计算图的形式来表述计算的编程系统。     
TensorFlow中的每一个计算都是计算图上的一个节点，而节点之间的边描述了计算之间的依赖关系。       
**计算图的使用：**     
TensorFlow程序一般可以分为两个阶段。      
在第一个阶段需要定义计算图中所有的计算。     
第二个阶段为执行计算。     
TensorFlow中的计算图不仅仅可以用来隔离张量和计算，它还提供了管理张量和计算的机制。       
**总结：**     
计算图是TensorFlow的计算模型，所有TensorFlow的程序都会通过计算图的形式表示。     
计算图上的每一个节点都是一个运算，而计算图上的边则表示了运算之间的数据传递关系。     
计算图上还保存了运行每个运算的设备信息（比如是通过CPU上还是GPU运行）以及运算之间的依赖关系。     
计算图提供了管理不同集合的功能，并且TensorFlow会自动维护5个不同的默认集合。    

2. TensorFlow 数据模型 --- 张量（tf.Tensor）      
*张量是TensorFlow管理数据的形式。*       
**张量的概念：**     
从功能的角度上看，张量可以被简单的理解为多维数组。其中零阶张量表示标量（scalar），也就是一个数；第一阶张量为向量（vector），也就是一个一维数组；第n阶张量可以理解为一个n维数组。     
但张量在TensorFlow中的实现并不是直接采用数组的形式，它只是对TensorFlow中运算结果的引用。在张量中并没有真正保存数字，它保存的是如何得到这些数字的计算过程。     
TensorFlow计算的结果不是一个具体的数字，而是一个张量结构，一个张量中主要保存了三个属性：名字（name）、维度（shape）和类型（type）。     
名字（name）：不仅是一个张量的唯一标识符，它同样也给出了这个张量是如何计算出来的。    
维度（shape）：描述了一个张量的维度信息。     
类型（type）：每一个张量会有一个唯一的类型。TensorFlow会对参与运算的所有张量进行类型的检查，当发现类型不匹配时会报错。    
TensorFlow支持14种不同的类型，主要包括实数（tf.float32、tf.float64）、整数（tf.int8、tf.int16、tf.int32、tf.int64、tf.uint8）、布尔型（tf.bool）和复数（tf.complex64、tf.complex128）。     
**张量的使用：**   
张量使用主要可以总结为两大类：   
第一类用途是对中间计算结果的引用。   
第二类情况是当计算图构造完成之后，张量可以用来获得计算结果，也就是得到真实的数字。     
**总结：**   
张量是TensorFlow的数据模型，TensorFlow中所有运算的输入、输出都是张量。    
张量本身并不存储任何数据，它只是对运算结果的引用。   
通过张量可以更好地组织TensorFlow程序。   

3. TensorFlow 运行模型 --- 会话（tf.Session）    
*会话拥有并管理TensorFlow程序运行时的所有资源。所有计算完成之后需要关闭会话来帮助系统回收资源，否则就可能出现资源泄露的问题。*    
**TensorFlow中使用会话的模式一般有两种：**   
第一种模式需要明确调用会话生成函数和关闭会话函数。   
第二种模式通过Python上下文管理器的机制，只要将所有的计算放在“with”的内部就可以。当上下文管理器退出时候会自动释放所有资源。这样既解决了因为异常退出时资源释放的问题，同时也解决了忘记调用Session.close函数而产生的资源泄露。   