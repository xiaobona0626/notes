# 安装python第三方包
1. pip from http://pypi.python.org/pypi/pip    用于安装python第三方包的工具
2. distribute from http://pypi.python.org/pypi/distribute    已被弃用，是SetupTools的一个分支，请参考SetupTools
3. nose from http://pypi.python.org/pypi/nose    扩展unittest，使得测试的编写、查找、运行更加方便
4. virtualenv from http://pypi.python.org/pypi/virtualenv    用于创建独立分离的python环境
5. 如何自动生成setup.py文件 http://blog.csdn.net/jianhong1990/article/details/7951606

### 安装virtualenvs 
```
pip install virtualenv
```

### Create Project
```
$ mkdir projectName
$ cd projectName
$ virtualenv --no-site-packages .env  或  python3 -m venv .env 
$ source .env/bin/activate
```


```
$ python -m venv .virtualenv
$ ve pip install -r requirements.txt
```
