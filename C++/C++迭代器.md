

# C++迭代器详解

<div id="arc-body">要访问顺序容器和关联容器中的元素，需要通过“迭代器（iterator）”进行。迭代器是一个变量，相当于容器和操纵容器的算法之间的中介。迭代器可以指向容器中的某个元素，通过迭代器就可以读写它指向的元素。从这一点上看，迭代器和<a href="/c/80/" target="_blank">指针</a>类似。<br>
<br>
迭代器按照定义方式分成以下四种。<br>
<br>
1) 正向迭代器，定义方法如下：
<p class="info-box">
容器类名::iterator&nbsp; 迭代器名;</p>
<br>
2) 常量正向迭代器，定义方法如下：
<p class="info-box">
容器类名::const_iterator&nbsp; 迭代器名;</p>
<br>
3) 反向迭代器，定义方法如下：
<p class="info-box">
容器类名::reverse_iterator&nbsp; 迭代器名;</p>
<br>
4) 常量反向迭代器，定义方法如下：
<p class="info-box">
容器类名::const_reverse_iterator&nbsp; 迭代器名;</p>
<h2>
迭代器用法示例</h2>
通过迭代器可以读取它指向的元素，<code>*迭代器名</code>就表示迭代器指向的元素。通过非常量迭代器还能修改其指向的元素。<br>
<br>
迭代器都可以进行<code>++</code>操作。反向迭代器和正向迭代器的区别在于：
<ul>
<li>
对正向迭代器进行<code>++</code>操作时，迭代器会指向容器中的后一个元素；</li>
<li>
而对反向迭代器进行<code>++</code>操作时，迭代器会指向容器中的前一个元素。</li>
</ul>
<br>
下面的程序演示了如何通过迭代器遍历一个 vector 容器中的所有元素。
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;iostream&gt;</span></li><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;vector&gt;</span></li><li><span class="sh_keyword">u</span><a href="/ref/sin.html" target="_blank" class="sh_url"><span class="sh_keyword">sin</span></a><span class="sh_keyword">g</span> <span class="sh_keyword">namespace</span> std<span class="sh_symbol">;</span></li><li><span class="sh_type">int</span> <span class="sh_function">main</span><span class="sh_symbol">()</span></li><li><span class="sh_cbracket">{</span></li><li>    <span class="sh_usertype">vector&lt;int&gt;</span><span class="sh_normal"> </span>v<span class="sh_symbol">;</span>  <span class="sh_comment">//v是存放int类型变量的可变长数组，开始时没有元素</span></li><li>    <span class="sh_keyword">for</span> <span class="sh_symbol">(</span><span class="sh_type">int</span> n <span class="sh_symbol">=</span> <span class="sh_number">0</span><span class="sh_symbol">;</span> n<span class="sh_symbol">&lt;</span><span class="sh_number">5</span><span class="sh_symbol">;</span> <span class="sh_symbol">++</span>n<span class="sh_symbol">)</span></li><li>        v<span class="sh_symbol">.</span><span class="sh_function">push_back</span><span class="sh_symbol">(</span>n<span class="sh_symbol">);</span>  <span class="sh_comment">//push_back成员函数在vector容器尾部添加一个元素</span></li><li>    vector<span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">iterator</span><span class="sh_normal"> </span>i<span class="sh_symbol">;</span>  <span class="sh_comment">//定义正向迭代器</span></li><li>    <span class="sh_keyword">for</span> <span class="sh_symbol">(</span>i <span class="sh_symbol">=</span> v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> i <span class="sh_symbol">!=</span> v<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span> <span class="sh_cbracket">{</span>  <span class="sh_comment">//用迭代器遍历容器</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>i <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">" "</span><span class="sh_symbol">;</span>  <span class="sh_comment">//*i 就是迭代器i指向的元素</span></li><li>        <span class="sh_symbol">*</span>i <span class="sh_symbol">*=</span> <span class="sh_number">2</span><span class="sh_symbol">;</span>  <span class="sh_comment">//每个元素变为原来的2倍</span></li><li>    <span class="sh_cbracket">}</span></li><li>    cout <span class="sh_symbol">&lt;&lt;</span> endl<span class="sh_symbol">;</span></li><li>    <span class="sh_comment">//用反向迭代器遍历容器</span></li><li>    <span class="sh_keyword">for</span> <span class="sh_symbol">(</span>vector<span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">reverse_iterator</span><span class="sh_normal"> </span>j <span class="sh_symbol">=</span> v<span class="sh_symbol">.</span><span class="sh_function">rbegin</span><span class="sh_symbol">();</span> j <span class="sh_symbol">!=</span> v<span class="sh_symbol">.</span><span class="sh_function">rend</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>j<span class="sh_symbol">)</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>j <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">" "</span><span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">return</span> <span class="sh_number">0</span><span class="sh_symbol">;</span></li><li><span class="sh_cbracket">}</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">#include &lt;iostream&gt;
#include &lt;vector&gt;
u<a href="/ref/sin.html" target="_blank" class="sh_url">sin</a>g namespace std;
int main()
{
    vector&lt;int&gt; v;  //v是存放int类型变量的可变长数组，开始时没有元素
    for (int n = 0; n&lt;5; ++n)
        v.push_back(n);  //push_back成员函数在vector容器尾部添加一个元素
    vector&lt;int&gt;::iterator i;  //定义正向迭代器
    for (i = v.begin(); i != v.end(); ++i) {  //用迭代器遍历容器
        cout &lt;&lt; *i &lt;&lt; " ";  //*i 就是迭代器i指向的元素
        *i *= 2;  //每个元素变为原来的2倍
    }
    cout &lt;&lt; endl;
    //用反向迭代器遍历容器
    for (vector&lt;int&gt;::reverse_iterator j = v.rbegin(); j != v.rend(); ++j)
        cout &lt;&lt; *j &lt;&lt; " ";
    return 0;
}</pre></div></div>
程序的输出结果是：<br>
0 1 2 3 4<br>
8 6 4 2 0<br>
<br>
第 6 行，vector 容器有多个构造函数，如果用无参构造函数初始化，则容器一开始是空的。<br>
<br>
第 10 行，begin 成员函数返回指向容器中第一个元素的迭代器。++i 使得 i 指向容器中的下一个元素。end 成员函数返回的不是指向最后一个元素的迭代器，而是指向最后一个元素后面的位置的迭代器，因此循环的终止条件是<code>i != v.end()</code>。<br>
<br>
第 16 行定义了反向迭代器用以遍历容器。反向迭代器进行<code>++</code>操作后，会指向容器中的上一个元素。rbegin 成员函数返回指向容器中最后一个元素的迭代器，rend 成员函数返回指向容器中第一个元素前面的位置的迭代器，因此本循环实际上是从后往前遍历整个数组。<br>
<br>
如果迭代器指向了容器中最后一个元素的后面或第一个元素的前面，再通过该迭代器访问元素，就有可能导致程序崩溃，这和访问 NULL 或未初始化的指针指向的地方类似。<br>
<br>
第 10 行和第 16 行，写<code>++i</code>、<code>++j</code>相比于写<code>i++</code>、<code>j++</code>，程序的执行速度更快。回顾<code>++</code>被重载成前置和后置运算符的例子如下：
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display:none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_usertype">CDemo</span><span class="sh_normal"> </span>CDemo<span class="sh_symbol">::</span><span class="sh_keyword">operator</span><span class="sh_symbol">++</span> <span class="sh_symbol">()</span></li><li><span class="sh_cbracket">{</span>  <span class="sh_comment">//前置++</span></li><li>    <span class="sh_symbol">++</span>n<span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">return</span> <span class="sh_symbol">*</span><span class="sh_keyword">this</span><span class="sh_symbol">;</span></li><li><span class="sh_cbracket">}</span></li><li><span class="sh_usertype">CDemo</span><span class="sh_normal"> </span>CDemo<span class="sh_symbol">::</span><span class="sh_keyword">operator</span> <span class="sh_symbol">++(</span><span class="sh_type">int</span> k<span class="sh_symbol">)</span></li><li><span class="sh_cbracket">{</span>  <span class="sh_comment">//后置++</span></li><li>    <span class="sh_usertype">CDemo</span><span class="sh_normal"> </span><span class="sh_function">tmp</span><span class="sh_symbol">(*</span><span class="sh_keyword">this</span><span class="sh_symbol">);</span>  <span class="sh_comment">//记录修改前的对象</span></li><li>    n<span class="sh_symbol">++;</span></li><li>    <span class="sh_keyword">return</span> tmp<span class="sh_symbol">;</span>  <span class="sh_comment">//返回修改前的对象</span></li><li><span class="sh_cbracket">}</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">CDemo CDemo::operator++ ()
{  //前置++
    ++n;
    return *this;
}
CDemo CDemo::operator ++(int k)
{  //后置++
    CDemo tmp(*this);  //记录修改前的对象
    n++;
    return tmp;  //返回修改前的对象
}</pre></div></div>
后置<code>++</code>要多生成一个局部对象 tmp，因此执行速度比前置的慢。同理，迭代器是一个对象，<a href="/stl/" target="_blank">STL</a> 在重载迭代器的<code>++</code>运算符时，后置形式也比前置形式慢。在次数很多的循环中，<code>++i</code>和<code>i++</code>可能就会造成运行时间上可观的差别了。因此，本教程在前面特别提到，对循环控制变量i，要养成写<code>++i</code>、不写<code>i++</code>的习惯。<br>
<br>
注意，容器适配器 stack、queue 和 priority_queue 没有迭代器。容器适配器有一些成员函数，可以用来对元素进行访问。
<h2>
迭代器的功能分类</h2>
不同容器的迭代器，其功能强弱有所不同。容器的迭代器的功能强弱，决定了该容器是否支持 STL 中的某种算法。例如，排序算法需要通过随机访问迭代器来访问容器中的元素，因此有的容器就不支持排序算法。<br>
<br>
常用的迭代器按功能强弱分为输入、输出、正向、双向、随机访问五种，这里只介绍常用的三种。<br>
<br>
1) 正向迭代器。假设 p 是一个正向迭代器，则 p 支持以下操作：++p，p++，*p。此外，两个正向迭代器可以互相赋值，还可以用<code>==</code>和<code>!=</code>运算符进行比较。<br>
<br>
2) 双向迭代器。双向迭代器具有正向迭代器的全部功能。除此之外，若 p 是一个双向迭代器，则<code>--p</code>和<code>p--</code>都是有定义的。<code>--p</code>使得 p 朝和<code>++p</code>相反的方向移动。<br>
<br>
3) 随机访问迭代器。随机访问迭代器具有双向迭代器的全部功能。若 p 是一个随机访问迭代器，i 是一个整型变量或常量，则 p 还支持以下操作：
<ul>
<li>
p+=i：使得 p 往后移动 i 个元素。</li>
<li>
p-=i：使得 p 往前移动 i 个元素。</li>
<li>
p+i：返回 p 后面第 i 个元素的迭代器。</li>
<li>
p-i：返回 p 前面第 i 个元素的迭代器。</li>
<li>
p[i]：返回 p 后面第 i 个元素的引用。</li>
</ul>
<br>
此外，两个随机访问迭代器 p1、p2 还可以用 &lt;、&gt;、&lt;=、&gt;= 运算符进行比较。<code>p1&lt;p2</code>的含义是：p1 经过若干次（至少一次）<code>++</code>操作后，就会等于 p2。其他比较方式的含义与此类似。<br>
<br>
对于两个随机访问迭代器 p1、p2，表达式<code>p2-p1</code>也是有定义的，其返回值是 p2 所指向元素和 p1 所指向元素的序号之差（也可以说是 p2 和 p1 之间的元素个数减一）。<br>
<br>
表1所示为不同容器的迭代器的功能。<br>
<br>
<table>
<caption>
表1：不同容器的迭代器的功能</caption>
<tbody>
<tr>
<th>
容器</th>
<th>
迭代器功能</th>
</tr>
<tr>
<td>
vector</td>
<td>
随机访问</td>
</tr>
<tr>
<td>
deque</td>
<td>
随机访问</td>
</tr>
<tr>
<td>
list</td>
<td>
双向</td>
</tr>
<tr>
<td>
set / multiset</td>
<td>
双向</td>
</tr>
<tr>
<td>
map / multimap</td>
<td>
双向</td>
</tr>
<tr>
<td>
stack</td>
<td>
不支持迭代器</td>
</tr>
<tr>
<td>
queue</td>
<td>
不支持迭代器</td>
</tr>
<tr>
<td>
priority_queue</td>
<td>
不支持迭代器</td>
</tr>
</tbody>
</table>
<br>
例如，vector 的迭代器是随机迭代器，因此遍历 vector 容器有以下几种做法。下面的程序中，每个循环演示了一种做法。<br>
<br>
【实例】遍历 vector 容器。
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;iostream&gt;</span></li><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;vector&gt;</span></li><li><span class="sh_keyword">using</span> <span class="sh_keyword">namespace</span> std<span class="sh_symbol">;</span></li><li><span class="sh_type">int</span> <span class="sh_function">main</span><span class="sh_symbol">()</span></li><li><span class="sh_cbracket">{</span></li><li>    <span class="sh_usertype">vector&lt;int&gt;</span><span class="sh_normal"> </span><span class="sh_function">v</span><span class="sh_symbol">(</span><span class="sh_number">100</span><span class="sh_symbol">);</span> <span class="sh_comment">//v被初始化成有100个元素</span></li><li>    <span class="sh_keyword">for</span><span class="sh_symbol">(</span><span class="sh_type">int</span> i <span class="sh_symbol">=</span> <span class="sh_number">0</span><span class="sh_symbol">;</span>i <span class="sh_symbol">&lt;</span> v<span class="sh_symbol">.</span><span class="sh_function">size</span><span class="sh_symbol">()</span> <span class="sh_symbol">;</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span> <span class="sh_comment">//size返回元素个数</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> v<span class="sh_symbol">[</span>i<span class="sh_symbol">];</span> <span class="sh_comment">//像普通数组一样使用vector容器</span></li><li>    vector<span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">iterator</span><span class="sh_normal"> </span>i<span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">for</span><span class="sh_symbol">(</span>i <span class="sh_symbol">=</span> v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> i <span class="sh_symbol">!=</span> v<span class="sh_symbol">.</span><span class="sh_function">end</span> <span class="sh_symbol">();</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span> <span class="sh_comment">//用 != 比较两个迭代器</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span> i<span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">for</span><span class="sh_symbol">(</span>i <span class="sh_symbol">=</span> v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> i <span class="sh_symbol">&lt;</span> v<span class="sh_symbol">.</span><span class="sh_function">end</span> <span class="sh_symbol">();++</span>i<span class="sh_symbol">)</span> <span class="sh_comment">//用 &lt; 比较两个迭代器</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span> i<span class="sh_symbol">;</span></li><li>    i <span class="sh_symbol">=</span> v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span></li><li>    <span class="sh_keyword">while</span><span class="sh_symbol">(</span>i <span class="sh_symbol">&lt;</span> v<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">())</span> <span class="sh_cbracket">{</span> <span class="sh_comment">//间隔一个输出</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span> i<span class="sh_symbol">;</span></li><li>        i <span class="sh_symbol">+=</span> <span class="sh_number">2</span><span class="sh_symbol">;</span> <span class="sh_comment">// 随机访问迭代器支持 "+= 整数"  的操作</span></li><li>    <span class="sh_cbracket">}</span></li><li><span class="sh_cbracket">}</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">#include &lt;iostream&gt;
#include &lt;vector&gt;
using namespace std;
int main()
{
    vector&lt;int&gt; v(100); //v被初始化成有100个元素
    for(int i = 0;i &lt; v.size() ; ++i) //size返回元素个数
        cout &lt;&lt; v[i]; //像普通数组一样使用vector容器
    vector&lt;int&gt;::iterator i;
    for(i = v.begin(); i != v.end (); ++i) //用 != 比较两个迭代器
        cout &lt;&lt; * i;
    for(i = v.begin(); i &lt; v.end ();++i) //用 &lt; 比较两个迭代器
        cout &lt;&lt; * i;
    i = v.begin();
    while(i &lt; v.end()) { //间隔一个输出
        cout &lt;&lt; * i;
        i += 2; // 随机访问迭代器支持 "+= 整数"  的操作
    }
}</pre></div></div>
list 容器的迭代器是双向迭代器。假设 v 和 i 的定义如下：
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display:none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_usertype">list&lt;int&gt;</span><span class="sh_normal"> </span>v<span class="sh_symbol">;</span></li><li>list<span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">const_iterator</span><span class="sh_normal"> </span>i<span class="sh_symbol">;</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">list&lt;int&gt; v;
list&lt;int&gt;::const_iterator i;</pre></div></div>
则以下代码是合法的：
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_keyword">for</span><span class="sh_symbol">(</span>i<span class="sh_symbol">=</span>v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> i<span class="sh_symbol">!=</span>v<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span></li><li>cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>i<span class="sh_symbol">;</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">for(i=v.begin(); i!=v.end(); ++i)
cout &lt;&lt; *i;</pre></div></div>
以下代码则不合法：
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_keyword">for</span><span class="sh_symbol">(</span>i<span class="sh_symbol">=</span>v<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> i<span class="sh_symbol">&lt;</span>v<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span></li><li>cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>i<span class="sh_symbol">;</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">for(i=v.begin(); i&lt;v.end(); ++i)
cout &lt;&lt; *i;</pre></div></div>
因为双向迭代器不支持用“&lt;”进行比较。以下代码也不合法：
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_keyword">for</span><span class="sh_symbol">(</span><span class="sh_type">int</span> i<span class="sh_symbol">=</span><span class="sh_number">0</span><span class="sh_symbol">;</span> i<span class="sh_symbol">&lt;</span>v<span class="sh_symbol">.</span><span class="sh_function">size</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>i<span class="sh_symbol">)</span></li><li>cout <span class="sh_symbol">&lt;&lt;</span> v<span class="sh_symbol">[</span>i<span class="sh_symbol">];</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">for(int i=0; i&lt;v.size(); ++i)
cout &lt;&lt; v[i];</pre></div></div>
因为 list 不支持随机访问迭代器的容器，也不支持用下标随机访问其元素。<br>
<br>
在 <a href="/cplus/" target="_blank">C++</a> 中，数组也是容器。数组的迭代器就是指针，而且是随机访问迭代器。例如，对于数组 int a[10]，int * 类型的指针就是其迭代器。则 a、a+1、a+2 都是 a 的迭代器。
<h2>
迭代器的辅助函数</h2>
STL 中有用于操作迭代器的三个函数模板，它们是：
<ul>
<li>
advance(p, n)：使迭代器 p 向前或向后移动 n 个元素。</li>
<li>
dis<a href="/ref/tan.html" target="_blank">tan</a>ce(p, q)：计算两个迭代器之间的距离，即迭代器 p 经过多少次 + + 操作后和迭代器 q 相等。如果调用时 p 已经指向 q 的后面，则这个函数会陷入死循环。</li>
<li>
iter_swap(p, q)：用于交换两个迭代器 p、q 指向的值。</li>
</ul>
<br>
要使用上述模板，需要包含头文件 algorithm。下面的程序演示了这三个函数模板的 用法。
<div class="snippet-container" style="undefined;"><div class="sh_bright snippet-wrap"><div class="snippet-menu sh_sourceCode" style="display: none;"><pre><a class="snippet-copy sh_url" href="#" style="display: none;">复制</a><a class="snippet-text sh_url" href="#">纯文本</a><a class="snippet-window sh_url" href="#">复制</a></pre></div><pre class="cpp sh_cpp snippet-formatted sh_sourceCode"><ol class="snippet-num"><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;list&gt;</span></li><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;iostream&gt;</span></li><li><span class="sh_preproc">#include</span> <span class="sh_string">&lt;algorithm&gt;</span> <span class="sh_comment">//要使用操作迭代器的函数模板，需要包含此文件</span></li><li><span class="sh_keyword">using</span> <span class="sh_keyword">namespace</span> std<span class="sh_symbol">;</span></li><li><span class="sh_type">int</span> <span class="sh_function">main</span><span class="sh_symbol">()</span></li><li><span class="sh_cbracket">{</span></li><li>    <span class="sh_type">int</span> a<span class="sh_symbol">[</span><span class="sh_number">5</span><span class="sh_symbol">]</span> <span class="sh_symbol">=</span> <span class="sh_cbracket">{</span> <span class="sh_number">1</span><span class="sh_symbol">,</span> <span class="sh_number">2</span><span class="sh_symbol">,</span> <span class="sh_number">3</span><span class="sh_symbol">,</span> <span class="sh_number">4</span><span class="sh_symbol">,</span> <span class="sh_number">5</span> <span class="sh_cbracket">}</span><span class="sh_symbol">;</span></li><li>    list <span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;</span> <span class="sh_function">lst</span><span class="sh_symbol">(</span>a<span class="sh_symbol">,</span> a<span class="sh_number">+5</span><span class="sh_symbol">);</span></li><li>    list <span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">iterator</span><span class="sh_normal"> </span>p <span class="sh_symbol">=</span> lst<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span></li><li>    <span class="sh_function">advance</span><span class="sh_symbol">(</span>p<span class="sh_symbol">,</span> <span class="sh_number">2</span><span class="sh_symbol">);</span>  <span class="sh_comment">//p向后移动两个元素，指向3</span></li><li>    cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">"1)"</span> <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>p <span class="sh_symbol">&lt;&lt;</span> endl<span class="sh_symbol">;</span>  <span class="sh_comment">//输出 1)3</span></li><li>    <span class="sh_function">advance</span><span class="sh_symbol">(</span>p<span class="sh_symbol">,</span> <span class="sh_symbol">-</span><span class="sh_number">1</span><span class="sh_symbol">);</span>  <span class="sh_comment">//p向前移动一个元素，指向2</span></li><li>    cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">"2)"</span> <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>p <span class="sh_symbol">&lt;&lt;</span> endl<span class="sh_symbol">;</span>  <span class="sh_comment">//输出 2)2</span></li><li>    list<span class="sh_symbol">&lt;</span><span class="sh_type">int</span><span class="sh_symbol">&gt;::</span><span class="sh_usertype">iterator</span><span class="sh_normal"> </span>q <span class="sh_symbol">=</span> lst<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">();</span></li><li>    q<span class="sh_symbol">--;</span>  <span class="sh_comment">//q 指向 5</span></li><li>    cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">"3)"</span> <span class="sh_symbol">&lt;&lt;</span> <span class="sh_function">distance</span><span class="sh_symbol">(</span>p<span class="sh_symbol">,</span> q<span class="sh_symbol">)</span> <span class="sh_symbol">&lt;&lt;</span> endl<span class="sh_symbol">;</span>  <span class="sh_comment">//输出 3)3</span></li><li>    <span class="sh_function">iter_swap</span><span class="sh_symbol">(</span>p<span class="sh_symbol">,</span> q<span class="sh_symbol">);</span> <span class="sh_comment">//交换 2 和 5</span></li><li>    cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">"4)"</span><span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">for</span> <span class="sh_symbol">(</span>p <span class="sh_symbol">=</span> lst<span class="sh_symbol">.</span><span class="sh_function">begin</span><span class="sh_symbol">();</span> p <span class="sh_symbol">!=</span> lst<span class="sh_symbol">.</span><span class="sh_function">end</span><span class="sh_symbol">();</span> <span class="sh_symbol">++</span>p<span class="sh_symbol">)</span></li><li>        cout <span class="sh_symbol">&lt;&lt;</span> <span class="sh_symbol">*</span>p <span class="sh_symbol">&lt;&lt;</span> <span class="sh_string">" "</span><span class="sh_symbol">;</span></li><li>    <span class="sh_keyword">return</span> <span class="sh_number">0</span><span class="sh_symbol">;</span></li><li><span class="sh_cbracket">}</span></li></ol></pre><pre class="snippet-textonly sh_sourceCode" style="display:none;">#include &lt;list&gt;
#include &lt;iostream&gt;
#include &lt;algorithm&gt; //要使用操作迭代器的函数模板，需要包含此文件
using namespace std;
int main()
{
    int a[5] = { 1, 2, 3, 4, 5 };
    list &lt;int&gt; lst(a, a+5);
    list &lt;int&gt;::iterator p = lst.begin();
    advance(p, 2);  //p向后移动两个元素，指向3
    cout &lt;&lt; "1)" &lt;&lt; *p &lt;&lt; endl;  //输出 1)3
    advance(p, -1);  //p向前移动一个元素，指向2
    cout &lt;&lt; "2)" &lt;&lt; *p &lt;&lt; endl;  //输出 2)2
    list&lt;int&gt;::iterator q = lst.end();
    q--;  //q 指向 5
    cout &lt;&lt; "3)" &lt;&lt; distance(p, q) &lt;&lt; endl;  //输出 3)3
    iter_swap(p, q); //交换 2 和 5
    cout &lt;&lt; "4)";
    for (p = lst.begin(); p != lst.end(); ++p)
        cout &lt;&lt; *p &lt;&lt; " ";
    return 0;
}</pre></div></div>
程序的输出结果是：<br>
1) 3<br>
2) 2<br>
3) 3<br>
4) 1 5 3 4 2<br>
</div>