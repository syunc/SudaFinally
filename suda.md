单链表操作：1

顺序表操作：1

二叉链的二叉树的创建 times：1

图的顶点与边的关系

Dijkstra算法的用途，思想，手动模拟验证其正确性 times：1





### 2010年

###### 数据结构

*chapter 2*

- [ ] 线性表

```javascript
//线性表的基本操作
---初始化---
InitList(&L);
---读操作---
Length(L);
LocateElem(L,e);
GetElement(L,i);
PrintList(L);
Empty(L);#空表返回TRUE，否则返回Flase
---写操作---
ListInsert(&L,i,e);
ListDelete(&L,i,&e);#删除L表中第i个，并用e返回删除的元素值
DestroyList(&L);
```

- 线性表的定义

```javascript
**** 顺序存储类型 ****
    
--- (静态分配)---
#define MaxSize 50
typedef struct {
	ElementType data[MaxSize];
    int length;
}SqlList;

--- 动态分配---
#define InitSize 100
typedef struct {
    ElementType *data;
    int MaxSize,length;
}SeqList;

usage：L.data = (ElementType*)malloc(sizeof(ElementType)*InitSize);
```

- 线性表的特点

```javascript
1. 随机存取，通过首地址和元素序号在O(1)时间内找到指定元素
2. 存储密度高
3. 逻辑上相邻的元素，物理上也相邻，所以插入需要移动大量元素；
```

- 时间复杂度

  ```
  最好情况：O(1)
  最坏情况：O(n)
  平均情况：O(n)
  ```

  

- [ ] 顺序表

- [ ] 链表

```
1. 删除
2. 插入
3. 新建

--- 删除链表指定元素 ---
/*
 * 不带头结点，则初始调用传入的需为指针，当做第一个定位点
 * 若带头结点，可直接传入链表首地址，设置指针操作
 */
void del_x (sqlList &L, ElementType x) {
    Lnode *q;//指向被删除的结点
    if(L == NULL) {
        return;
    }
    if(L->data == x) {
        q = L;
        L = L->next;
        free(q);
        del_x(pre, x)
    }
    else {
        L = L->next;//指向下一结点
        del_x(L, x);
    }
}

--- 线性表满足奇数位序元素为奇数 ---
void arrangeNum(SqlList L, int Length) 
    int oddposition,evenposition;//两个分别指向奇位置和偶位置的序号；
    int temp;
    oddposition = 0,evenposition = 1;//因为数组下标从0开始，则奇数序号从0,2,4...偶数序号1,3,5...
    while(oddposition + evenposition < 2*(Length-1)) {//两个指针都不超出表长
        if(L.data[oddposition] % 2 == 1) { //当前指针所指位置为奇数则将指针移至下一个奇位置
            oddposition += 2; 
        }
        else {
            if(L.data[evenposition] %2 == 1) {//当前奇数位序为偶数且偶数位序的元素为奇数，则交换
                temp = L.data[oddposition];
                L.data[oddposition] = L.data[evenposition];
                L.data[evenposition] = temp;
            }
            evenposition += 2;//偶数位序指针移至下一偶数位序地址
        }
    }
}
```



- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 栈和队列

```shell
### concept
1.栈和队列的异同
	相同点：都是线性表
	不同点：区别在于不同的读写方式。
        队列：按先进先出原则，出队入队操作发生在存储区的两端
        栈：按后进先出原则，进栈出栈操作发生在存储区同一端



```



- [ ] 压缩矩阵

```shell
### concept 
1.什么是压缩矩阵的
	答：矩阵的压缩存储指为多个值相同的元素只分配一个存储空间，对零元素不分配存储空间。其目的是为了节省存储空间。
2.不同矩阵的压缩存储
  1).对称矩阵 
  
  
  
  
  
  
  
  
  
  2).三角矩阵 
  
  
  
  
  
  
  
  
  
  
  
  
  
  3).三对角矩阵
  
  
  
  
  
  
  
  
  
  
  
  
  4).稀疏矩阵 
  	三元组法：
        A[][0] = 行坐标
        A[][1] = 列坐标
        A[][2] = 该位置的值
   // for example 
        A[0][0] = 4  // 矩阵的行数     
        A[0][1] = 4  // 矩阵的列数
        A[0][2] = 3  // 矩阵中非零元素的个数

        A[1][0] = 0  // 1 元素的行坐标
        A[1][1] = 0  // 1 元素的列坐标
        A[1][2] = 1  // 1 元素的值

        A[2][0] = 2  // 7 元素的行坐标
        A[2][1] = 0  // 7 元素的列坐标
        A[2][2] = 2  // 7 元素的值

        A[3][0] = 3  // 4 元素的行坐标
        A[3][1] = 3  // 4 元素的列坐标
        A[3][2] = 4  // 4 元素的值

        A[][] = {{4,4,3},{0,0,1},{2,0,2},{3,3,4}} //压缩后的矩阵
```



