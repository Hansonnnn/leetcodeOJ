#### 在N个数中寻找最大的K个数

方法一：快排思想

N个数放在长度为N的数组S[]中，将S[]数组分为两部分Sa与Sb，取数组的其中一个元素X，Sa中的元素数值大于X，Sb部分的元素数值小于X。在这里就会出现两种情况

1）Sa中的元素个数大于或等于K，那么这K个数可以在Sa部分中寻找

2）Sa中的元素个数小于K,Sa的元素个数为T，那么剩下的K-T个元素需要在Sb中寻找

```
/**
 * Created by smith on 2017/2/8.
 *
 * @description quickSort
 */
public class KmaxFind {

    public int partition(int a[],int s,int t){
        int i,j,x;
        i=s;
        j=t;
        x=a[i];//哨兵
        while(i<j){
            while(a[j]<x&&i<j){
                j--;
            }
            if(i<j){
                a[i++]=a[j];
            }
            while(a[i]>x&&i<j){
                i++;
            }
            if(i<j){
                a[j--]=a[i];
            }

        }
        a[i]=x;
        return i;
    }

    public int findKmaxNum(int a[],int low,int high,int k){
        int index;
        int n;
        while(low<high){
            index=partition(a,low,high);
            n =index-low+1;
            if(k==n) {
                return index;
            }
            if(k>n){
               return  findKmaxNum(a,index+1,high,k-n);
            }
            if(k<n){
               return  findKmaxNum(a,low,index,k);
            }
        }
        return 0;
    }
```
