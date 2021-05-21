

## 分发饼干0521

LeetCode455.分发饼干

**题目描述**
有一群孩子和一堆饼干，每个孩子有一个饥饿度，每个饼干都有一个大小。每个孩子只能吃
最多一个饼干，且只有饼干的大小大于孩子的饥饿度时，这个孩子才能吃饱。求解最多有多少孩子可以吃饱。

**输入输出样例**
输入两个数组，分别代表孩子的饥饿度和饼干的大小。输出最多有多少孩子可以吃饱的数
量。

```
Input: [1,2], [1,2,3]
Output: 2
```



**解题思路**

贪心。对孩子饥饿度和饼干尺寸从小到大排序，然后逐一比较，满足条件就算一个孩子

**代码实现**

```c++
#include<iostream>
#include <vector>
#include<algorithm>
using namespace std;
int findContentChildren(vector<int>& children, vector<int>& cookies) {
	sort(children.begin(), children.end());
	sort(cookies.begin(), cookies.end());
	int child = 0, cookie = 0;
	/*
	* 举例：[1,2],[1,2,3]
	* 可以划分为[1,2],[1,3],[2,3],后两个中，因为不重复，所以是，[1,2],[2,3]这两种
	*/
	while (child < children.size() && cookie < cookies.size()) {
		if (children[child] <= cookies[cookie]) 
			++child;
		++cookie;
	}
	return child;
}


int main() {
	int a[] = { 1,2 };
	int b[] = { 1,2,3 };
	//构建vector，批量插入元素
	vector<int> children(a, a + sizeof(a) / sizeof(a[0]));
	vector<int> cookies(b, b + sizeof(b) / sizeof(b[0]));

	cout << findContentChildren(children, cookies) << endl;

	system("pause");
	return 0;
}
```





