#面试题总结-常见算法
##1.快速排序

####实现思想

1.选取基准值，一般选择数组的 第一位（最好选择中位数）.
2.分割数据，以基准数值的位置为分界点，分成左右两个序列，（此时左边 序列的值都比基准值小，右边的值都比基准值大）.
3.递归的对左右两个序列进行排序（直到序列为空或只有一个元素）.



	代码-Java实现

	static void quickSort(int arrays[],int left,int right){

		if(left < right){
			//分割数据(将比基准值小的移到基准值的左边，比基准值大的移到基准值的右边，并返回基准值的位置)
			int flag = partition(arrays,left,right);
			//递归排基准值前的数据，
			quickSort(arrays,left,flag-1);
			//递归排基准值后的数据
			quickSort(arrays,flag+1，right);
		}
	}


	 static int partition(int arrays[], int left,int right){
		//选定基准值的值
		int base = arrays[left];
		while(left < right){
			while(left < right && arrays[right] >= base){
				right--;
			}
			arrays[left] = arrays[right];
			while(left < right && arrays[left] <= base){
				left ++;
			}
			arrays[right] = arrays[left];
		}
		arrays[left] = base;
		return left;
	}

#####js实现快速排序可以参考阮一峰的这篇文章，非常清晰明了http://www.ruanyifeng.com/blog/2011/04/quicksort_in_javascript.html