*chapter 4*

- [ ] 二叉树 + 算术表达式

```
--- 二元运算符算术表达式存储在二叉树，计算表达式值 ---

```



*chapter 5*

- [ ] 广度优先遍历

```c
//广度优先算法
bool visited[MAX_VERTEX_NUM];
void BFSTraverse (Graph G) {
    for (i = 0; i<G.vexnum; ++i) {
        visited[i] = FALSE;
    }
    InitQueue(Q);
    for (i = 0; i<G.vexnum; ++i) {
        if(!visited[i]);
        BFS(G, i);
    }
}

void BFS (Graph G, int v) {
    visit(v);
    visited[v] = TRUE;
    Enqueue(Q, v);
    while(!isEmpty(Q)) {
        Dequeue(Q, v);
        for(w = FirstNeighbor(G, v); w>0; w = NextNeighbor(G, v, w)) {
            if(!visited[w]) {
                visit(w);
                visited[w] = TRUE;
                EnQueue(Q, w);
            } //if
        } // for
    } //while
}

//广度优先算法的单源最短路径

void BFS_MIN_Distance(Graph G, int u) {
    //d[i]表示从u到i结点的最短路径
    for(i=0; i<G.vexnum; i++) {
        d[i] = -1;
    }
    visited[u] = true;d[u] = 0;
    EnQueue(Q, u); // 队头元素出队
    while(!isEmpty(Q)) {
        Dequeue(Q, u);
        for(w = FirstNeighbor(G, u); w>0; w = NextNeighbor(G, u, w)) {
            if(!visited[w]) { //w为u的尚未访问的邻接顶点
                visit(w);
                visited[w] = TRUE;
                d[w] = d[u] + 1; //路劲长度加1
                EnQueue(Q, w);顶点w入队
            } //if
        } // for
    } //while
}


```

- 时间复杂度

```
--- 邻接表 ---
每个顶点搜索一次(即入队一次) => O(|V|)
每条边至少访问一次          => O(|E|)
所以时间复杂度为 O(|E|) + O(|V|)

--- 邻接矩阵 --- 
查找每个顶点 => O(|V|)
所以时间复杂度为 O(|V|)xO(|V|)
```

- 广度优先生成树

















- [ ] 深度优先遍历

```
//深度优先遍历
bool visited[MAX_VERTEX_NUM];
void DFSTraverse (Graph G) {
    for (v = 0; v<G.vexnum; ++v) {
        visited[v] = FALSE;
    }
    for (v = 0; v<G.vexnum; ++v) {
        if(!visited[v]);
        DFS(G, v);
    }
}

void BFS (Graph G, int v) {
    visit(w);
    visited[w] = TRUE;
    for(w = FirstNeighbor(G, u); w>0; w = NextNeighbor(G, u, w)) {
            if(!visited[w]) { //w为u的尚未访问的邻接顶点
                DFS(G,w)
            } //if
        } // for
}
```

- 时间复杂度

```
--- 邻接表 ---
所以时间复杂度为 O(|E|) + O(|V|)

--- 邻接矩阵 --- 
所以时间复杂度为 O(|V|)xO(|V|)
```

- 空间复杂度

```
借助工作栈递归
所以空间复杂度为 O(|V|)
```

- 深度优先生成树





















###### 操作系统



### 2011年

###### 数据结构

*chapter 2*

`some tips:` 

```c
for example :int temp = 3; (temp的变量地址为0x8000) 

int*代表 将绝对地址转化为内存的地址 =》 内存的物理地址(0x8000)
*(int*)temp =3 ;//对地址进行写操作
(int&): 将某个变量解释为整型。
```



- [ ] 单链表

```
--- 不带头结点，递归，将偶数结点与奇数结点拆分 ---
void depatchLists(LinkList *L1,LinkList *L2) {
    LinkList *p;
    if(!L1) {
        return;
    }
    
    if(L1->data % 2 == 0) {
    	p = L1;
        L2->next = L1;
        L1 = L1->next;
        free(p);
        depatchLists(L1,L2);
    }
    depatchLists(L1->next,L2);
}

--- 将偶数序号结点与奇数序号结点拆分 ---
算法设计思想：设置一个访问变量，初值为0，每访问一个结点序号自动加1，然后根据序号的奇偶性将结点进行拆分到不同的表，重复操作直至到表尾。







```



- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 队列 + 循环队列

```
1. 队列定义
	只允许在表的一端进行插入，而在表的另一端进行删除，这种操作受限的线性表叫队列。
2.循环队列定义	
	循环队列是指将顺序队列假想为一个环状的空间，即把存储队列元素的表从逻辑上看成一个环。
	
	
	
	
```



- [ ] 压缩矩阵

*chapter 4*

- [ ] 二叉树

```c
--- 层次遍历 --- 
void LevelOrder(BTNode *b) 
{ 
    BTNode *p;
	BTNode *Q[MaxSize];  
	int front,rear; 

	front=rear=-1; 
    rear++;//队尾指针向后移动
	Q[rear]=b;//根结点入队
	while(front!=rear)//队不空则出队，并把孩子结点入队
    { 
        front=(front+1)%MaxSize;//队头指针往前移动
        p=Q[front];//结点出队
		printf("%c ",p->data);//visit        
		if(p->lchild!=NULL)//存在左孩子则入队
        {
	    	rear=(rear+1)%MaxSize;            
			Q[rear]=p->lchild; 
        }    
        if(p->rchild!=NULL) //存在右孩子则入队
        { 
            rear=(rear+1)%MaxSize;             
			Q[rear]=p->rchild; 
        }          
	}     
}
    
    
    
--- 层次遍历+非递归 求解树的高度 ---
    
    
    

    
    
 --- 层次遍历+递归 求解树的高度 ---   
    






```







*chapter 5*

- [ ] 最小生成树

```
1. 最小生成树定义
	对于一个带权连通无向图G=(V,E),生成树不同，每棵树的权也可能不同。设R为G的所有生成树的集合，若T为R中边的权值之和最小的那棵生成树，则T称为G的最小生成树。构造最小生成树有普里姆算法和克鲁斯卡尔算法。
	
```

- 最小生成树的构造

```
--- Prim ---
输入：图G=(V,E,W), V={1,2,3,...n}
设计思想：初始S={1}//加入一个顶点
选择连接S与V-S集合的最短边e={i,j},其中i ∈ S，j ∈ V-S，将e加入树T，j加入S.
继续执行上述过程，直至S=V为止

    *** 伪码 ***
  1. S <- {1}
  2. while V-S ≠ ∅ do
  3.     从V-S中选择j使得j到S中顶点的边权值最小
  4.     S <- S ∪ {j}

正确性证明：归纳法


时间复杂度
算法步骤执行O(n)次
每次执行O(n)时间:找连接S与V-S的最短边
算法时间复杂度为：T(n) = O(n²)


--- Kruskal ---

输入：图G=(V,E,W), V={1,2,3,...n}
输出：图G的最小生成树

设计思想：
（1）按照长度从小到大对边排序，
（2）依次考察当前最短边e，如果e与T的边不构成回路，则把e加入树T，否则跳过e直到选择了n-1条边为止

输入：连通图G //顶点数n,边数m
输出：G的最小生成树

1. 权从小到大排序E的边，E={e1,e2....em}
2. T <- ∅
3. repeat
4. 	  e  <- E中的最短边
5.    if e的两端点不在同一连通分支
6.	  then T <- T ∪ {e}
7.    E  <- E-{e}
8. until T 包含了n-1条边

```



- [ ] 单源最短路问题

>给定带权有向网络G=（V，E，W）每条边e=<i,j>的权w(e)为非负实数，表示从i到j的距离源点s∈V.求：从s出发到达其他节点的最短路径。

```shell

--- Dijkstra算法 --- 

*** 有关概念 *** 
初始 S = {s}, S = V 时算法结束
从s到u相对于S的最短路径：从s到u且仅经过S中顶点的最短路径

dist[u] : 从s到u相对于S最短路径：从s到u且经过S中顶点的最短路径 (需要经过集合S的相对最短路径长度)
short[u] : 从s到u的最短路径的长度 (全局，即问题解，所有路径最短的那一条 final result)
dist[u] ≥ short[u] (不断计算相对的最短长度，不断扩充S的集合后，相对长度会越来越改善，当改善到和全局最短路一样长)

*** 设计思想 ***
输入：有向图G = (V,E,W)， V = (1,2,3,....n),s=1
输出：从s到每个顶点的最短路径

1. 初始 S = {1}
2. 对于 i ∈ V-S,计算1到i相对于S的最短路，长度dist=[i]
3. 选择V-S中dist值最小的j，将j加入S,修改V-S中顶点的dist值
4. 继续上述过程，直到S=V为止

*** 伪码 ***
1. S <- {s}
2. dist[s] <- 0
3. for i ∈ V-{s} do
4. 	  dist[i] <- w(s,i) //s到i没边，w(s,i) = ∞
5. while V-S≠∅ do
6.	  从V-S取相对于S的最短路径的顶点j
7.	  S <- S ∪ {j}
8.	  for i ∈ V-S do
9.    if dist[i] + w(j,i) < dist[i] //加入的顶点使从源点到其他顶点的路径更小则更新dist数组值
10.   then dist[i] <- dist[i] + w(j,i)




```

