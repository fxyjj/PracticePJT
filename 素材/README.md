# 第一步：把代码放在Github作版本控制
## 1: 在本地创建仓库（在终端进入项目文件夹，输入如下指令）

    `git init`

## 2: 查看文件夹中未追踪到的文件

    `git status`

## 3: 记录所有文件并准备将其上传
    
    `git add *`

## 4: commit 所有文件：
    
    `git commit -m "first commit"`

## 关联远程仓库（需知晓远程仓库的路径url）：
    `git remote add origin url`
    `git remote rm origin`  修改关联仓库
 
    `git remote -v`  查看关联情况

## 5: 上传

    `git push -u origin master`

## 6: 查看 git 日志
    
    `git log`

## 7:每次更新项目代码后记得要git最新版本的项目代码到github仓库
    `git add *`
    `git commit -m "date or n-th commit"`
    `git push -u origin master`

# (optional)第二步：使用 Anaconda 创建Python的虚拟环境
（更好的管理python的资源包，在电脑中独立成一个虚拟环境，与电脑中其他python文件包互不冲突，推荐使用）

## 创建虚拟环境

    `conda create -n env_name Python=version_number(2.x or 3.x)`
    
## 查看虚拟环境

    `conda env list`
    
## 激活与关闭虚拟环境

    `conda activate env_name` 进入虚拟环境
    `conda deactivate` 退出虚拟环境

# 第三步：环境搭建

## 安装 node.js

*网页搜索 node.js, 根据自己的电脑类型版本安装*

## 终端使用node.js 资源管理命令下载vue
    `npm install vue`
    `npm install @vue/cli` vue的项目脚手架，更多信息访问：https://cli.vuejs.org/zh/guide/

*建议使用cnpm安装脚手架，直接用上述命令会很慢*

    `npm install cnpm -g`
    `cnpm install -g @vue/cli`
    
*如果上述命令出错，请尝试使用管理员权限运行命令*：

    `sudo npm install cnpm -g` 
    
*终端提示输入管理员密码*

*你可以使用*

    `npm list` 
    
*来查看已安装的关于node.js的资源包*

~~## 新建Vue项目~~
  ~~  `vue ui`~~
    ~~打开vue图形界面，可以方便创建项目~~
    
~~按照ui提示创建完成后，进入项目文件夹，打开README 文件，依次执行提到的命令：~~

  ~~  `npm install`~~

   ~~ `npm run serve` 运行生产版本~~

~~or~~

    ~~`npm run dev` 运行开发版本~~

（此处大概率不会涉及项目在服务器上的部署，所以此处我们只用开发版本的指令）
## 新建Vue项目

    `sudo cnpm install -g @vue/cli-init`
    
    `cnpm install -g webpack`
    
    `vue init webpack pjt_name`

进入建好的文件夹，执行命令：

    `cnpm install`
    
    `npm run dev`
    

## --------------------- 至此，完成了前端的环境配置 ---------------------

    执行
    `npm run dev`
终端会有提示项目运行在本地的某个端口上，点击显示的url可以在浏览器打开看到效果。

## 新建Django 项目

首先要下载django环境包：

    `pip install django`  
    (与npm类似，可以使用 pip list 来查看python已下载的资源库)
    `python -m django --version` 查看django版本（此项目中使用的版本为3.1.7）

创建django项目：

    `django-admin startproject pjt_Name` (此处名字可自定义)
    
其次，修改django项目中的setting.py 和urls.py:
        
        `npm run build` 先将vue项目打包
        
> 修改 setting.py:
    TEMPLATES  -> 'DIRS': ['pjt_name/dist'] (这里需要填入你的vue项目中dist文件夹的路径) 
    
    新增：
    STATICFILES_DIRS = [
        os.path.join(BASE_DIR,"vue_fe/dist/static")
    ]
    
> 修改urls.py:

    `from django.contrib import admin`
    `from django.conf.urls import url`
    `from django.urls import path`
    `from django.views.generic.base import TemplateView`

    `urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'',TemplateView.as_view(template_name="index.html"))]`
        
    其中vue项目和django项目要在统一目录下，（不是最外层的django目录，而是在manage.py所在的画那一层目录）

最后，运行：
    
    `python manage.py runserver`
    
## -------------------- 至此，完成了前后端的搭建 ------------------------


# 第四步： 数据库连接

## 数据库权限问题：
### 关闭数据库 `sudo /usr/local/mysql/support-files/mysql.server stop`
### (在Mac下终端)使用mysql语句：`sudo /usr/local/mysql/bin/mysql -u root -p`
### 跳过密码验证：
     终端进入文件夹：`cd /usr/local/mysql/bin/`
     `sudo su`
     `./mysqld_safe --skip-grant-tables &`
     再次连接数据库 `sudo /usr/local/mysql/support-files/mysql.server stop`
### 数据库语句：
- `show databases;` 查看现存的数据库
- `create database db_name;` 创建数据库
- `drop database db_name;` 删除数据库
- `use db_name;` 选择数据库
- `show tables` 查看数据库中的表格
- `desc db_tb_name;` 显示表结构
- `drop table db_tb_name;` 删除表格
-- 修改数据库用户密码
- `use mysql`
- `update user set authentication_string=MD5(“你的新密码”) where user=“root”;`
- `flush privileges;` 权限刷新

## 下载 mysql 以及 mysql workbench

## 打开数据库服务器

## 为我们的项目创建一个新的数据库

## 下载 python中的mysql依赖包：
	`pip install pymysql`
由于 Django 使用MySQLdb库来连接MySQL数据库。但是MySQLdb不支持Python3.x版本，所以此处使用pymysql来代替MySQLdb
##  在setting.py 中设置：
	`DATABASES = {
    	'default': {
	        # 'ENGINE': 'django.db.backends.sqlite3',
	        # 'NAME': BASE_DIR / 'db.sqlite3',
	        'ENGINE': 'django.db.backends.mysql',
	        'NAME':'db_name',
	        'USER':'root',
	        'PASSWORD':'usr_pwd',
	        'HOST':'localhost',
        	'POST':'3306'
    	}
	}`
## 在 `__init__.py` 中写入：
	`import pymysql`

	`pymysql.install_as_MySQLdb()`

## ----------------- 至此，完成了环境的所有配置，可以开始进行项目了 ------------------

