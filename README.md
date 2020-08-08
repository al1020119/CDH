# Cloudera CDH集群离线安装脚本

## 更新记录
- [2020-08-08-08] 增加CDH5.16.2自动化安装脚本

## 快速开始

1. 准备数台全新安装的Linux Redhat7/CentOS7.x的服务器，我这里准备的是三台

    > 在/opt下建如下文件夹
    * software
    * module
    * scripts
    * ...

2. 安装常用依赖软件(有就不用安装)

    ```bash
    + yum install net-tools.x86_64
    + yum install vim
    + yum install wget
    ```

3. 克隆本项目到software中

    ```bash
    git clone https://github.com/abcfyk/setup_cdh.git
    ```

4. 分别下载两个安装文件并放置在本项目的packages目录下(体积较大，可选择第三方下载工具)

    ```bash
    wget -P /opt/software/setup_cdh/packages https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/5.16.2/RPMS/x86_64/cloudera-manager-daemons-5.16.2-1.cm5162.p0.7.el7.x86_64.rpm
    wget -P /opt/software/setup_cdh/packages http://archive.cloudera.com/cdh5/parcels/latest/CDH-5.16.2-1.cdh5.16.2.p0.8-el7.parcel 
    ```
5. 下载ORACLE JDK 1.8(只支持64bit版本，最低支持8u74，建议为8u181)

    ```bash
    wget -P setup_cdh/packages http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-linux-x64.tar.gz
    ```

> 建议直接进入package中使用 wget -c url 防止终端，从而可以进行断点传

> 由于这两个文件过大，Git对文件大小有限制，因此需要自己下载

> 其中jdk概率性失败，如果下载之后出现解压不了，建议自己去官网下载

6. 编辑根目录下的ip.list文件，填写集群节点的内网地址，每行一个

7. 上传本项目到集群任意一台服务器(建议在ip.list文件中的第一台服务器)，准备安装

8. 使用**ROOT**用户执行安装命令(非全自动安装，安装过程中会要求配置MySQL和输入集群其他服务器的root密码)

   ```bash
   cd setup_cdh && sh setup_cdh5.sh
   ```

## 参考

官网：https://www.cloudera.com/products/product-components/cloudera-manager.html

教程：https://www.cnblogs.com/jlmx/p/CDH_5_16_2_on_CentOS7.html





