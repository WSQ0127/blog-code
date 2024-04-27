---
title: 517编程普及组数学之图论基础
categories: OI
tags:
  - OI
  - C++
  - 517coding
  - 数学
  - 图论
cover: 'https://image.wsq127.top/file/bb91b00c28fd2210948bd.png'
abbrlink: 362ffdf7
date: 2024-04-18 00:10:06
---
在算法或数学中，图是由若干给定的顶点及连接两顶点的边所构成的图形，这种图形通常用来描述某些事物之间的某种特定关系。顶点用于代表事物，连接两顶点的边则用于表示两个事物间具有这种关系。

### 基本概念

* **节点（或顶点）**：图中的一个元素，可以用来表示某个实体或概念。在C++中，通常可以用整数或自定义的结构体来表示节点。
* **度**：指与一个点相连的节点数量。
* **边**：连接图中两个节点的线，可以是有向的（箭头指向）也可以是无向的。
* **边权**：指一条边的权值，可以理解为长度。

### 分类

* **无向图**：指每条边都是没有方向的图，可以从任意一边出发，类似双行道。
* **有向图**：指每条边都是有方向的，只能按照相应的方向，类似单行道。
* **完全图**：只每两个点之间都有一条边。一个有 $n$ 个节点的完全图有 $n*(n-1)/2$ 条边。
* **连通图**：指每个点都可以到达另一个点。
* **连通块**：一张非连通图中会有多个连通块，每一个连通块中的每个点都可以到达另一个点。
* **树**：指 $n$ 个点，$n-1$ 条边的连通图。

### 表示

在 C++ 中，图有两种表达：

* #### 邻接矩阵：

    通过矩阵存储图，`a[i][j]` 表示点 $i$ 到点 $j$​ 是否有边。

    ```c++
    int a[N][N]//定义
    a[u][v]=1//添加一条 u 指向 v 的节点
    ```

    

* #### 邻接表

    使用向量数组存储图， `a[i]` 存储所有点 $i$​​ 指向的点。

    ```C++
    vector<int> a[N]//定义
    a[u].push_back(v)//添加一条 u 指向 v 的节点
    ```

    

### 算法

