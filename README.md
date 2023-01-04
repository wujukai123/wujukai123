# README.md (Luogu.com.cn) ZH_CN
# wujukai123


## 置顶信息
### 团队
团队已建成，欢迎加入：[编程蒟蒻游乐场](https://www.luogu.com.cn/team/53107)

> 转团队公告：
>
> 团队题目更新了！一共六道题，都很水！大家赶紧把它们AC掉！
### 自制主题（自用）
典雅黑：https://www.luogu.com.cn/theme/design/85434

伸手不见五指：https://www.luogu.com.cn/theme/design/86300

紫色梦呓：https://www.luogu.com.cn/theme/design/86301

CTJ被抓：https://www.luogu.com.cn/theme/design/86680
### 大事祭
- 2022/4/7 开始刷第一题祭
- 2022/9/12 提交 100 次祭
- 2022/9/29 AC 100 题祭
- 2022/10/18 提交 200 次祭
- 2022/10/23 AC 200 题祭
- 2022/11/1 提交 300 次祭
- 2022/11/21 洛谷升为蓝名祭
- 2022/11/20 AC 100 道入门题祭
- 2022/11/23 AC 100 道普及-题祭
- 2022/11/24 提交 400 次祭
- 2022/11/24 AC 300 题祭
- 2022/11/28 提交 500 次祭
- 2022/12/1 AC 400 题祭
- 2022/12/3 AC 200 道入门题祭
- 2022/12/5 洛谷升为绿名祭
- 2022/12/5 提交 600 次祭
- 2022/12/8 提交 700 次祭
- 2022/12/8 AC 500 题祭
- 2022/12/11 提交 800 次祭
- 2022/12/14 AC 200 道普及-题祭
- 2022/12/15 AC 600 题祭
- 2022/12/16 AC 100 道普及/提高-题祭
- 2022/12/17 提交 900 次祭
- 2022/12/22 AC 300 道入门题祭
- 2022/12/29 提交 1k 次祭
- 2022/12/30 AC 700 题祭
### 个人洛谷信息
![我的练习情况](https://luogu.wao3.cn/api/practice?id=712378)

![我的练习情况](https://luogu.wao3.cn/api/guzhi?id=712378&scores=100,21,0,0,0)
## 重要信息
### 我的谷友们（均已互关）
![](https://cdn.luogu.com.cn/upload/image_hosting/y107pj78.png?x-oss-process=image/resize,m_lfit,h_680,w_900)
## 个人信息
### 姓名
*钜铠
### 网名
wujukai123
（备用：wujukai188、wjk188、wjk123）
### 机型
1. MacBook Air 6,2 (13-inch,  2013) + macOS Ventura 13.1 Beta (OpenCore Legacy Patcher supports) + 250.79 GB File Storage + Intel Core i5 Dual-Core 1.3 GHz + 8GB 1600 MHz DDR3 + Intel HD Graphics 6000 1536MB
（现在已废）
2. MacBook Air 7,1 (13-inch, 2017) + macOS Monterey 12.6.2 + 121.12 GB File Storage + Intel Core i5 Dual-Core 1.8 GHz + 8GB 1600 Mhz DDR3 + Intel HD Graphics 6000 1536MB（现在主要使用）
### 性别
男
### 社交网站
个人洛谷（已升为绿名）：[wujukai123 的个人中心](https://www.luogu.com.cn/user/712378)

个人洛谷博客：还没写什么内容 [文章列表 - wujukai123 的博客 - 洛谷博客](https://www.luogu.com.cn/blog/wujukai123/)

GitHub：一堆啥也不是的东西 [wujukai123 (Kevin Woo)](https://github.com/wujukai123)

Gitee：一堆没用的烂玩意，已彻底停更 [Wu Jukai (wujukai123) - Gitee.com](https://gitee.com/wujukai123)

CSDN：已停止更新，有170篇文章 [钜铠的博客_CSDN博客-macOS,网络,后端领域博主](https://blog.csdn.net/weixin_59197425?spm=1018.2118.3001.5148)

个人网站：正在建设 

[wujukai.com](https://wujukai.com)

[wjk188.wordpress.com](https://wjk188.wordpress.com)

### 码风
应该比较好看吧。。。
```cpp
#include <iostream>
#include <queue>
#include <map>
using namespace std;

string e;

struct node {
	string x, path;
	int y;
};

queue<node> q;
map<string, bool> vis;

string A(string x) {
	swap(x[0], x[7]);
	swap(x[1], x[6]);
	swap(x[2], x[5]);
	swap(x[3], x[4]);
	return x;
}

string B(string x) {
	char t = x[3];
	x[3] = x[2];
	x[2] = x[1];
	x[1] = x[0];
	x[0] = t;
	t = x[4];
	x[4] = x[5];
	x[5] = x[6];
	x[6] = x[7];
	x[7] = t;
	return x;
}

string C(string x) {
	char t = x[6];
	x[6] = x[5];
	x[5] = x[2];
	x[2] = x[1];
	x[1] = t;
	return x;
}

void bfs() {
	q.push(node{"12345678", "", 0});
	vis["12345678"] = true;
	while (!q.empty()) {
		string x = q.front().x, path = q.front().path;
		int y = q.front().y;
		q.pop();
		if (x == e) {
			cout << y << endl;
			cout << path << endl;
			return ;
		}
		string t = A(x);
		if (!vis[t]) {
			q.push(node{t, path + "A", y + 1});
			vis[t] = true;
		}
		t = B(x);
		if (!vis[t]) {
			q.push(node{t, path + "B", y + 1});
			vis[t] = true;
		}
		t = C(x);
		if (!vis[t]) {
			q.push(node{t, path + "C", y + 1});
			vis[t] = true;
		}
	}
}

int main() {
	for (int i = 1; i <= 8; i++) {
		char t;
		cin >> t;
		e += t;
	}
	bfs();
	return 0;
}
```
 
 
