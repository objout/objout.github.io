---
layout: post
title: 快速排序
tags: algorithm
categories: C语言
---

### 快速排序
<hr>
1. 是由东尼·霍尔所发展的一种排序算法。
2. 在平均状况下，排序n个元素要O(nlogn)次比较。
3. 在最坏状况下则需要O(n<sup>2</sup>)次比较，但这种状况并不常见。
4. 事实上，快速排序通常明显比其他O(nlogn)算法更快，因为它的内部循环可以在大部分的架构上很有效率地被实现出来。

5. 快速排序使用分治策略(Divide and Conquer)来把一个序列分为两个子序列。步骤为：
从序列中挑出一个元素，作为"基准"(pivot).把所有比基准值小的元素放在基准前面，
所有比基准值大的元素放在基准的后面（相同的数可以到任一边），这个称为分区(partition)操作。
6. 分类 -----内部比较排序
7. 数据结构 ---- 数组
8. 最差时间复杂度 ----O(n<sup>2</sup>)
9. 最优时间复杂度 ---- 每次选取的基准都是中位数，这样每次都均匀的划分出两个分区，只需要logn次划分就能结束递归，时间复杂度为O(nlogn)
10. 平均时间复杂度 ---- O(nlogn)
11. 所需辅助空间 ------ 主要是递归造成的栈空间的使用(用来保存left和right等局部变量)，取决于递归树的深度，一般为O(logn)，最差为O(n)
12. 稳定性 ---------- 不稳定
<hr>

~~~c++
/*快速排序.c*/
//C语言实现
#include <stdio.h>

void Swap(int A[], int i, int j)
{
    int temp = A[i];
    A[i] = A[j];
    A[j] = temp;
}

int Partition(int A[], int left, int right)  // 划分函数
{
    int pivot = A[right];               // 这里每次都选择最后一个元素作为基准
    int tail = left - 1;                // tail为小于基准的子数组最后一个元素的索引
    for (int i = left; i < right; i++)  // 遍历基准以外的其他元素
    {
        if (A[i] <= pivot)              // 把小于等于基准的元素放到前一个子数组末尾
        {
            Swap(A, ++tail, i);
        }
    }
    Swap(A, tail + 1, right);           // 最后把基准放到前一个子数组的后边，剩下的子数组既是大于基准的子数组
                                        // 该操作很有可能把后面元素的稳定性打乱，所以快速排序是不稳定的排序算法
    return tail + 1;                    // 返回基准的索引
}

void QuickSort(int A[], int left, int right)
{
    if (left >= right)
        return;
    int pivot_index = Partition(A, left, right); // 基准的索引
    QuickSort(A, left, pivot_index - 1);
    QuickSort(A, pivot_index + 1, right);
}

int main()
{
    int A[]={ 5, 2, 9, 4,7,6,1, 3, 8 };
    int n = sizeof(A) / sizeof(int);
    QuickSort(A, 0, n - 1);
    printf("快速排序结果：\n");
    for (int i = 0; i < n; ++i)
    {
        printf("%d ", A[i]);
    }
    printf("\n");
    return 0;
}

/*迭代法实现*/
typedef struct _Range 
{
    int start, end;
} Range;
Range new_Range(int s, int e)
{
    Range r;
    r.start = s;
    r.end = e;
    return r;
}
void swap(int *x, int *y) 
{
    int t = *x;
    *x = *y;
    *y = t;
}
void quick_sort(int arr[], const int len) 
{
    if (len = range.end)
            continue;
        int mid = arr[(range.start + range.end) / 2];
        int left = range.start, right = range.end;
        do
        {
            while (arr[left]  mid)
            --right;
 
            if (left <= right)
            {
            swap(&arr[left],&arr[right]);
                left++;
                right--;
            }
        } while (left <= right);
 
        if (range.start  left) 
        r[p++] = new_Range(left, range.end);
    }
}
~~~