- [ ] Dijkstra算法的基本原理



*chapter 6*

- [ ] 查找

```c
--- NxN的矩阵(行元素值递增，列元素值递增)，使用O(n)算法确定x是否在矩阵中 ---
算法思想：从右上角开始，每次将搜索值与右上角的值比较，如果大于右上角的值，则直接去除1行，否则，则去掉1列。依次类推，继续下去，算法的时间复杂度即为O(n).
bool stepWise(int mat[][], int N, int x, int &row, int &col) {
    if (x< mat[0][0] || x > mat[N-1][N-1]) 
        return false;
    row = 0;
    col = N-1;
    while (row <= N-1 && col >= 0) {
        if (mat[row][col] < target)
            row++;
        else if (mat[row][col] > target)
            col--;
        else
            return true;
    }
    return false;
}

```



*chapter 7*

- [ ] 排序的时间复杂度比较以及各个排序的特点，根据特点选择排序

```
各个排序算法的特点
Q: 随机排序的n个记录的链表，其中n>1000
A:直接插入排序，因为直接插入排序适用于链表，而其他大多数排序只适用于顺序表。
----
Q: 随机排序的n个记录的数组，其中n>1000
A:快速排序，n极大时应采用复杂度为O(log2n)的排序算法，且当排序的关键字是随机排列时，速排序的时间最短。
----
Q: n个记录，其中所以的记录都距离正确位置至多两个位置
A：冒泡排序，因为记录距离正确位置至多两个位置，已基本有序。



```



###### 操作系统



### 2012年

###### 数据结构

*chapter 2*

- [ ] 单链表删除元素插入到另一链表

*chapter 3* 

- [ ] 栈模拟队列
- [ ] 队列操作

*chapter 4*

- [ ] 用二叉链表建立二叉树

*chapter 5*

- [ ] 图中顶点与边关系
- [ ] 顶点与边与存储的矩阵的关系
- [ ] 判断环

- [ ] Floyd 算法的思想及性能分析



*chapter 6*



*chapter 7*

- [ ] 简单排序



###### 操作系统



### 2013年

###### 数据结构

*chapter 2*

- [ ] 单链表+递归删除关键字

*chapter 3* 

- [ ] 

*chapter 4*

- 存储结构

- [ ] 双亲表示法

```c
--- define and description ---
#define MAX_TREE_SIZE 100 //最多结点个数

typedef struct { //树的结点定义
	ElementType data; //数据元素
	int parent; //双亲位置域
}PTNode;
typedef struct { //树的类型定义
	PTNode nodes[MAX_TREE_SIZE]; //双亲表示
	int n; //结点数
}PTNode;
```



<img src="images/tree/saving/tree.png" style="zoom:80%;" />



`应用：双亲表示法应用于解决查找某结点的父结点` 



- [ ] 孩子表示法

> 邻接表

<img src="images/tree/saving/tree.png" alt="img" style="zoom:80%;" />



<img src="images/tree/saving/2.png" style="zoom:80%;" />



`应用：孩子表示法应用于查找某结点的孩子结点`



- [ ] 孩子兄弟表示法(二叉树表示法)

> 左指针指向第一个孩子结点，右指针指向兄弟结点

```c
--- define and description ---
typedef struct CSNode {
	ElementType data; //数据域
	struct CSNode *firstchild,*nextsibling;//第一个孩子和右兄弟指针
}CSNode, *CSTree;
```



![img](images/tree/saving/3.png)



`特点 :最大的优点就是可以方便实现树转换为二叉树的操作，易于查找结点的孩子，其缺点是查找双亲比较麻烦。 `

`usage:`

```
--- 统计结点个数 + 递归 ---




```



*chapter 5*



- 图的存储方式

- [ ] 邻接矩阵存储的定义

