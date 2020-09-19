---
layout: post
date: 2020-06-15 10:11
title:  "Sorting Code In Java"
description: Basic information about the Sorting Algorithm.
comments: true
category: 
- docs
- help
tags:
- documentation
- sort
- java
---

Markdown (or Textile), Liquid, HTML & CSS go in. Static sites come out ready for deployment.

# sort algorithm in java

## Bubble sort
{% highlight ruby linenos %}
public static void bubblesort(int[] array){
	boolean sorted = false;
	int temp;
	while(!sorted){
		sorted = true;
		for(int i = 0; i < array.length - 1; i++){
			if(array[i] > array[i+1]){
				temp = array[i];
				array[i] = array[i+1];
				array[i+1] = temp;
				sorted = false;
			}
		}
	}
} 
{% endhighlight %}
<!--more-->
## Insertion Sort
{% highlight ruby linenos %}
public static void insertionsort(int[] array){
	for(int i =0; i < array.length; i++){
		int current = array[i];
		int j = i-1;
		while(j >= 0; current < array[j]){
			array[j+1] = array[j];
			j--;
		}
		array[j+1] = current;
	}
}
{% endhighlight %}

## Selection Sort


## Merge Sort
{% highlight ruby linenos %}
  public static void merge(int[] left_arr,int[] right_arr, int[] arr,int left_size, int right_size){
      
      int i=0,l=0,r = 0;
      //The while loops check the conditions for merging
      while(l<left_size && r<right_size){
          
          if(left_arr[l]<right_arr[r]){
              arr[i++] = left_arr[l++];
          }
          else{
              arr[i++] = right_arr[r++];
          }
      }
      while(l<left_size){
          arr[i++] = left_arr[l++];
      }
      while(r<right_size){
        arr[i++] = right_arr[r++];
      }
  }

  public static void mergeSort(int [] arr, int len){
      if (len < 2){return;}
      
      int mid = len / 2;
      int [] left_arr = new int[mid];
      int [] right_arr = new int[len-mid];
      
    //Dividing array into two and copying into two separate arrays
      int k = 0;
      for(int i = 0;i<len;++i){
          if(i<mid){
              left_arr[i] = arr[i];
          }
          else{
              right_arr[k] = arr[i];
              k = k+1;
          }
      }
    // Recursively calling the function to divide the subarrays further
      mergeSort(left_arr,mid);
      mergeSort(right_arr,len-mid);
    // Calling the merge method on each subdivision
      merge(left_arr,right_arr,arr,mid,len-mid);
  }
{% endhighlight %}

## Quick Sort
{% highlight ruby linenos %}
public class Test {

	public static void main(String[] args) {
		int n[] = { 6, 5, 2, 7, 3, 9, 8, 4, 10, 1 };
		quicksort(n);
		System.out.print("快排结果：");
		for (int m : n) {
			System.out.print(m + " ");
		}
	}

	public static void quicksort(int n[]) {
		sort(n, 0, n.length - 1);
	}

	public static void sort(int n[], int l, int r) {
		if (l < r) {
			// 一趟快排，并返回交换后基数的下标
			int index = patition(n, l, r);
			// 递归排序基数左边的数组
			sort(n, l, index - 1);
			// 递归排序基数右边的数组
			sort(n, index + 1, r);
		}

	}

	public static int patition(int n[], int l, int r) {
		// p为基数，即待排序数组的第一个数
		int p = n[l];
		int i = l;
		int j = r;
		while (i < j) {
			// 从右往左找第一个小于基数的数
			while (n[j] >= p && i < j) {
				j--;
			}
			// 从左往右找第一个大于基数的数
			while (n[i] <= p && i < j) {
				i++;
			}
			// 找到后交换两个数
			swap(n, i, j);
		}
		// 使划分好的数分布在基数两侧
		swap(n, l, i);
		return i;
	}

	private static void swap(int n[], int i, int j) {
		int temp = n[i];
		n[i] = n[j];
		n[j] = temp;
	}

}

{% endhighlight %}
