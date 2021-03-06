title:  树&二叉树&二叉排序树&多路搜索树(B树)-总结

date: 2017-06-17 00:00:01
tags: [ 数据结构 ]



---


完整学习见： 《 大话数据结构》 第六章 树


---


# Tree：根结点-内部节点-终端节点(叶子节点) 组成的数据结构
![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/12872520.jpg)



---
# 二叉树【Binary tree】：每个节点最多有两个子节点
- 遍历二叉树：前序，中序，后续 （利用递归或自循环+ Stack栈回放路径 ）  
![]( http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/94470744.jpg)


---
#   二叉排序树【Binary Sort tree】【BST】：在二叉树的基础上，最左终端结点最小，使用中序遍历的方法可排序元素
- 插入： 致入任意数值，首个为根，后者逐个比较小放左，大放右直至终端结点

-  删除： 叶子结点(直删)  单叶内部结点(子替位)  双叶内部结点(前驱或后继替位)


![]( http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/51153658.jpg)


---
#   二叉平衡树【AVL树】： 是一种高度平衡的二插排序树。子树`深度差`最大为1
-  `平衡因子（BF）`  = 左字树深度-右子树深度
- `BF值为正（即左子树深）`，因此为达到平衡将`整树右旋` / 反之  `整树左旋` 【 目标：找最小不平衡树，进行平衡控制】
- 特殊场景：`旋转节点的BF值`与`旋转方向的参考节点的BF值`是相反的情况下，需要先统一
![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/3065500.jpg)

 
---
#   多路查找树【 muitl-way search tree 】：每个结点可以存储多个元素，孩子数是父结点元素数+1（且必需或全没有）
-  `2-3树`：结点的孩子树可以为2个或3个，即结点元素可以为1个或2个。
     -   2结点如有3孩子,中间字树的范围介于2结点元素的访问之间
    -  元素 插入 2结点 ： 找到最近小于元素的结点，如为2结点可扩展为3结点，插入到右边/无更小值插入2结点的左边
     - 元素插入3结点：因3结点已经是最大容量，无法再插入新元素，需要拆分。
          - 情况一：3结点的父结点是2结点， 可将2结点扩展为3结点，再将待插入的元素补入3结点的子树空位
        - 情况二：3结点的父结点是3结点，需要再向上找是否有可扩展的2结点。扩展后插入方式同上

          - 情况三：结合情况1,2，顶层结点均为3结点，无法再插入元素，则整链的3结点都解体为2结点
     - `删终端 3结点中元素`：不会破坏结构，直删即可
    - `删终端 2结点中元素`：会出现不平衡情况，需要`平衡补位`，补位元素所在结点因由2个结点否则移位后还是不平
    - `删非终端 2结点中元素`  ： 会出现不平衡情况，需要`平衡补位`，前置或后置元素替位
     - `删非终端 3结点中元素`  ： 会出现不平衡情况，需要`平衡补位` ，前置或后置元素 替位


![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/93548120.jpg)

- `2-3-4树`：类似`2-3树`，要么没有孩子要么4个孩子，结点元素可以为1到3个

    - 插入，删除操作同` 2-3树 `逻辑


![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/15573800.jpg)

 
- `B树【B-tree】`： `2-3树`是3阶B树， `2-3-4树`是4阶B树。树阶是最大孩子树的数目

    - 查找：根结点开始查找关键字匹配和区间子树结点的递归匹配

    -  插入，删除操作同` 2-3树 `  `2-3-4树` 逻辑


![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/91316945.jpg)

 
- `B+树`：是`B树`的变形树

    - 1.每个分支结点的元素会在中序`后继者`的位置再次列出：`随机查找`（顶层开始，逐层查找）
    - 2.每个叶子节点会保存指向下一个叶子节点的指针：`范围查找`（从起点开始随下一叶子节点位置按顺序找到范围内所有记录）


![](http://7xnbs3.com1.z0.glb.clouddn.com/17-6-17/83935023.jpg)



---
**参考**
`大话数据结构.pdf` 第六章 树