```c
--- define ---
#define MaxVertexNum 100; //顶点的最大数目
#define int VertexType;  //顶点的数据类型
#define char EdgeType;  //带权图中边上的权值的数据类型
Typedef struct{
	VertexType vex[MaxVertexNum]; //顶点表
	EdgeType edge[MaxVertexNum][ MaxVertexNum]; //邻接矩阵，边表
	int vexnum,arcnum;  //图的当前顶点数和弧数
} MGraph;

--- 特点 ---
   
1. 一定是一个对称矩阵并且唯一，实际存储中只需要存储上三角或者下三角
2. row i and col j 所对应在图的邻接矩阵的存储中的下标是(i*(i+1)/2 + j)
3. 无向图中 row i 或者 col i 所对应的非0(或者非∞的元素)的个数是第i个顶点的度
4. 在有向图中row i 所对应的非0(或者非∞的元素)的个数是第i个顶点的出度OD(Vi)， col i 所对应的非0(或者非∞的元素)的个数是第i个顶点的入度ID(Vi)
5. 稠密图适合邻接矩阵
6. 设图G的邻接矩阵为A,A1为A的n次幂相乘的矩阵，则元素A1[i][j]等于由顶点i到顶点j的长度为n的路劲的数目..
7. 空间复杂度为O(n²)，其中n为顶点数
8. 其主对角线代表从自身顶点到自身的距离，所以全部为0
```



- [ ] 邻接表的定义

> 为每个结点开辟指针，指针指向连接的结点

```c
--- define ---
#define MaxVertexNum 100; //顶点的最大数目
#define int VertexType;  //顶点的数据类型

Typedef struct ArcNode {
	int adjvex; //弧指向的顶点
	struct ArcNode *next; //下一条弧的指针
	//InfoType info; //网的边权值
} ArcNode;

Typedef struct VNode { //顶点表结点
	VertexType data; //顶点信息
	ArcNode *first; //指向第一条依附该顶点的弧的指针
} VNode,AdjList[MaxVertexNum];

Typedef struct {
	adjList vertices; //邻接表
	int vexnum,arcnum; //图的顶点数和弧数
} ALGraph; //ALGraph是以邻接表存储的图类型

--- 特点 ---
1. 若为无向图存储空间O(|V|+2|E|)(倍数2是因为每条边出现了两次)
2. 若为有向图存储空间O(|V|+|E|)
3. 适合稀疏图
4. 计算出度只需要计算顶点的邻接表的结点个数
5. 图的邻接表表示不唯一

```



- [ ] Disjkstra算法求单元最短路径的思想



```
--- Reference --- 
算法思想：设有两个顶点集合S和T，S中存放图中已找到最短路径的顶点，T存放图中剩余顶点。初始时，S中只包含Vo，然后不断从T中选取到Vo路径长度最短的顶点Vu并入到S中，S每并入一个新的顶点，Vu都要修改顶点Vo到T中顶点的最短路径长度值。不断重复此过程，直到T中顶点全部并入到S中为止。时间复杂度是O(n²)。
```



*chapter 6*

- [ ] hash表构造及查找



###### 操作系统



### 2014年

###### 数据结构

*chapter 2*

- [ ] 单链表
- [ ] 顺序表

*chapter 3* 

- [ ] 

*chapter 4*

- [ ] 二叉链的二叉树

*chapter 5*

- [ ] Dijkstra算法的用途，思想，手动模拟验证其正确性



###### 操作系统



### 2015年

###### 数据结构

*chapter 2*

- [ ] 单链表
- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 

*chapter 4*

- [ ] 递归建立二叉树

*chapter 5*

- [ ] 图的度
- [ ] 拓扑序列



###### 操作系统

```

```



### 2016年

###### 数据结构

*chapter 2*

- [ ] 单链表
- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 栈和队列
- [ ] 压缩矩阵

*chapter 4*

- [ ] 二叉树建立

*chapter 5*

- [ ] 图的入度与出度

*chapter 7*

堆排序，归并排序



###### 操作系统



### 2017年

###### 数据结构

*chapter 2*

- [ ] 单链表
- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 栈和队列
- [ ] 压缩矩阵

*chapter 4*

- [ ] 二叉树 + 算术表达式

*chapter 5*

- [ ] 广度优先遍历
- [ ] 深度优先遍历



###### 操作系统



### 2018年

###### 数据结构

*chapter 2*

- [ ] 单链表
- [ ] 顺序表元素重新排序

*chapter 3* 

- [ ] 栈和队列
- [ ] 压缩矩阵

*chapter 4*

- [ ] 二叉树 + 算术表达式

*chapter 5*

- [ ] 广度优先遍历
- [ ] 深度优先遍历



###### 操作系统







引用参考