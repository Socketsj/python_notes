# virtualenvwrapper的基本使用

### 1. 安装 virtualenvwrapper(需要先安装virtualenv)

    $ pip install virtualenvwrapper

### 2. 设置虚拟环境的存放目录(可将以下命令添加到shell启动文件中)

    $ export WORKON_HOME = 〜/venvs
    $ source /usr/local/bin/virtualenvwrapper.sh

### 3. 创建虚拟环境

    $ mkvirtualenv venv
    (venv)$

### 4. 查看虚拟环境目录下的所有环境

    $ workon

### 5. 切换到指定的虚拟环境

    $ workon venv

### 6. 退出虚拟环境

    $ deactivate

### 7. 删除虚拟环境

    $ rmvirtualenv venv

