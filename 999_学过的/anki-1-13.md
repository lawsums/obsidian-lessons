`button-home`   `button-anki-open`   `button-anki-update`
DECK: 算法设计与分析

1. {Q}以下是计算xⁿ的值的过程
```cpp
int power(x, m)
{//计算xᵐ的值并返回。
y=(1);i=m;
While(i-- >0)
   y=y*x;
(return y);
}
```
，变量y初始值设为1的原因是（ ）；循环条件While(i-- >0)的含义是（ ）；循环体y=y\*x的作用是（ ）；若m=0，该函数返回值为（ ）{A}乘法的单位元，保证m=0时结果为1（x⁰=1），且不影响后续乘积累积；控制循环执行m次（初始i=m，每次i减1，直至i=0时退出）；累积x的乘积，逐步计算x×x×…×x（共m个x相乘）；1{E}
<!--ID: 1768273331517-->

2. {Q}以下是背包问题的贪心算法过程
```cpp
void Knapsack(int n,float M,float v[],float w[],float x[])
{
       Sort(n,v,w);
       int i;
       for (i=1;i<=n;i++) x[i]=0;
       float c=M;
       for (i=1;i<=n;i++) {
          if (w[i]>c) break;
          x[i]=1;
          c -=w[i];
          }
       if (i<=n) x[i]=c/w[i];
}
```
，Sort(n,v,w)函数的作用是按照（ ）对物品排序；初始时for循环将x[i]全部设为0的目的是（ ）；当w[i]>c时执行break的原因是（ ）；若i<=n时x[i]=c/w[i]，此处x[i]表示（ ）{A}单位重量价值从大到小；初始化物品选择状态（未选择时装入比例为0）；当前物品重量超过剩余背包容量，无法完整装入；该物品的装入比例{E}
<!--ID: 1768273331521-->

3. {Q}以下是最大子段和的动态规划算法过程
```cpp
int MaxSum(int n, int a[])
{
    int sum=0, b=0；   //sum存储当前最大的b[j], b存储b[j]
    for(int j=1； j<=n； j++)  {  
        if (b>0)  b+= a[j] ；
        else  b=a[i];     ；    //一旦某个区段和为负，则从下一个位置累和
        if(b>sum) sum=b;
     }
     return sum；
 }        
```
，代码中“b存储b[j]”的含义是（ ）；else分支“b=a[i]”存在笔误，正确应为（ ）；执行该else分支的原因是（ ）；if(b>sum) sum=b的作用是（ ）{A}以当前元素a[j]为结尾的子段和；b=a[j]；此前子段和为负，继续累加会降低后续子段和，需从当前元素重新开始累加；更新当前找到的最大子段和{E}
<!--ID: 1768273331525-->

4. {Q}以下是快速排序算法过程
```cpp
template<class Type>
void QuickSort (Type a[], int p, int r)
{
      if (p<r) {
        int q=Partition(a,p,r);
        QuickSort (a,p,q-1); //对左半段排序
        QuickSort (a,q+1,r); //对右半段排序
        }
}
```
，Partition(a,p,r)函数的核心功能是（ ）；递归调用的条件if(p<r)的含义是（ ）；QuickSort(a,p,q-1)和QuickSort(a,q+1,r)分别表示对（ ）排序；该算法能实现整体排序的关键是（ ）{A}选择基准元素，将数组划分为左半段（小于基准）和右半段（大于等于基准），并返回基准位置q；当前子数组长度大于1（需继续划分排序）；划分后基准左侧的子数组、基准右侧的子数组；通过递归划分将大数组分解为小数组，排序后合并实现整体有序{E}
<!--ID: 1768273331529-->

5. {Q}以下是排列问题算法过程
```cpp
Template <class Type>
void perm(Type list[],  int k, int m )
{ //产生[list[k:m]的所有排列
    if(k==m)
     {  //只剩下一个元素
         for (int i=0;i<=m;i++)  cout<<list[i];
         cout<<endl;
    }
    else  //还有多个元素待排列，递归产生排列
       for (int i=k; i<=m; i++)
        {
           swap(list[k],list[i]);
           perm(list,k+1,m);
           swap(list[k],list[i]);         
     }
  } 
```
，if(k\==m)时执行输出操作的原因是（ ）；第一次swap(list[k],list[i])的作用是（ ）；perm(list,k+1,m)表示（ ）；第二次swap(list[k],list[i])的作用是（ ）{A}此时list[k: m]已形成一个完整排列（k与m重合，无剩余元素待排列）；确定当前位置k的元素，构建部分解；递归产生list[k+1: m]的所有排列；恢复数组原状态，以便尝试下一个元素组合（回溯）{E}
<!--ID: 1768273331532-->

6. {Q}以下是二分搜索算法过程
```cpp
template<class Type> 
int BinarySearch(Type a[], const Type& x, int l, int r)
{
     while (l<=r ){ 
        int m = ((l+r)/2);
        if (x == a[m]) return m;
        if (x < a[m]) r = m-1; else r = m+1;
        }
    return -1;
}
```
，变量m=((l+r)/2)的含义是（ ）；if(x < a[m]) r = m-1的作用是（ ）；else分支“r = m+1”存在逻辑错误，正确应为（ ）；循环条件l<=r的含义是（ ）{A}当前搜索区间[l,r]的中间位置索引；缩小搜索区间至左半段，排除右半段（右半段元素均大于x）；l = m+1；搜索区间不为空（仍有元素待查找）{E}
<!--ID: 1768273331536-->

7. {Q}以下是合并排序算法过程
```cpp
template<class Type>
void Mergesort(Type a[], int left, int right)
{
if (left<right){
int i=(left+right)/2;
Mergesort(a, left, i );
Mergesort(a, i+1, right);
Merge(a,b, left,i,right);//合并到数组b
Copy(a,b, left,right ); //复制到数组a
}
}
```
，int i=(left+right)/2的作用是（ ）；Mergesort(a, left, i )和Mergesort(a, i+1, right)分别表示（ ）；Merge(a,b, left,i,right)函数的输入是（ ）；Copy(a,b, left,right )的作用是（ ）{A}将当前数组区间[left,right]划分为两个等长子区间[left,i]和[i+1,right]；对左子区间[left,i]排序、对右子区间[i+1,right]排序；两个已排序的子数组a[left..i]和a[i+1..right]；将b中合并后的有序数据复制回原数组a，完成当前区间排序{E}
<!--ID: 1768273331539-->
