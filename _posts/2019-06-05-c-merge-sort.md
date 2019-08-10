---
layout: post
title: 归并排序(C语言描述)
tags: algorithm
categories: C语言
---

归并排序所体现的思想是分治，将大问题分解成小问题，并逐一求解，最后得出解。该算法将一个数组分为两个子数组，而后两个子数组进行比较，通过对索引的操作来完成。 <br/>
最差时间复杂度:O(nlogn) <br/>
最优时间复杂度:O(nlogn) <br/>
平均时间复杂度:O(nlogn) <br/>
所需辅助空间:O(n) <br/>
稳定性:稳定 <br/>
<hr>

~~~c++
/*归并排序.c*/
#include <stdio.h>
#include <stdlib.h>

void Merge(int *, int, int, int);
void MergeSort(int *, int,int);

int main()
{
	int n, i;
	int num[1000];
	
	scanf ("%d",&n);
	for (i = 0; i < n; i++)
	scanf ("%d",num + i);
	
	MergeSort(num, 0, n - 1);
	
	for (i = 0; i < n; i++)
	{
	printf ("%7d",*(num + i));
	}
	return 0;
}
	
void Merge(int * p, int left, int mid, int right)
{
	int len = right - left + 1, k;
	int i = left, j = mid + 1;
	int index = 0;
	int * temp = (int *)malloc(sizeof(int) * len);
	
	while (i <= mid && j <= right)
	{
		temp[index++] = p[i] <= p[j]?p[i++]:p[j++];
	}
	while (i <= mid)
	{
		temp[index++] = p[i++];
	}
	while (j <= right)
	{
		temp[index++]=p[j++];
	}
	
	for (k = 0; k < len; k++)
	{
		p[left++] = temp[k];
	}
	
	free(temp);
}

void MergeSort(int * p,int left,int right)
{
	if (left == right)
	return ;
	
	int mid=(left + right) / 2;
	
	MergeSort(p, left, mid);
	MergeSort(p, mid + 1, right);
	
	Merge(p, left, mid, right);
}
~~~
