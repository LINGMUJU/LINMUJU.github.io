---
title: Python
tags: basic
---


# 文件读写
## 目录结构
linux：/
windows：( \C:\ D:\ )
绝对路径：以根目录为起始
相对路径，以当前为起始点(.)，上一级为(..)，再上一级(../..)，下一级(./)
## 读写
+在原功能的基础上增加读写功能
x创建写模式
f=open("文件路径","模式：读(r)、清空原数据写(w)、在原文件基础上继续写(a)",encoding="编码")
f=close()
or
with open("文件路径","模式：读(r)、清空原数据写(w)、在原文件基础上继续写(a)",encoding="编码") as f
### 读
rt以文本模式打开
rb以二进制模式打开
print(f.read()) 一次性读完所有，并记录文件
print(f.read(byte)) 一次性读相应字节数
print(f.readline()) 读一行内容并打印
print(f.readlines()) 返回全部文件内容
```py
fname = input("请输入要打开的文件名称:")
fo = open(fname,"r")
for line in fo:
    print(line)
fo.close()
```
```py
f = open("./data.text","r",encoding="utf-8")
line = f.readline() #读一行
while line != "" : #判断当前是否为空
    print(line) #不为空则打印当前行
    line = f.readline() #读取下一行
```
### 写
f.write()
ls = ["中国", "法国", "美国"]
f.writelines(ls)
f.seek(0)

## 数据
### 一维
    数据的维度：一维、二维、多维、高维
    一维数据的表示：列表类型(有序)和集合类型(无序)
    一维数据的存储：空格分隔、逗号分隔、特殊符号分隔
    一维数据的处理：字符串方法 .split() 和 .join()
### 二维
    二维数据的表示：列表类型，其中每个元素也是一个列表
    CSV格式：逗号分隔表示一维，按行分隔表示二维
    二维数据的处理：for循环+.split()和.join()


# 异常
## 捕捉异常
try
except
try：代码
except:可能发生的异常类型 print("不符合规则")
except:捕捉所有类型
else:结果
finally:结束程序
## 测试
库:import unittest
被测试文件:text.py
测试文件:test_text.py
from 文件名 import 函数名/类名
class Test类名(unittest.TestCase):
    def setUp(self):
        self.sentence = Sentence("测试开始")
    def test_(self):
        assert 会直接中断
        self.assertEqual(self.sentence.被测试类或函数) 
python -m unittest 运行 .表示测试通过F表示没有通过
assertEqual(A,B)   取反assertNotEqual(A,B)
assertTrue(A)     取反assertFalse(A)
asserttln(A,B)   A in B   取反assertNotln(A,B)

# 列表、字典、元组
## 列表
shopping_list=[,] 列表是可变的
.append 添加
max(list)
min(list)
sorted(list)
## 元组
example_tuple=(,) 不可变，但可以存相同
## 字典
dict={"键":"值",} 可变
    dict["键"]="值" 添加
    "键" in dict 可知该键是否存在
    del dict["键"]="值" 删除
    dict.key()所有键
    dict.valus()所有值
    dict.items()所有键值对
    d.get(k, <default>) 键k存在，则返回相应值，不在则返回<default>值
    d.pop(k, <default>) 键k存在，则取出相应值，不在则返回<default>值
    d.popitem() 随机从字典d中取出一个键值对，以元组形式返回
    d.clear() 删除所有的键值对
    len(d)


## 集合

    集合用大括号 {} 表示，元素间用逗号分隔
    建立集合类型用 {} 或 set()
    建立空集合类型，必须使用set()

S.add(x) 如果x不在集合S中，将x增加到S
S.discard(x) 移除S中元素x，如果x不在集合S中，不报错
S.remove(x) 移除S中元素x，如果x不在集合S中，产生KeyError异常
S.clear() 移除S中所有元素
S.pop() 随机返回S的一个元素，更新S，若S为空产生KeyError异常
S.copy() 返回集合S的一个副本
len(S) 返回集合S的元素个数
x in S 判断S中元素x，x在集合S中，返回True，否则返回False
x not in S 判断S中元素x，x不在集合S中，返回True，否则返回False
set(x) 将其他类型变量x转变为集合类型

包含关系比较、数据去重

## 序列
序列类型：字符串类型、元组类型、列表类型


# 爬虫
## 获取网页内容 requests

## 解析网页内容
HTTP
GET
POST
请求行：
    POST/user/info HTTP/1.1
请求头：
    HOST:www.example.com
    User-Agent:curl/7.77.0
    Accept:*/*
        e:接受HTML text/html、接受JOSN application/json、 接受HTML和JSON text/html,application/json、接受任意类型*/*
请求体：//GET一般是空的
    {"username":
    "email":"llj.qq.com"}

