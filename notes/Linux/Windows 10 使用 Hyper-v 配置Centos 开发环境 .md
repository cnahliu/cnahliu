#Windows 10 使用Hyper-v 搭建 Node.js 开发环境

##主要步骤
- Windows 10 安装 Hyper-v
- 配置Hyper-v 网络
- Hyper-v 安装 Centos 7
- Centos 7 配置Centos 网络 安装 Node.js、Oh My ZSH、PM2、Git、SSH
- Centos 配置 Samba


##Windows 10 安装 Hyper-v
1. 使用管理员权限打开PowerShell
2. 键入`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All`
3. 重启

##配置Hyper-v 网络
1. 进入Hyper-v 管理器，选择虚拟交换机管理器，选择`内部`类型并创建虚拟交换机
2. 进入网络共享中心选择可上网的本地适配器，右击属性后选择共享选项卡，
3. 勾选允许其他网络用户通过此计算机的Internet 连接来连接，并选择Hyper-v网卡(vEthernet)
4. 勾选允许其他网络网络用户控制或禁用共享的Internet 连接

##安装Centos 7
1. 下载镜像
`http://mirrors.163.com/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1611.iso
`
2. 过程略

##配置Cetnos 7 网络

1.编辑网卡配置

	```
	vi /etc/sysconfig/network-scripts/ifcfg-eth0
	```

	```
	BOOTPROTO=static
	ONBOOT=yes
	IPADDR=192.168.137.137
	NETMASK=255.255.255.0
	GATEWAY=192.168.137.1
	```

2. 重启网络配置

	```/etc/init.d/network restart```

3. 配置DNS

	```echo -e 'nameserver 114.114.114.114\nnameserver 223.5.5.5' > /etc/resolv.conf ```

4. 安装SSH、net-tools

	```yum install openssh-server net-tools
	

##配置Samba

1.安装依赖包

`yum install samba samba-client samba-common`

2.备份配置文件

`cp /etc/samba/smb.conf{.example,''}`
`
echo -e "
[Data]
\n comment = Data 
\n path = /data/
\n public = no
\n valid users = root
\n guest ok = no
\n writable = yes
\n browseable = yes
\n create mask = 0765
" >>/etc/samba/smb.conf
`
`
systemctl restart smb.service
`
`
systemctl restart nmb.service
`
3. 关闭SELlinux

`sed -i '/SELINUX/s/enforcing/disabled/' /etc/selinux/config`
`setenforce 0`

4. 关闭防火墙

`systemctl mask firewalld`

`systemctl stop firewalld`

5. 添加Samba用户

`smbpasswd -a root`

##更新Git
1. 安装编译依赖包并卸载可能存在的git

`yum groupinstall "Development Tools";yum install gettext-devel openssl-devel perl-CPAN perl-devel zlib-devel wget;yum remove git`

2. 下载最新的Git源码包

`wget https://github.com/git/git/archive/master.tar.gz`

3. 解压并编译

`tar -zxf master.tar.gz;cd git-master;make configure;./configure --prefix=/usr/local;make install;`

4. 校验Git版本(如果>2 则表明成功了)

`git --version`

##安装Nodejs
`curl --silent --location https://raw.githubusercontent.com/nodesource/distributions/master/rpm/setup_6.x | bash -;yum -y install nodejs`
##配置CNPM
` npm install -g cnpm --registry=https://registry.npm.taobao.org`