---
title: 2023 ZJ noip 迷惑行为大赏
categories: 整活
tags:
  - 整活
  - ZJ
  - NOIp
  - 整活大赏
  - 统计
abbrlink: ffca3de1
date: 2023-12-05 23:42:04
---
## 前言

如果您不愿意展示自己的代码，可以申请撤下您的代码。

如果上述代码中存在个人信息泄露情况，请立即联系作者。

代码来源：

{% link 浙江省 NOIP 2023 考生代码, http://www.cs.zju.edu.cn/csen/2023/1118/c62747a2828209/page.htm %}

## 正文
### 统计
共 $788$ 人，$3404$ 份文件，平均每入约 $4.319797$ 份文件

其中：
* `114514` 出现 $114$ 次（臭
* `1919810` 出现 $26$ 次
* `AC` 出现 $26$ 次
* `ccf` 出现 $45$ 次
* `noi` 出现 $35$ 次
* `csp` 出现 $11$ 次
* `orz` 出现 $47$ 次
* `qwq` 出现 $212$ 次
* `rp` 出现 $160$ 次
* `rp++` 出现 $27$ 次
* `system` 出现 $243$ 次
* `define` 出现 $4315$ 次
* `rand` 出现 $400$ 次
* $57$ 人注释了文件操作
* $63$ 人写了对拍

### 空间第一：ZJ-0184
本场重量级

共 ${44.9 MB}$

一人霸占 ${\frac{9}{10}}$
![wiztree空间](https://cdn.luogu.com.cn/upload/image_hosting/spag3tqv.png)
死因：[玄学文件](https://www.wenshushu.cn/f/cp628pnzxso/folder/cp61txk7ent)

### 一、白给型

ZJ-0595:

逆行+听天由命+《消失的分号》+有头无尾
```cpp
#include<bits/stdc++.h>
using namespace std;
int n,m;
int main(){
	freopen("tribool.in","r",stdin);
	freopen("tribool.out","w",stdin);
	srand(time(NULL))
	cin>>n>>m;
	for(int i=1;i<=m;i++)printf("%d\n",rand()%500+1);
}
```
ZJ-0498:
```cpp
#include<bits/stdc++.h>
using namespace std;

signed main(){
	freopen("run.in","r",stdin);
	freopen("run.out","w",stdout);
	//ru guo ni yao ba ta jia ru mi huo xing wei da shang , jian yi xian si xin wo ,xie xie.
	ios::sync_with_stdio(false);
	cin.tie(0);
	cout.tie(0);
	cout<<"Life isn't always easy.";
	cout<<"I'm Aslf_Ek.";
	cout<<"Goodbye,OI";
	cout<<"Maybe I should get out and find my own life.";
	cout<<"UID 175719";
	cout<<"I have too much to say,but I said before.";
	cout<<"Everything is like OI ,isn't it ?";
	cout<<"I once falling love with a girl,";
	cout<<"but,like OI ,she left me alone.";
	cout<<"I like those memories.";
	cout<<"Hope the it like me,too.";
	cout<<"there's still a long way to go.";
	cout<<"For me ,for my dream.";
	
	cout<<"I remember the words I said,";
	
	cout<<" Its not the dream,it's the destiny ";
	
	cout<<"Today,I'm away from OI";
	cout<<"I don't know how much things I will lose.";
	cout<<"but what I only have to do is just chase,and lose,chase,and lose.";
	
	
	
	
	cout<<"It's my life.";
	
	
	
	return 0;
}
```
### 二、~~暴厌语言~~友好问候
ZJ-0496:
```cpp
/*

fuck ccf
fuck noip
fuck csp

我不干了

还有一个小时考试结束 

看我光速退役

*/
```
```cpp
int fuck_ccf()
{
	scanf("%d%d%d%d",&n,&m,&k,&d);
	ll ans=0;
	for(int i=1;i<=m;i++)
	{
		int x,y;ll v;
		scanf("%d%d%lld",&x,&y,&v);
		ans=max(ans,ans-y*d+v);
	}
	printf("%lld\n",ans);
	return 0;
}
```
### 三、ccf庇佑
ZJ-0558:
```cpp
//    ------ ------ ------
//    --     --     --
//    --     --     ------
//    --     --     --
//    ------ ------ --
//    
//
//
//    --  -- ------ --     ------  --  -- ------ 
//    --  -- --     --     --  --  - -- - --    
//    ------ ------ --     ------  - -- - ------
//    --  -- --     --     --      - -- - --    
//    --  -- ------ ------ --      - -- - ------ 
```
ZJ-0220:
```cpp
int main(){
	freopen("run.in","r",stdin);
	freopen("run.out","w",stdout);
//	I love CCF(^_^)
	return 0;
}
```
ZJ-0245:
```cpp
//I would appreciate it if CCF cound give me 1=
```
ZJ-0266:
```cpp
			std::cout << 0 << std::endl;
			// I know I can't solve a so difficult problem like this
			// so can you give me 45 pts?
			// please! I thank you ccf !!!
```
ZJ-0285:
```cpp
/*
I love CCF
chu le t3 mei gei duo shao fen
qi ta ti bu fen fen dou hao duo!!!
*/
```
### 四、诈骗
ZJ-0608:
```cpp
//100pts......?
//I don't know
//**** ***
//never gonna give you up
//sto ccf orz
```
ZJ-0266~~怎么还是他~~的小作文:

```cpp
/*
Oh, I'm so bored (12: 30)
I'm a junior high school student 
I used to think I will AFO after taking 1=
but I think I will be more and more confident
and also be more and more strong
we should fight fight fight, without stopping

Never gonna give you up~
Never gonna let you down~

rp++ rp++
#define int long long
](
using namespace std;
//freopen
*/
```
### 五、玄学
ZJ-0085:
什么都写了，又好像什么都没写
```cpp
#include<cstdio>
#include<iostream>
#define ll long long
#define ull unsigned ll
#define Tp template<typename _T>
Tp _T mabs(_T x){ return x<0?-x:x; }
Tp _T mmin(_T x,_T y){ return x<y?x:y; }
Tp _T mmax(_T x,_T y){ return x<y?y:x; }
Tp void mswap(_T &x,_T &y){ _T t=x; x=y; y=t; return; }
using namespace std;
#define maxn

int main(){
	//freopen(".in","r",stdin);
	//freopen(".out","w",stdout);
	cin.tie(0); cout.tie(0); ios::sync_with_stdio(0);
	
	return 0;
}
```
ZJ-0023:
对怕写错位置
```cpp
#include<bits/stdc++.h>
using namespace std;
#define rep(i,j,k) for(int i=(j),i##_=(k);i<=i##_;i++)
#define per(i,j,k) for(int i=(j),i##_=(k);i>=i##_;i--)
#define ckmn(i,j) (i=min(i,j))
#define ckmx(i,j) (i=max(i,j))
#define fir first
#define sec second
#define mkp make_pair
#define eb emplace_back
#define pb push_back
typedef long long ll;
typedef long double db;
#define siz(i) ((int)(i).size())
#define all(i) (i).begin(),(i).end()
// #define int ll
typedef vector<int> vi;
typedef pair<int,int> pi;
signed main(){ios::sync_with_stdio(false),cin.tie(nullptr);
    system(("g++ run.cpp -O2 -Dsuper -Wall -Wextra -Wshadow -o run"));
    system(("g++ run_bf.cpp -O2 -Dsuper -Wall -Wextra -Wshadow -o run_bf"));
    system(("g++ make.cpp -O2 -Dsuper -Wall -Wextra -Wshadow -o make"));
    while(1){
        system(("./make > qwq.in"));
        system(("./run < qwq.in > 1.out"));
        system(("./run_bf < qwq.in > 2.out"));
        if(system(("diff 1.out 2.out -b"))) break;
    }
return 0;}
```
### 六、原p
ZJ-0423:
```cpp
//		if (3==tt){
//			cout<<"yuanshen";
//			fo(i,1,n) cout<<char(x[i]);
//			cout<<endl;
//			cout<<"qidong";
//			fo(i,1,n) cout<<char(t[i]);
//			cout<<endl;
//		}
```
### 七、~~小黑子~~真爱粉
ZJ-0467:
```cpp
struct ngm{
	int to,nxt,z;
}e[100001];
```
ZJ-0285:
```cpp
#include<bits/stdc++.h>
#define int long long
using namespace std;
int dian,T,n,m,ans,kun,d,i,x,y,z,tree[1010][1010],dp[1010][1010],j;
int lowbit(int x){return x&-x;}
void add(int x,int y,int z){
	for(;y<=n;y+=lowbit(y))
		tree[x][y]+=z;
}
int da(int x,int y){
	int sum=0;
	for(;y;y-=lowbit(y))
		sum=sum+tree[x][y];
	return sum;
}
signed main(){
	freopen("run.in","r",stdin);
	freopen("run.out","w",stdout);
	cin>>dian>>T;
	if(dian==17||dian==18){
		while(T--){
			cin>>n>>m>>kun>>d;ans=0;
			for(i=1;i<=m;i++){
				cin>>x>>y>>z;
				if(y>kun||y>x)continue;
				if(z>y*d)ans=ans+z-y*d;
			}
			cout<<ans<<'\n';
		}
		return 0;
	}
	while(T--){
		cin>>n>>m>>kun>>d;
		for(i=1;i<=n;i++)
			for(j=0;j<=n;j++)
				tree[i][j]=0;
		for(i=1;i<=m;i++){
			cin>>x>>y>>z;
			add(x,y,z);
		}
		for(i=0;i<=n;i++)
			for(j=0;j<=kun;j++)
				dp[i][j]=-1e18;
		dp[0][0]=0;
		for(i=1;i<=n;i++){
			for(j=0;j<=min(i-1,kun);j++)
				dp[i][0]=max(dp[i][0],dp[i-1][j]);
			for(j=1;j<=min(kun,i);j++)
				dp[i][j]=dp[i-1][j-1]+da(i,j)-d;
		}
		ans=0;
		for(j=0;j<=min(n,kun);j++)
			ans=max(ans,dp[n][j]);
		cout<<ans<<'\n';
	}
	return 0;
}
```
### 八、游记
ZJ-0364:
```cpp
// 题记: 老骥伏枥, 志在千里
// 11:41 前两题 如 过了, 来水一下
// 其实l₀是几并不重要
// 只要有一个较短的满足条件即可输出1
// 对前缀DP
// 但是居然要考虑最末尾
// 12:06 ... 遗憾的, 不会写暴力
// 最优策略一定是数字间互相对应
// 不会有一个数字被分成两段
// 12:12 两序列最末端的数字一定会在一起
// 所以结果的相对大小关系与最末端数字相同
// 强制让a > b
// 12：36 啊, 台昆南拉
// 测试点应该是没有捆测, 这点我相信西西弗
// 骗到5分, 险些失手
```