### 网页技术结构
HTML(定义网页的结构和信息) CSS(定义网页的样式) JavaScript(定义用户和网页的交互逻辑)
HTML
```
<!DOCTYPE HTML> 告知浏览器是html
<html> 开始
    <body>
        <h1></h1> 标题，最多h6
        <p>给你<br>换行<b>加粗</b><i>斜体</i><u>加下划线</u></p> 文字
        <p class="content></p> 定义类的名称
        <img src="链接"width="px">
        <a href="链接跳转"target="指定网页的打开方式_self _blank">文字</a>
        <div style="background-color:red"></div> 容器，可以直接改变整体的颜色等
        <span></span> 容器，可以改变一部分颜色等
        <ol> 有序
        <li></li>
        </ol>
        <ul> 无序
        </ul>
        <table border="1"> 添加属性
            <thead>
                <tr>
                    <td>表头一</td>
                    <td>表头二</td>
                </tr>
            </thead>
                <tr> 第一行
                    <td>内容</td>
                </tr>
                <tr> 第二行
                    <td>内容</td>
                </tr>                
            <tbody>
            </tbody>
        </table>
    </body>
</html> 结束
```
## 储存和分析数据BeautifulSoup4
soup = BeautifulSoup(content,"html.parser")
all=soup.findAll("标签",attrs={"class":"value"})
利用for循环筛选
```py
import requests
from bs4 import BeautifulSoup
#伪装为浏览器
headers={
    "User-Agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36"
}
#获得回应
with open("D:/vc/py/title.txt","w",encoding="utf-8") as titles:
    for start_num in range(0,250,25):
        response = requests.get(f"https://movie.douban.com/top250?start={start_num}",headers=headers)
        #print(response.text)
        html=response.text
        soup = BeautifulSoup(html,"html.parser")
        #寻找标题
        all_titles = soup.findAll("span",attrs={"class":"title"})#标签，类
        for title in all_titles:
            title_string = title.string
            if "/" not in title_string:
                titles.write(title_string)
                titles.write('\n')
```

# wordcloud库的使用

wordcloud库把词云当作一个WordCloud对象
w.generate(txt) 向WordCloud对象w中加载文本txt
w.to_file(filename) 将词云输出为图像文件，.png或.jpg格式
```py
import wordcloud
c = wordcloud.WordCloud()
c.generate("wordcloud by Python")
c.to_file("pywordcloud.png")
```

    w = wordcloud.WordCloud(<参数>)
    width 指定词云对象生成图片的宽度，默认400像素
    height 指定词云对象生成图片的高度，默认200像素
    min_font_size 指定词云中字体的最小字号，默认4号
    max_font_size 指定词云中字体的最大字号，根据高度自动调节
    font_step 指定词云中字体字号的步进间隔，默认为1
    font_path 指定字体文件的路径，默认None
    max_words 指定词云显示的最大单词数量，默认200
    stop_words 指定词云的排除词列表，即不显示的单词列表
    mask 指定词云形状，默认为长方形，需要引用imread()函数
    background_color 指定词云图片的背景颜色，默认为黑色
    mask = imread("图形照片") from imageio import imread

# jieba库
- 中文文本需要通过分词获得单个的词语
- jieba是优秀的中文分词第三方库，需要额外安装
- jieba库提供三种分词模式，最简单只需掌握一个函数

分词三种模式
- 精确模式：把文本精确的切分开，不存在冗余单词 jieba.lcut(s)
- 全模式：把文本中所有可能的词语都扫描出来，有冗余 jieba.lcut(s, cut_all=True)
- 搜索引擎模式：在精确模式基础上，对长词再次切分jieba.lcut_for_search(s)

jieba.add_word(w)向分词词典增加新词
```py
import jieba
with open("E://AATemporary_folder//python_review//report.txt","r+",encoding = "utf-8") as txt:
    txt=txt.read()
words=jieba.lcut(txt)
counts={} #定义数量字典
for word in words:
    if len(word)==1: #如果是一个字的话即不是词，跳过
        continue
    else:
        counts[word]=counts.get(word,0)+1
items=list(counts.items())
items.sort(key=lambda x:x[1],reverse=True)#实现倒序
for i in range(20):
    word,count = items[i]
    print("{0:<10}{1}".format(word,count))
```

# turtle

turtle.setup(width, height, startx, starty) 建立绘制窗口
turtle.goto(x, y) 空间坐标前进与后退
turtle.seth(angle) 改变行进的方向，绝对
turtle.left(angle) 左转
turtle.right(angle) 右转
turtle.colormode(mode) 颜色
turtle.penup() turtle.pu()抬起画笔
turtle.pendown() turtle.pd()落下画笔
turtle.pensize(width) turtle.width(width)画笔宽度
turtle.pencolor(color) 画笔颜色
turtle.forward(d) turtle.fd(d)向前行进
turtle.circle(r, extent=None)r: 默认圆心在海龟左侧r距离的位置，extent: 绘制角度，默认是360度整圆
turtle.setheading(angle) turtle.seth(angle)改变行进方向

# random

基本随机数函数:seed(), random()
扩展随机数函数:randint(), getrandbits(), uniform(),randrange(), choice(), shuffle(), sample()

# Pylnstaller
pip install pyinstaller
pyinstaller -F  <文件名.py>
--clean 清理打包过程中的临时文件
-D, --onedir 默认值，生成dist文件夹
-F, --onefile 在dist文件夹中只生成独立的打包文件
-i <图标文件名.ico> 指定打包程序使用的图标(icon)文件
pyinstaller -F Text_progress_bar.py #打包exe
pyinstaller -F -w Text_progress_bar.py #不带控制台打包
pyinstaller -F -w chengzi.ico Text_progress_bar.py #打包指定exe图标
<https://app.xunjiepdf.com/img2icon/>链接转化成ico图片

# 数据
字符串反转
>>> a='123456789' 
>>> a = a[::-1]
