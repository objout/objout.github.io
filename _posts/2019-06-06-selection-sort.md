---
layout: post
title: 选择排序
tags: algorithm
categories: C语言
---

### 选择排序
<hr>
1. 在序列中找到最小或最大元素，放到序列的起始位置作为已排序序列,再从剩余元素中寻找，放到已排列序列的末尾。
2. 最差时间复杂度:O(n<sup>2</sup>)
3. 最优时间复杂度:O(n<sup>2</sup>)
4. 平均时间复杂度:O(n<sup>2</sup>)
5. 所需辅助空间:O(1)
6. 稳定性:不稳定
<hr>


~~~c++
/*选择排序.c*/
#include <stdio.h>
#include <stdlib.h>

void SelectionSort(int *,int n);

int main()
{
	int n,i;
	int num[1000];

	scanf("%d",&n);
	for (i = 0; i < n; i++)
	scanf("%d",num + i);
	
	SelectionSort(num, n);

	for (i = 0; i < n; i++)
	printf("%d ",*(num + i));
	return 0;
}
	
void SelectionSort(int * p,int n)
{
	int i,j;
	for (i = 0; i < n - 1; i++)
	{
		for (j = i + 1;j < n; j++)
		{
			if (p[i] >= p[j])
			{
			int temp = p[i];
			p[i] = p[j];
			p[j] = temp;
			}
		}
	}
}
~~~