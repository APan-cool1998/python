# python
# 下载 python 3.9  替换 3.6

    1. 先下载python3.9的依赖包
    yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel

    2. 下载python3.9安装包
    wget http://npm.taobao.org/mirrors/python/3.9.0/Python-3.9.0.tgz

    如果安装时，没有wget命令，使用yum -y install wget进行安装
    3. 如果下载时候没有进入/usr/local ，可以迁移文件到/usr/local

    mv Python-3.9.0.tgz /usr/local/

    输入cd /usr/local 进入local目录 输入

    tar -zxvf Python-3.9.0.tgz

    解压完成 进入cd python-3.9.0目录

    输入./configure prefix=/usr/local/python3 进行配置


    然后使用 make && make install 进行编译

    如果在编译出现报错：

    ModuleNotFoundError: No module named '_ctypes'

    make: *** [install] Error 1

    使用 yum install -y libffi-devel 安装后，重新进行配置和编译。

    4、添加快捷访问的方式 如需要 在虚拟环境下一般不用，直接创建一个虚拟环境的python版本就行

    ln -s /usr/local/python3/bin/python3.9 /usr/bin/python3
    不行使用
    ln -sf /usr/local/python3/bin/python3.9 /usr/bin/python3

    ln -s /usr/local/python3/bin/pip3.9 /usr/bin/pip3

    输入pip3 -V或者python3 -V查看版本

    # Linux or MacOS
    python -m ensurepip --upgrade

    # using python 3
    python3 -m ensurepip --upgrade

    # On Windows
    py -m ensurepip --upgrade

# 虚拟环境问题
    1.安装虚拟环境
    pip install virtualenv

    2.创建虚拟环境  以及指定版本去创建
    virtualenv -p /usr/bin/python3.9 env_adhd   指定版本

    python3.9 -m venv /opt/asd_vr_env


    3.激活虚拟环境
    source ./bin/active
    4.退出虚拟环境
    deactivate

    # 更新pip版本
    python -m pip install --upgrade pip


    pip install -r requirements.txt
    豆瓣源
   https://pypi.douban.com/simple/ scrapy

# nginx tips
     1.nginx 重启后有可能出现80端口被占用
      fuser -k 80/tcp
    2.修改了nginx文件后有可能出现 /run/nginx.pid 错误
      nginx -c /etc/nginx/nginx.conf 
    3.pip freeze > requirements.txt 出现一些路径问题
    使用 pip list --format=freeze > requirements.txt
    4.查看端口号是否被占用
    netstat -anp | grep 端口号
    查看端口号是否被占用
    5. fuser -k -n tcp 8080  
    杀死这个端口下所有
    6.
    SET FOREIGN_KEY_CHECKS = 0;   
    TRUNCATE TABLE 表名;  
    SET FOREIGN_KEY_CHECKS = 1; 