* #### 拓扑排序

    ##### 概念

    拓扑排序针对于有向无环图(DAG)。

    每一个节点在进行拓扑排序后会先于所有它能到达的点。

    这样似乎不好理解，用一个简单的图排序一遍就懂了。

    <svg id="mermaidChart0" width="100%" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="max-width: 262.875px; margin: auto;" viewBox="-8 -9.3125 262.875 117.88671875" role="graphics-document document" aria-roledescription="flowchart-v2"><style>#mermaidChart0{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;fill:#ccc;}#mermaidChart0 .error-icon{fill:#a44141;}#mermaidChart0 .error-text{fill:#ddd;stroke:#ddd;}#mermaidChart0 .edge-thickness-normal{stroke-width:2px;}#mermaidChart0 .edge-thickness-thick{stroke-width:3.5px;}#mermaidChart0 .edge-pattern-solid{stroke-dasharray:0;}#mermaidChart0 .edge-pattern-dashed{stroke-dasharray:3;}#mermaidChart0 .edge-pattern-dotted{stroke-dasharray:2;}#mermaidChart0 .marker{fill:lightgrey;stroke:lightgrey;}#mermaidChart0 .marker.cross{stroke:lightgrey;}#mermaidChart0 svg{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;}#mermaidChart0 .label{font-family:"trebuchet ms",verdana,arial,sans-serif;color:#ccc;}#mermaidChart0 .cluster-label text{fill:#F9FFFE;}#mermaidChart0 .cluster-label span,#mermaidChart0 p{color:#F9FFFE;}#mermaidChart0 .label text,#mermaidChart0 span,#mermaidChart0 p{fill:#ccc;color:#ccc;}#mermaidChart0 .node rect,#mermaidChart0 .node circle,#mermaidChart0 .node ellipse,#mermaidChart0 .node polygon,#mermaidChart0 .node path{fill:#1f2020;stroke:#81B1DB;stroke-width:1px;}#mermaidChart0 .flowchart-label text{text-anchor:middle;}#mermaidChart0 .node .label{text-align:center;}#mermaidChart0 .node.clickable{cursor:pointer;}#mermaidChart0 .arrowheadPath{fill:lightgrey;}#mermaidChart0 .edgePath .path{stroke:lightgrey;stroke-width:2.0px;}#mermaidChart0 .flowchart-link{stroke:lightgrey;fill:none;}#mermaidChart0 .edgeLabel{background-color:hsl(0, 0%, 34.4117647059%);text-align:center;}#mermaidChart0 .edgeLabel rect{opacity:0.5;background-color:hsl(0, 0%, 34.4117647059%);fill:hsl(0, 0%, 34.4117647059%);}#mermaidChart0 .labelBkg{background-color:rgba(87.75, 87.75, 87.75, 0.5);}#mermaidChart0 .cluster rect{fill:hsl(180, 1.5873015873%, 28.3529411765%);stroke:rgba(255, 255, 255, 0.25);stroke-width:1px;}#mermaidChart0 .cluster text{fill:#F9FFFE;}#mermaidChart0 .cluster span,#mermaidChart0 p{color:#F9FFFE;}#mermaidChart0 div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:12px;background:hsl(20, 1.5873015873%, 12.3529411765%);border:1px solid rgba(255, 255, 255, 0.25);border-radius:2px;pointer-events:none;z-index:100;}#mermaidChart0 .flowchartTitleText{text-anchor:middle;font-size:18px;fill:#ccc;}#mermaidChart0 :root{--mermaid-alt-font-family:sans-serif;}</style><g><marker id="mermaidChart0_flowchart-pointEnd" class="marker flowchart" viewBox="0 0 10 10" refX="6" refY="5" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker><marker id="mermaidChart0_flowchart-pointStart" class="marker flowchart" viewBox="0 0 10 10" refX="4.5" refY="5" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" orient="auto"><path d="M 0 5 L 10 10 L 10 0 z" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker><marker id="mermaidChart0_flowchart-circleEnd" class="marker flowchart" viewBox="0 0 10 10" refX="11" refY="5" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><circle cx="5" cy="5" r="5" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></circle></marker><marker id="mermaidChart0_flowchart-circleStart" class="marker flowchart" viewBox="0 0 10 10" refX="-1" refY="5" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><circle cx="5" cy="5" r="5" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></circle></marker><marker id="mermaidChart0_flowchart-crossEnd" class="marker cross flowchart" viewBox="0 0 11 11" refX="12" refY="5.2" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><path d="M 1,1 l 9,9 M 10,1 l -9,9" class="arrowMarkerPath" style="stroke-width: 2; stroke-dasharray: 1, 0;"></path></marker><marker id="mermaidChart0_flowchart-crossStart" class="marker cross flowchart" viewBox="0 0 11 11" refX="-1" refY="5.2" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><path d="M 1,1 l 9,9 M 10,1 l -9,9" class="arrowMarkerPath" style="stroke-width: 2; stroke-dasharray: 1, 0;"></path></marker><g class="root"><g class="clusters"></g><g class="edgePaths"><path d="M20.844,58.286L49.438,86.977L69.138,86.977" id="L-A-B-0" class=" edge-thickness-normal edge-pattern-solid flowchart-link LS-A LE-B" style="fill:none;" marker-end="url(#mermaidChart0_flowchart-pointEnd)"></path><path d="M20.844,40.976L49.438,12.285L86.465,12.285L123.492,12.285L143.313,12.285" id="L-A-C-0" class=" edge-thickness-normal edge-pattern-solid flowchart-link LS-A LE-C" style="fill:none;" marker-end="url(#mermaidChart0_flowchart-pointEnd)"></path><path d="M98.492,86.977L123.492,86.977L143.192,86.977" id="L-B-D-0" class=" edge-thickness-normal edge-pattern-solid flowchart-link LS-B LE-D" style="fill:none;" marker-end="url(#mermaidChart0_flowchart-pointEnd)"></path><path d="M173.184,12.285L198.305,12.285L223.101,37.459" id="L-C-E-0" class=" edge-thickness-normal edge-pattern-solid flowchart-link LS-C LE-E" style="fill:none;" marker-end="url(#mermaidChart0_flowchart-pointEnd)"></path><path d="M173.305,86.977L198.305,86.977L223.101,61.803" id="L-D-E-0" class=" edge-thickness-normal edge-pattern-solid flowchart-link LS-D LE-E" style="fill:none;" marker-end="url(#mermaidChart0_flowchart-pointEnd)"></path></g><g class="edgeLabels"><g class="edgeLabel"><g class="label" transform="translate(0, 0)"><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="edgeLabel"></span></div></foreignObject></g></g><g class="edgeLabel"><g class="label" transform="translate(0, 0)"><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="edgeLabel"></span></div></foreignObject></g></g><g class="edgeLabel"><g class="label" transform="translate(0, 0)"><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="edgeLabel"></span></div></foreignObject></g></g><g class="edgeLabel"><g class="label" transform="translate(0, 0)"><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="edgeLabel"></span></div></foreignObject></g></g><g class="edgeLabel"><g class="label" transform="translate(0, 0)"><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="edgeLabel"></span></div></foreignObject></g></g></g><g class="nodes"><g class="node default default flowchart-label" id="flowchart-A-0" transform="translate(12.21875, 49.630859375)"><circle style="" rx="0" ry="0" r="12.21875" width="24.4375" height="42.1953125"></circle><g class="label" style="" transform="translate(-4.71875, -13.59765625)"><rect></rect><foreignObject width="9.4375" height="27.1953125"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="nodeLabel">A</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-B-1" transform="translate(86.46484375, 86.9765625)"><circle style="" rx="0" ry="0" r="12.02734375" width="24.0546875" height="42.1953125"></circle><g class="label" style="" transform="translate(-4.52734375, -13.59765625)"><rect></rect><foreignObject width="9.0546875" height="27.1953125"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="nodeLabel">B</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-C-2" transform="translate(160.8984375, 12.28515625)"><circle style="" rx="0" ry="0" r="12.28515625" width="24.5703125" height="42.1953125"></circle><g class="label" style="" transform="translate(-4.78515625, -13.59765625)"><rect></rect><foreignObject width="9.5703125" height="27.1953125"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="nodeLabel">C</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-D-3" transform="translate(160.8984375, 86.9765625)"><circle style="" rx="0" ry="0" r="12.40625" width="24.8125" height="42.1953125"></circle><g class="label" style="" transform="translate(-4.90625, -13.59765625)"><rect></rect><foreignObject width="9.8125" height="27.1953125"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="nodeLabel">D</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-E-4" transform="translate(235.08984375, 49.630859375)"><circle style="" rx="0" ry="0" r="11.78515625" width="23.5703125" height="42.1953125"></circle><g class="label" style="" transform="translate(-4.28515625, -13.59765625)"><rect></rect><foreignObject width="8.5703125" height="27.1953125"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span class="nodeLabel">E</span></div></foreignObject></g></g></g></g></g></svg>

    

    对于上面这幅图：

    * A->B->C->D->E
    * A->B->D->C->E
    * A->C->B->D->E
    * ...

    都是这幅图的拓扑排序结果，当然，在很多时候会要求你输出字典序最小的情况。

    ##### 思路

    要实现拓扑排序，我们发现，第一个节点的入度为 $0$，而删去第一个节点后，第二个节点入读仍然为 $0$。

    它的大概逻辑就是：

    1. 找到所有入度为 $0$ 的节点，并加入答案数组
    2. 删去入度为 $0$ 的节点，并更新其它节点的入度
    3. 反复 1、2 步，直到没有节点

    {% mermaid %}
    graph LR
    
    A((A))
    B((B))
    C((C))
    D((D))
    E((E))
    
    A-->B
    A-->C
    B-->D
    C-->E
    D-->E
    {% endmermaid %}

    {% mermaid %}
    graph LR
    
    A((1))
    B((B))
    C((C))
    D((D))
    E((E))
    
    A-.->B
    A-.->C
    B-->D
    C-->E
    D-->E
    {% endmermaid %}

    {% mermaid %}
    graph LR
    
    A((1))
    B((2))
    C((3))
    D((D))
    E((E))
    
    A-.->B
    A-.->C
    B-.->D
    C-.->E
    D-->E
    {% endmermaid %}

    {% mermaid %}
    graph LR
    
    A((1))
    B((2))
    C((3))
    D((4))
    E((E))
    
    A-.->B
    A-.->C
    B-.->D
    C-.->E
    D-.->E
    {% endmermaid %}

    

    ##### 实现

    ```c++
    #include <bits/stdc++.h>
    using namespace std;
    
    int n,m;
    vector<int> mp[100005];//使用邻接表存图
    map<int,int> in;
    vector<int> ans;
    
    int main()
    {
        cin>>n>>m;
        for(int i=1;i<=m;i++)
        {
            int u,v;
            cin>>u>>v;
            mp[u].push_back(v);//表示 u 有一条指向 v 的边
            in[v]++;//统计入度
        }
        queue<int> q;//存储当前所有入度为 0 的点
        for(int i=1;i<=n;i++)
        {
            if(in[i]==0)//如果入度为 0
                q.push(i);//加入队列
        }
        while(!q.empty())
        {
            int t=q.front();
            q.pop();
            ans.push_back(t);//将 t 加入答案数组
            for(int i=0;i<mp[t].size();i++)
            {
                in[mp[t][i]]--;//t 指向的所有节点入度减一
                if(in[mp[t][i]]==0)//如果入度为 0
                    q.push(mp[t][i]);//加入队列
            }
        }
        for(int i=0;i<ans.size();i++)
            cout<<ans[i]<<" ";
        return 0;
    }
    ```

* #### 最短路

    ##### 概念

    字面意思，最短路指的是从一个点到达另一个点的最短路径

    ##### 思路

    这里讲解 Dijkstra 算法。

    这个算法运用到了一个贪心的思想，即走到当前节点时路径最优。走到这个节点时，我们去遍历所有下一个节点，如果从这个节点走过去比原来的路径短的话，就更新。当然，一开始都得赋值为极大值。

    ##### 代码

    由于是图论基础，不展示（（（~~没写出来用vector的，一个邻接矩阵一个前向星~~