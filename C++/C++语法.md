# c++ 相关语法知识（STL )

[toc]

Vector

vector 遍历的三种方式

定义：

```
struct Point
{
    double x;
    double y;
};
 vector<Point> points;
```



1. 通过下标进行访问

   ```C++
   for(int i = 0;i<points.size();i++){
       printf(points[i]);
   }
   ```

2. 通过迭代器进行访问

   ```
   vector<point> :: iterator iter;
   for(iter = points.begin();iter!= points.end();iter++){
   	printf(&*iter,(*iter).x,(*iter).y)
   }
   ```

3. 基于范围的for循环

   ```C++
   for(auto iter: points){
       printf(iter.x,iter.y)
   }
   ```

   ps: 如何理解C++ 中的迭代器  见c++迭代器

   

### vector 的基本操作

####  插入

```
push_back() 是在尾部添加
insert(p,t) 是在迭代器 p处插入元素t
```

#### 删除

```
clear() 删除所有元素
pop_back() 删除末尾元素
erase(p) 删除迭代器p处的元素
```

#### 初始化

``` 
vector<T> v1(n) 指定长度
vector<T> v2(n,i) 指定长度n 并每个元素都是i
vector<T> v3<v1>  定义一个v1的副本
vector<T> v  定义要给空的vector
```

#### 错误示例

```
    在对一个长度正在改变的vector进行删除和添加操作的时候会出现以下问题
    int leastInterval(vector<char>& tasks, int n) {
        //交替执行任务。 讲tasks 作为一个队列
    
        char first = tasks[0];
        int num = tasks.size();
        int bsize = tasks.size();
        tasks.erase(tasks.begin());
        while(tasks.size()!=bsize){
            bsize = tasks.size();
            vector<char>::iterator iter; 
            for(iter = tasks.begin();iter!=tasks.end();iter++){          
                if((*iter)==first)  tasks.push_back((*iter));
                else first = (*iter); 
                tasks.erase(iter);    
            }
        }
        int output = tasks.size()*n + num;
        return output;
    }
    ==42==ERROR: AddressSanitizer: negative-size-param: (size=-1)
    #4 0x7f6a884ad0b2  (/lib/x86_64-linux-gnu/libc.so.6+0x270b2)
0x6020000000d3 is located 3 bytes inside of 8-byte region [0x6020000000d0,0x6020000000d8)
allocated by thread T0 here:
    #6 0x7f6a884ad0b2  (/lib/x86_64-linux-gnu/libc.so.6+0x270b2)
==42==ABORTING    
```



## unordered_map

以键值对（pair类型）的形式存储数据，存储的各个键值对的**键互不相同且不允许被修改**。

无序

#### 头

```c++
#include <unordered_map>
using namespace std;
```

#### 初始化

```
unordered_map<string, string> umap;// 空的
unordered_map<string, string> umap{//有内容的
    {"Python教程","http://c.biancheng.net/python/"},
    {"Java教程","http://c.biancheng.net/java/"},
    {"Linux教程","http://c.biancheng.net/linux/"} };
unordered_map<string, string> umap2(umap);//拷贝
```

#### 遍历

```
for(auto[a,v]:fre){
	printf(a);
	printf(b);
}
for(auto& v: umap){
delete v.second;
}
for(auto iter = umap.begin();iter!=umap.end();++iter){
	cout<<iter->first<<" "<<iter->second<<endl;
}
```

#### 增

```
insert(k,v);emplace(k,v);emplace_hint(l,v);
```

#### 删

```
erase();
clear(); 
```

#### 改

swap（） 交换两个容器的键值对

```c++
unordered_map<char, int> freq;
for (char ch: tasks) {
	++freq[ch];
}
```

#### 查

```
size(); max_size();at(key);find(key);count(key);empty()
```

## Map





Line 32: Char 25: runtime error: member access within misaligned address 0xbebebebebebebebe for type 'ListNode', which requires 8 byte alignment (solution.cpp)
0xbebebebebebebebe: note: pointer points here
<memory cannot be printed>
SUMMARY: UndefinedBehaviorSanitizer: undefined-behavior prog_joined.cpp:42:25



## 用法细节

### 指针使用常见错误

```c++
/*不能对空指针进行*p操作*/
int * a; 
void func(int *a){
    *a = 1;  
}
func(a);// 错误： 空指针不能进行*p的操作
int b = 1; 
a = &b; 
func(a);//正确
```



```c++
/*
在函数里面修改传入的指针是没有用的，只能修改*p(指针的对象)； 
因为函数中的对象是temp，在函数结束之后会被销毁
*/
bool LRUReplacer::Victim(frame_id_t *frame_id) {
  int umap_size = umap.size();
  LOG_INFO("# before victim umap.size():%d",umap_size) ;
  if (umap.empty()) return false;

  show_linklist();
  show_umap();
  Node *victim = tail->prev;
  frame_id = &victim->frame_id;//错误： 修改指针所指的对象，没有用
  *frame_id = victim->frame_id;//正确： 修改指针所指对象的值，有用
  umap.erase(victim->frame_id);
  remove(victim);
  umap_size = umap.size();
  LOG_INFO("# frame_id:%d",(int)*frame_id) ;
  LOG_INFO("# after victim umap.size():%d",umap_size) ;
  return true;

}
```

### 数组数据依次向前移动一位（数组删除一个元素的非遍历方法）

```
MappingType array[0];
// 将array+index 的元素删除
memmove(array + index, array + index + 1,
                static_cast<size_t>(size - 1 - index) * sizeof(MappingType));
```

### 类型转换 static_cast、const_cast 、reinterpret_cast、dynamic_cast 

```
//newtype 是要转换的类型， data 是被转换的数据
xxx_cast<newType>(data)
```

static_cast : 不能进行指针类型的转换，只适用于同类型的数据的转换，最安全。（转换不成功，程序会报错）

const_cast: 用来将 const/volatile 类型转换为非 const/volatile 类型。

reinterpret 是“重新解释”的意思，顾名思义，reinterpret_cast 这种转换仅仅是对二进制位的重新解释，不会借助已有的转换规则对数据进行调整，非常简单粗暴，所以风险很高(怎么转换都能运行，程序不会报错)



###  引用，只有申明，没有初始化，可以使用引用进行赋值吗？ 可以

ValueType value;
