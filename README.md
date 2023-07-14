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

