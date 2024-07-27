
#### HW3-3:求第k小的数

```c++
#include <iostream>
#include<cmath>
#include <algorithm>
using namespace std;

int n;

void qsort(int *x,int l, int r,int k)
{
	int i = l, j = r, mid = x[(l + r) / 2];
	do
	{
		while (x[j] < mid)
			j--;
		while (x[i] > mid)
			i++;
		if (i <= j)
		{
			swap(x[i], x[j]);
			i++;
			j--;
		}
	} while (i <= j);
	//快排后数组被划分为三块： l<=j<=i<=r
	if (k <= j) qsort(x,l, j,k);//在左区间只需要搜左区间
	else if (i <= k) qsort(x,i, r,k);//在右区间只需要搜右区间
	else //如果在中间区间直接输出
	{
		printf("%d", x[j + 1]);
	}
}

int main()
{
	int k;
	cin >> n;
	cin >> k;
	int *target=new int[n];
	for (int i = 0; i < n; i++) {
		scanf("%d", &target[i]);
	}
	qsort(target, 0, n-1,k);
	return 0;
}
```
