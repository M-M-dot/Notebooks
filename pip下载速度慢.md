# pip 下载时候  time out 或者速度慢

使用pip安装python库的时候经常会遇到超时而无法下载的问题，解决办法如下：

## 一，首先在下面文件夹下建立一个pip文件夹

C:\Users\Administrator\AppData\Roaming

然后在pip文件夹下新建一个文件pip.ini，内容：

```
[global]
timeout = 60000
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
use-mirrors = true
mirrors = https://pypi.tuna.tsinghua.edu.cn
```

这样就把pip安装源改成国内的了，速度很快

 

## 二，可单次使用国内源

1，设置超时时间：pip --default-timeout=100 install  Pillow,

2，不使用缓存：pip  --no-cache-dir install Pillow

2，使用国内源：pip install web.py -i http://pypi.douban.com/simple --trusted-host pypi.douban.com

阿里云 http://mirrors.aliyun.com/pypi/simple/

中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/ 

豆瓣(douban) http://pypi.douban.com/simple/ 

清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/

中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/

例：使用如下方法解决 下载速度会明显改善

pip install -i https://pypi.doubanio.com/simple/ 包名

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/ 
```



------------------------------------------------
版权声明：本文为CSDN博主「roohom」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_39161804/article/details/81191977

### 出现的问题

1. **问题1** 

   command :

   ```
   pip install https://pypi.tuna.tsinghua.edu.cn/simple/ ipykernel  
   ```

   error message : 

   ```
   Cannot unpack file /tmp/pip-uPp0eu-unpack/simple.html (downloaded from /tmp/pip-WluO09-build, content-type: text/html); cannot detect archive format
   Cannot determine archive format of /tmp/pip-WluO09-build
   ```

   ![1581240695547](pip%E4%B8%8B%E8%BD%BD%E9%80%9F%E5%BA%A6%E6%85%A2.assets/1581240695547.png)

   **解决方法：**

   ```
   pip install --index-url https://pypi.tuna.tsinghua.edu.cn/simple/ ipykernel
   ```

   **参考链接：** 

   https://zhuanlan.zhihu.com/p/24391265
   
   ```
   python -m ipykernel install --user --name env2 --display-name "spacy_env"
   ```
   
   





