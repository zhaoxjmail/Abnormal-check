# OutliersCheck And FusionResult 异常值检查，剔除后得到融合结果
 >version 1.0.0   
 >author cc   
 >date 2019.6.7
 
 ####function 功能实现
 * 判断一组数据（原数据）是否存在异常值
 * 能全自动找出一组数据中的异常值的集合（异常集）
 * 能得到去除异常集得到融合后的结果集（融合集）
 * 能得到去除异常集得到融合后的结果值（融合值）
 * 新增：循环查找原数据算出最后的异常集（最终异常集）

## 1. Simple description 简单描述
#### 就是对一组数据进行检查，找出其中的异常值并去除，得到最后正常结果。
## 2. Advantages 算法优势
* 原生java代码，使用jdk8+，绝无其他jar包
* 工具类，即拿即用，不需要太多类的记忆，看到异常值处理，想到cc，想到CCUtil即可。
* 对Integer,Double,以及String型的集合做了兼容性的封装，都可以是原数据。
## 2. e.g 举例说明
>下面同一室内同一地点同一时间点由温度传感器采集到一组温度数据，其中那个数据可能发生了异常？
>  
>  ![图片](https://thumbnail0.baidupcs.com/thumbnail/e47dcf5b8f6bbd9560ce1fb1fd3ed428?fid=3495865747-250528-75614652796259&rt=pr&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-1wbKf9OSZLCie5BrM%2fzWhGoS7vg%3d&expires=8h&chkbd=0&chkv=0&dp-logid=3665662987139532033&dp-callid=0&time=1559926800&size=c256_u256&quality=90&vuk=3495865747&ft=image)
>   
>根据肉眼和经验可以判断出，在温度数据中编号5的32℃是异常值，但湿度数据中很难判断是否存在异常值。
>下面的任务就是一定的算法找出这个异常值，把32度剔除掉，把剩下的温度再处理。
## 3. Quick start 快速入门
>下载和导入依赖后，使用工具类CCUtil即可。

>以下都是提供自动化的算法，介绍几个常用的api。
> * ocExist(list)方法：只要传入一个集合，就能检查出中间是否存在异常值，存在返回true，反之；     
> * ocMap(list)方法：只要传入一个集合，就能返回异常值的下标和值的map集合,如上面实例中返回是{4=32}；
> * fusionList(list)方法：只要传入集合，将异常值去除后的剩下元素的集合输出，如上面实例就返回去掉32度剩下7个温度的集合；
> * fusionValue(list) 方法：传入一个集合，返回将异常值去除后剩下元素的平均值。
## 4. Algorithm principle 算法原理
> * 基于3σ准则改善的cc算法。
> * [论文基础](https://pcsdata.baidu.com/doc/4ffd1434d1cee7a2499382bc102add6c?fid=3495865747-250528-853441141972489&time=1559987974&rt=pr&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-iJ5a9zfkJ1qpK0peeZoI0t2g0j0%3d&expires=8h&chkbd=0&chkv=0&dp-logid=3681853685609331921&dp-callid=0&type=pdf&from=lo&method=newview&ndb_key=n-lodocview-qd-lo-4ffd1434d1cee7a2499382bc102add6c-convert-pdf&region=Qingdao&file_size=2718787&file_type=doc)   
>   简单来说，就是符合正太（高斯）分布的数据，我们都可以通过cc算法来实现大数据量的异常值剔除和融合。
## 5. Explain 说明
>   本人是编程小白，在此文档中暂且只是大致方向上的概述和简单实现这个算法，中间代码，逻辑，数据量，优化等等还有许许多多的不足之处，比如：

>1.未实现对象思想，应该就是全自动，返回一个结果封装好的对象。    
>2.对数据量的算法太少，没有大数据的支持，比如我这套中的源码，简单对数据量的多少自动实现了不同的敏感度（就是对3σ）的数字3进行放大或者缩小，
在目前来说，一组数据中，3<个是没有必要异常值查找的，3~8用1σ准则，8~11用2σ准则，>11用3σ准则。    
>3.代码上存在有逻辑不严谨的地方。     
>4.后面我会完善代码和编写文档，不会和错误的地方太多。     
>5.希望有大数据研究，和我一起来发展这个算法框架的欢迎一起开发vx 13195530002 ，许多不足的地方欢迎指正 584137831@qq.com   

# 在此谢谢大家~
