#Jekyll安装配置及其相关问题

[TOC]

## **安装流程**

```shell
$ gem install bundler jekyll
$ jekyll new my-awesome-site
$ cd my-awesome-site
$ bundle exec jekyll serve
```



## 使用步骤

### [Setting up your GitHub Pages site locally with Jekylll](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll)

[Websites for you and your projects](https://pages.github.com/)



## **相关问题**

###Q1 无法找到 jekll 或 bundle

1）确认jekll或者bundle是否安装成功

```she
$ irb
>>>  require "jekyll"
# => true   

```

如果返回true才是安装成功，bundle也是类似操作检查是否已经安装。

如果没有安装成功，重新返回到安装步骤。

2）确认安装成功后，在bash_profile的PATH中加入jekll的bin目录， 通过如下命令查找bin目录

```shell
$ gem which jekyll
/Users/xxxx/.gem/ruby/2.3.0/gems/bundler-2.0.2/lib/bundler.rb 
#根据如上路径确认gem及ruby所在路径
$ ls /Users/xxxx/.gem/ruby/2.3.0/bin

```

3）把路径添加到profile中，在~/.bash_profile或类似profile文件中加入如下环境变量设置，并重新刷新profile

```sh
# GEM 环境变量设置
export GEMPATH=/Users/xxxx/.gem/ruby/2.3.0
export GEMBIN=$GEMPATH/bin
export PATH=$PATH:$GEMBIN
# 刷新profile
source ~/.bash_profile
```

然后就可以在命令行直接调用jekyll或者bundle了

###Q2 执行bundle exec jekyll serve

```shell
$ bundle exec jekyll serve
Could not find gem 'github-pages' in any of the gem sources listed in your Gemfile.
```

修改site路径下的Gemfile文件，添加相关的依赖，然后执行

```shell
$bundle install
```

