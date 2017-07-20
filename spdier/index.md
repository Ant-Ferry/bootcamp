# 爬虫工程师

> Welcome to Beijing Zaoshu Ltd.

## 技能树
### 英语阅读能力
>  

### 编程语言
> 主力编程语言是Python3。

### 爬虫框架

#### Scrapy
> 如果以前没使用过，可以先从[文档](https://docs.scrapy.org/en/latest/)看起

#### Selenium
> 一般不上这一套东西，但是如果目标站点有非常多的前端JS跳转或者其他必须模拟浏览器的原因，直接使用这个。
>
> 因为模拟浏览器的各种行为，最后相当于写了一个浏览器，不如一步到位。

#### Without framework
> 因为历史原因，我们有一些项目是没有使用爬虫框架写的，新开的项目一般不允许不适用框架了，比如一般框架现成的失败重试机制，需要手写的话非常浪费时间。

### Git
> 团队内部使用Git进行版本管理，[统一读法请点这里](http://dict.youdao.com/dictvoice?audio=git&type=1)，请不要读`G-I-T`。
>
> 中央没有钦点的Git客户端，要使用Github客户端、SouceTree还是Tower什么的都可以，但是基本的Git操作需要有一定的了解。
>
> 一般通过Github同步代码，但是如果偶尔需要同步一些临时性的修改，通过邮件发送patch也是可以接受的。
```bash
# A
git diff > patch # send patch with email


# B
# after got the patch
cd ${GIT_ROOT}
git apply patch
```

#### gitignore
1. 一般来说，只向git repo里面提交文本文件以及必要的资源文件，比如代码。其他文件、文件夹，比如IDE自动生成的**.idea**文件夹，运行python程序自动生成的*.pyc或者__pycache__文件夹等，或者其他编译语言编译的中间文件、输出文件等，全部不能提交到git repo里面去。
2. [gitignore样例](https://www.gitignore.io/api/go%2Cc%2B%2B%2Cvim%2Cpython%2Cpycharm)，样例覆盖了**vim, python, go, c++**。

#### 多人协作
> 请阅读[Github workflow](https://guides.github.com/introduction/flow/)


