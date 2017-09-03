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

ModuleNotFoundError: No module named 'win32api'
```
$ pip install pypiwin32
```

# pyenv 使用
```
$ pyenv install -l  //可以安装的列表
$ pyenv install 3.5.4 // 安装的程序
$ pyenv global 3.5.4  // 全局版本
$ pyenv rehash        // 安装完成之后需要对数据库进行更新
$ pyenv versions      // 查看系统已安装的版本
$ pyenv local 3.5.4   // 指定目录的python版本
```
