# zstack-ctl 命令 使用手册

### 产品版本 ： ZStack Cloud 5.5.0 文档版本 ： V5.5.0

## **版权声明**

版权所有 [©] 上海云轴科技股份有限公司 2026。保留一切权利。

非经本公司书面许可 ， 任何单位和个人不得擅自摘抄、复制本文档内容的部分或全部 ， 并不得以任

何形式传播。

**商标说明**

ZStack商标和其他云轴科技商标均为上海云轴科技股份有限公司的商标。

本文档提及的其他所有商标或注册商标 ， 由各自的所有人拥有。

**注意**

您购买的产品、服务或特性等应受云轴科技公司商业合同和条款的约束 ， 本文档中描述的全部或部

分产品、服务或特性可能不在您的购买或使用范围之内。除非合同另有约定 ， 云轴科技公司对本文

档内容不做任何明示或暗示的声明或保证。

由于产品版本升级或其他原因 ， 本文档内容会不定期进行更新。除非另有约定 ， 本文档仅作为使用

指导 ， 本文档中的所有陈述、信息和建议不构成任何明示或暗示的担保。

文档版本 ： V5.5.0 I

## **目录**

#### **版权声明.................................................................................................... I** **1 简介.........................................................................................................1** **2 ctl基础命令............................................................................................. 2**

2.1 status................................................................................................................................ 2

2.2 start...................................................................................................................................2

2.3 stop...................................................................................................................................2
2.4 start_ui..............................................................................................................................3
2.5 stop_ui.............................................................................................................................. 4
2.6 start_node.........................................................................................................................4
2.7 stop_node.........................................................................................................................5
2.8 restart_node......................................................................................................................5
2.9 configured_collect_log......................................................................................................5
2.10 dump_mysql................................................................................................................... 7
2.11 change_ip....................................................................................................................... 8
2.12 show_configuration.........................................................................................................8
2.13 configure.........................................................................................................................9
2.14 show_ui_config...............................................................................................................9
2.15 config_ui......................................................................................................................... 9
2.16 ui_status....................................................................................................................... 11
2.17 install_license............................................................................................................... 11
2.18 reset_password............................................................................................................ 11
2.19 change_mysql_password............................................................................................. 12
#### **3 ctl高级命令........................................................................................... 13**

3.1 install_management_node..............................................................................................13
3.2 upgrade_management_node..........................................................................................14
3.3 rollback_management_node.......................................................................................... 14
3.4 taillog.............................................................................................................................. 15
3.5 install_ui..........................................................................................................................15
3.6 install_db.........................................................................................................................15
3.7 upgrade_db.....................................................................................................................16
3.8 deploydb......................................................................................................................... 17
3.9 rollback_db..................................................................................................................... 17
3.10 clear_license.................................................................................................................18
3.11 restore_config...............................................................................................................18
3.12 save_config...................................................................................................................18
3.13 set_deployment............................................................................................................ 18
3.14 start_vdi........................................................................................................................ 19
3.15 stop_vdi........................................................................................................................ 20
3.16 vdi_status......................................................................................................................20
3.17 setenv........................................................................................................................... 20

3.18 unsetenv....................................................................................................................... 20

3.19 mysql_restrict_connection............................................................................................ 21
3.20 getenv...........................................................................................................................21
3.21 bootstrap.......................................................................................................................21
3.22 upgrade_ctl...................................................................................................................22
#### **术语表.....................................................................................................23**

II 文档版本 ： V5.5.0

## **1 简介**

CTL是ZStack Cloud独有的系统命令 ， 可以帮助用户完成多种系统设置。CTL下有多条子命令 ， 帮助用户
简化安装操作和环境配置 ， 把精力集中在ZStack Cloud的使用上。

本手册将详细介绍每条子命令的作用和使用方法。

文档版本 ： V5.5.0 1

## **2 ctl基础命令**

### **2.1 status**

**描述**

显示指定节点上ZStack Cloud状态和信息。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|none|显示当前节点的状态和信息|zstack-ctl status|
|--host HOST|显示指定节点的状态和信息|zstack-ctl status --host<br>192.168.0.10|

### **2.2 start**

**描述**

启动ZStack Cloud相关服务 ， 包括管理节点和UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|none|启动相关服务，包括管理节点<br>和UI服务|zstack-ctl start|
|--daemon|开启显示守护进程模式|zstack-ctl start --daemon|

### **2.3 stop**

**描述**

停止ZStack Cloud相关服务 ， 包括管理节点和UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|none|停止相关服务，包括管理节点<br>和UI服务|zstack-ctl stop|

2 文档版本 ： V5.5.0

### **2.4 start_ui**

**描述**

启动ZStack Cloud的UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|UI服务器IP，默认**localhost**|zstack-ctl start_ui --host<br>172.20.11.122|
|--mn-host MN_HOST|管理主机IP，默认_127.0.0.1_|zstack-ctl start_ui --mn-host<br>127.0.0.1|
|--mn-port MN_PORT|ZStack Cloud管理主机端<br>口，默认8080|zstack-ctl start_ui --mn-port<br>8080|
|--webhook-host WEBHOOK<br>_HOST|Webhook主机IP，默认_127.0.0_<br>_.1_|zstack-ctl start_ui --webhook-<br>host 127.0.0.1|
|--webhook-port WEBHOOK<br>_PORT|Webhook主机端口，默认5000|zstack-ctl start_ui --webhook-<br>port 5000|
|--server-port SERVER_PORT|UI服务器端口，默认5000|zstack-ctl start_ui --server-port<br>5000|
|--log LOG|UI日志文件夹，默认_/usr/local/_<br>_zstack/apache-tomcat/logs_|zstack-ctl start_ui --log /usr/<br>local/zstack/apache-tomcat/<br>logs|
|--enable-ssl|启用HTTPS登录UI|zstack-ctl start_ui --enable-ssl|
|--ssl-keyalias SSL_KEYALIAS|UI证书别名|zstack-ctl start_ui --ssl-keyalias<br>zstackui|
|--ssl-keystore SSL_KEY<br>STORE|UI证书路径，默认_/usr/local/_<br>_zstack/zstack-ui/ui.keystore_<br>_.p12_|zstack-ctl start_ui --ssl-<br>keystore /usr/local/zstack/<br>zstack-ui/ui.keystore.p12|
|--ssl-keystore-type SSL_KEY<br>STORE_TYPE|UI证书类型，默认**PKCS12**|zstack-ctl start_ui --ssl-<br>keystore-type PKCS12|
|--ssl-keystore-passwor<br>d SSL_KEYSTORE_P<br>ASSWORD|UI证书私钥密码，默<br>认**password**|zstack-ctl start_ui --ssl-<br>keystore-password password|
|--db-url DB_URL|UI数据库URL，默认_jdbc:mysql_<br>_://10.0.46.243:3306_|zstack-ctl start_ui --db-url<br>jdbc:mysql://10.0.46.243:3306|

文档版本 ： V5.5.0 3

|参数|介绍|示例|
|---|---|---|
|--db-username DB_USER<br>NAME|UI数据库用户名，默认**zstack_**<br>**ui**|zstack-ctl start_ui --db-<br>username zstack_ui|
|--db-password DB_PASS<br>WORD|UI数据库密码，默认**zstack.ui**<br>**.password**|zstack-ctl start_ui --db-<br>password zstack.ui.password|
|--timeout TIMEOUT|UI启动时间，默认为120s|zstack-ctl start_ui --timeout<br>120|

**注:** 请确保修改后的UI数据库用户名/密码能访问名为 **zstack_ui** 的数据库。

### **2.5 stop_ui**

**描述**

停止指定节点的UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|UI服务器IP，默认为localhost|zstack-ctl stop_ui --host<br>172.20.12.111|

### **2.6 start_node**

**描述**

启动指定节点上的ZStack Cloud管理节点服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定启动节点的SSH URL|zstack-ctl start_node --host<br>172.20.11.122|
|--timeout TIMEOUT|设置ZStack Cloud启动时<br>间，默认为300s|zstack-ctl start_node --timeout<br>600|
|--daemon|开启显示ZStack Cloud守护进<br>程模式|zstack-ctl start_node --daemon|
|--simulator|开启显示ZStack Cloud模拟器<br>模式|zstack-ctl start_node --<br>simulator|

4 文档版本 ： V5.5.0

### **2.7 stop_node**

**描述**

停止指定节点上的ZStack Cloud管理节点服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定停止节点的SSH URL|zstack-ctl stop_node --host<br>172.20.12.111|
|--force, -f|强制停止java进程|zstack-ctl stop_node --force|

### **2.8 restart_node**

**描述**

重启管理节点。

|参数|介绍|示例|
|---|---|---|
|none|重启管理节点|zstack-ctl restart_node|

### **2.9 configured_collect_log**

**描述**

收集诊断命令。用于新日志收集 ， 支持预览日志大小 ， 用户可根据需求 ， 选择不同参数自定义收集

某时间段日志、单独收集管理节点/数据库/计算节点日志、全部日志等。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|-p|自定义收集日志的yaml配置文<br>件路径|zstack-ctl<br>configured_collect_log -p /var/<br>lib/zstack/|
|--check|仅查询并展示收集日志大<br>小，不进行日志收集操作|zstack-ctl<br>configured_collect_log --check|
|--full|默认模式，收集除数据库日志<br>以外的所有日志，包括：管理<br>节点日志、计算节点日志、镜<br>像服务器日志、主存储日志、<br>路由器日志|zstack-ctl<br>configured_collect_log --full|

文档版本 ： V5.5.0 5

|参数|介绍|示例|
|---|---|---|
|--full-db|收集包括数据库日志在内的所<br>有日志|zstack-ctl<br>configured_collect_log --full-db|
|--mn-db|收集管理节点日志（包含数据<br>库日志）|zstack-ctl<br>configured_collect_log --mn-db|
|--mn-only|仅收集管理节点日志（不包括<br>数据库日志）|zstack-ctl<br>configured_collect_log --mn-<br>only|
|--mn-host|收集管理节点和计算节点日<br>志（不包括数据库日志）|zstack-ctl<br>configured_collect_log --mn-<br>host|
|--since SINCE|收集N天内（Nd）或者N小时<br>内（Nh）的日志|zstack-ctl<br>configured_collect_log --since<br>2d|
|--from-date FROM_DATE|•<br>日志收集起始时间，支持格<br>式：<br>◦<br>yyyy-MM-dd：仅设置年<br>月日，时分秒默认为0<br>，例如：2018-11-22，代<br>表2018-11-22 00:00:00<br>◦<br>yyyy-MM-dd_hh:mm:ss<br>：设置具体时间，精确<br>到秒，例如：2018-11<br>-22_09:30:00<br>•<br>若仅设置FROM_DATE，收<br>集FROM_DATE到当前时间<br>的日志<br>•<br>若FROM_DATE设置为-1<br>，将收集截止时间前的所有<br>日志|zstack-ctl<br>configured_collect_log --from-<br>date 2018-11-22|
|--to-date TO_DATE|•<br>日志收集截止时间，格式同<br>上<br>•<br>若仅设置TO_DATE，默<br>认FROM_DATE为当前时间<br>前24小时|zstack-ctl<br>configured_collect_log --to-<br>date 2018-11-23|

6 文档版本 ： V5.5.0

### **2.10 dump_mysql**

**描述**

转存数据库到备份文件。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--file-name FILE_NAME|设置备份数据库文件的名<br>字，默认为**zstack-backup-db**<br>**注:**<br>•<br>系统会自动为备份的<br>数据库文件添加管理<br>节点IP作为前缀，若<br>为双管环境，则IP地<br>址为VIP所在管理<br>节点的IP。同时添<br>加备份日期和时<br>间作为后缀。例<br>如，**172.20.1.123-**<br>**zstack-backup-db**<br>**-2016-12-07_14-43**<br>**-43.gz**表示管理节<br>点172.20.1.123在201<br>进行的数据库备份。|6年12月7日14点43分43秒<br>zstack-ctl dump_mysql --file-<br>name 'zstack-backup-db'|
|--file-path FILE_PATH|设置备份数据库文件保存的绝<br>对路径，默认为_/var/lib/zstack/_<br>_mysql-backup_|zstack-ctl dump_mysql --file-<br>path '/var/lib/zstack/mysql-<br>backup'|
|--keep-amount KEEP_AM<br>OUNT|设置备份数据库保留的个<br>数，超出阈值的旧备份文件将<br>被删除，默认为60|zstack-ctl dump_mysql --keep-<br>amount 50|
|--host-info HOST_INFO|设置异地数据库和UI数据备份<br>的目的主机信息，格式为**root**<br>**@ip_address:port**<br>•<br>异地备份远端主机目录为_/_<br>_var/lib/zstack/from-zstack-_<br>_remote-backup/_。<br>•<br>默认端口为22。|zstack-ctl dump_mysql --host-<br>info root@172.20.0.30:22|
|--host HOST_INFO|--host HOST_INFO|zstack-ctl dump_mysql --host<br>root@172.20.0.30:22|
|--h HOST_INFO|--h HOST_INFO|zstack-ctl dump_mysql --h<br>root@172.20.0.30:22|

文档版本 ： V5.5.0 7

|参数|介绍|示例|
|---|---|---|
|--delete-expired-file|删除异地主机_/var/lib/zstack/_<br>_from-zstack-remote-backup/_目<br>录下的过期文件。|zstack-ctl dump_mysql --<br>delete-expired-file|
|--delete|--delete|zstack-ctl dump_mysql --delete|
|--d|--d|zstack-ctl dump_mysql --d|
|--append-sql-file APPEND_<br>SQL_FILE|附加SQL语句文件对数据库进<br>行操作|zstack-ctl dump_mysql --<br>append-sql-file SQL_File|

### **2.11 change_ip**

**描述**

从ZStack Cloud配置文件中更新管理IP。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--ip IP|为管理节点设置一个新<br>的IP，新的IP会自动同步<br>到ZStack Cloud的配置文件中<br>**注: ** 如果修改了当前<br>管理节点的操作系<br>统IP，可以用该命令自<br>动修改所有和ZStack<br>Cloud相关的配置文件<br>的IP地址为新的IP地址|zstack-ctl change_ip --ip<br>172.20.12.47|
|--mysql_ip MYSQL_IP|为数据库设置一个新的IP，默<br>认与管理节点IP相同|zstack-ctl change_ip --<br>mysql_ip 172.20.12.47|
|--cloudbus_server_ip<br> CLOUDBUS_SERVER_IP|为消息总线设置一个新的IP<br>，默认与管理节点IP相同|zstack-ctl change_ip<br>--cloudbus_server_ip<br>172.20.12.47|

### **2.12 show_configuration**

**描述**

显示ZStack Cloud配置文件 **zstack.properties** 的信息。

8 文档版本 ： V5.5.0

|参数|介绍|示例|
|---|---|---|
|none|显示ZStack Cloud配置文<br>件**zstack.properties**的信息|zstack-ctl show_configuration|

### **2.13 configure**

**描述**

修改ZStack Cloud配置文件。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|设置管理节点的IP或者域<br>名，默认为localhost|zstack-ctl configure --host<br>root@192.168.0.10|
|--duplicate-to-remote<br> DUPLICATE_TO_REMOTE|同步本节点的配置文件到远程<br>节点|zstack-ctl configure --duplicate-<br>to-remote root@192.168.0.10|
|--use-file USE_FILE|设置配置文件的位置|zstack-ctl configure --use-<br>file /usr/local/zstack/apache-<br>tomcat/webapps/zstack/WEB-<br>INF/classes/zstack.properties|

### **2.14 show_ui_config**

**描述**

显示UI配置 ， 例如服务端口等。

|参数|介绍|示例|
|---|---|---|
|none|显示UI配置，例如服务端口等|zstack-ctl show_ui_config|

### **2.15 config_ui**

**描述**

配置UI地址和端口等。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|UI服务器IP，默认**localhost**|zstack-ctl config_ui --host<br>172.20.11.122|

文档版本 ： V5.5.0 9

|参数|介绍|示例|
|---|---|---|
|--init|初始化**zstack.ui.properties**|zstack-ctl config_ui --init|
|--restore|重置**zstack.ui.properties**，恢<br>复默认设置|zstack-ctl config_ui --restore|
|--mn-host MN_HOST|ZStack Cloud管理主机IP，默<br>认_127.0.0.1_|zstack-ctl config_ui --mn-host<br>127.0.0.1|
|--mn-port MN_PORT|ZStack Cloud管理主机端<br>口，默认8080|zstack-ctl config_ui --mn-port<br>8080|
|--webhook-host WEBHOOK<br>_HOST|Webhook主机IP，默认_127.0.0_<br>_.1_|zstack-ctl config_ui --webhook-<br>host 127.0.0.1|
|--webhook-port WEBHOOK<br>_PORT|Webhook主机端口，默认5000|zstack-ctl config_ui --webhook-<br>port 5000|
|--server-port SERVER_PORT|UI服务器端口，默认5000|zstack-ctl config_ui --server-<br>port 5000|
|--ui-address UI_ADDRESS|修改UI服务器IP|zstack-ctl config_ui --ui-<br>address 172.20.0.10|
|--log LOG|UI日志文件夹，默认_/usr/local/_<br>_zstack/apache-tomcat/logs_|zstack-ctl config_ui --log /usr/<br>local/zstack/apache-tomcat/<br>logs|
|--enable-ssl {True,False}|启用/关闭HTTPS登录UI，默<br>认**False**|zstack-ctl config_ui --enable-<br>ssl True|
|--ssl-keyalias SSL_KEYALIAS|UI证书别名，默认**zstackui**|zstack-ctl config_ui --ssl-<br>keyalias zstackui|
|--ssl-keystore SSL_KEY<br>STORE|UI证书路径，默认_/usr/local/_<br>_zstack/zstack-ui/ui.keystore_<br>_.p12_|zstack-ctl config_ui --ssl-<br>keystore /usr/local/zstack/<br>zstack-ui/ui.keystore.p12|
|--ssl-keystore-type {PKCS12<br>,JKS}|UI证书类型，默认**PKCS12**|zstack-ctl config_ui --ssl-<br>keystore-type PKCS12|
|--ssl-keystore-passwor<br>d SSL_KEYSTORE_P<br>ASSWORD|UI证书私钥密码，默<br>认**password**|zstack-ctl config_ui --ssl-<br>keystore-password password|
|--db-url DB_URL|UI数据库URL，默认_jdbc:mysql_<br>_://10.0.46.243:3306_|zstack-ctl config_ui --db-url<br>jdbc:mysql://10.0.46.243:3306|
|--db-username DB_USER<br>NAME|UI数据库用户名，默认**zstack_**<br>**ui**|zstack-ctl config_ui --db-<br>username zstack_ui|

10 文档版本 ： V5.5.0

|参数|介绍|示例|
|---|---|---|
|--db-password DB_PASS<br>WORD|UI数据库密码，默认**zstack.ui**<br>**.password**|zstack-ctl config_ui --db-<br>password zstack.ui.password|

**注:** 请确保修改后的UI数据库用户名/密码能访问名为 **zstack_ui** 的数据库。

### **2.16 ui_status**

**描述**

检查指定节点UI服务状态。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定查看UI服务器IP，默认<br>为localhost|zstack-ctl ui_status --host<br>172.20.11.12|

### **2.17 install_license**

**描述**

安装ZStack Cloud的 license， 安装完成后需要在UI上刷新。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--license LICENSE, -f<br> LICENSE|指定license文件的完整路径|zstack-ctl install_license<br>--license /root/trailext-<br>license-100days-6hosts.txt|
|--prikey PRIKEY|（可选）指定产生license私钥<br>的路径|zstack-ctl install_license --<br>prikey /root/tmp|

### **2.18 reset_password**

**描述**

重设ZStack Cloud超级管理员 （admin） 的密码。

文档版本 ： V5.5.0 11

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--password PASSWORD|重设ZStack Cloud超级管理员<br>的密码，如果不设置，默认密<br>码为password|zstack-ctl reset_password --<br>password 123456|

### **2.19 change_mysql_password**

**描述**

更改mysql数据库密码。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--root-password ROOT_PA<br>SSWORD, -root ROOT_PA<br>SSWORD|原有的mysql root密码|zstack-ctl<br>change_mysql_password --<br>root-password oldpswd|
|--user-name USER_NAME, -<br>user USER_NAME|需要改变密码的用户名|zstack-ctl<br>change_mysql_password --<br>user-name root|
|--new-password NEW_PAS<br>SWORD, -new NEW_PAS<br>SWORD|需要设置的新密码|zstack-ctl<br>change_mysql_password --<br>new-password newpswd|
|--remote-ip REMOTE_IP, -ip<br> REMOTE_IP|如果想更改远程数据库密<br>码，需要设置远程IP。|zstack-ctl<br>change_mysql_password --<br>remote-ip 10.0.0.2|

12 文档版本 ： V5.5.0

## **3 ctl高级命令**

### **3.1 install_management_node**

**描述**

按照配置文件在当前节点或者远端节点安装ZStack Cloud管理节点 ， 请在配置好当前节点后安装其

他节点。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定安装管理节点的IP|zstack-ctl<br>install_management_node --<br>host 172.20.12.111|
|--install-path INSTALL_PATH|指定安装管理节点的路径，默<br>认为：_/usr/local/zstack_|zstack-ctl<br>install_management_node --<br>install-path /usr/local/zstack|
|--source-dir SOURCE_DIR|指定Apache Tomcat安装包的<br>路径，默认安装在_/usr/local/_<br>_zstack/apache-tomcat/_|zstack-ctl<br>install_management_node --<br>source-dir /usr/local/zstack/<br>apache-tomcat/|
|--debug|开启显示Ansible调试|zstack-ctl<br>install_management_node --<br>debug|
|--force-reinstall|删除已存在的Apache Tomcat<br>，重新安装管理节点|zstack-ctl<br>install_management_node --<br>force-reinstall|
|--yum YUM|使用ZStack Cloud预定义<br>的yum源。 可用的包括：<br>alibase、aliepel、163base、ust<br>local|cepel、zstack-<br>zstack-ctl<br>install_management_node --<br>yum 163base|
|--ssh-key SSH_KEY|设置SSH登录的私钥路径|zstack-ctl<br>install_management_node --<br>ssh-key /root/.ssh/id_rsa|

文档版本 ： V5.5.0 13

### **3.2 upgrade_management_node**

**描述**

管理节点升级到指定版本。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定升级节点的SSH URL|zstack-ctl<br>upgrade_management_node --<br>host 172.20.31.34|
|--war-file WAR_FILE|设置zstack.war包的URL，可以<br>是http URL或者本地的完整路<br>径|zstack-ctl<br>upgrade_management_node<br>--war-file /usr/local/zstack/<br>zstack.war|
|--debug|开启显示Ansible调试|zstack-ctl<br>upgrade_management_node --<br>debug|
|--ssh-key SSH_KEY|设置SSH登录的私钥路径|zstack-ctl<br>upgrade_management_node --<br>ssh-key /root/.ssh/id_rsa|

### **3.3 rollback_management_node**

**描述**

如果升级失败 ， 可以使用此命令回滚管理节点的状态。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定回滚管理节点的IP|zstack-ctl<br>rollback_management_node --<br>host 172.20.12.111|
|--war-file WAR_FILE|设置**zstack.war**包的URL，可以<br>是http URL或者本地的完整路<br>径|zstack-ctl<br>rollback_management_node<br>--war-file /usr/local/zstack/<br>zstack.war|
|--debug|开启显示Ansible调试|zstack-ctl<br>rollback_management_node --<br>debug|

14 文档版本 ： V5.5.0

|参数|介绍|示例|
|---|---|---|
|--ssh-key SSH_KEY|设置SSH登录的私钥路径|zstack-ctl<br>rollback_management_node --<br>ssh-key /root/.ssh/id_rsa|
|--property-file PROPERT<br>Y_FILE|指定回滚时的ZStack Cloud配<br>置文件|zstack-ctl<br>rollback_management_node --<br>property-file /usr/local/zstack/<br>apache-tomcat/webapps/<br>zstack/WEB-INF/classes/<br>zstack.properties|

### **3.4 taillog**

**描述**

显示管理节点日志更新。

|参数|介绍|示例|
|---|---|---|
|none|显示管理节点日志更新|zstack-ctl taillog|

### **3.5 install_ui**

**描述**

安装ZStack Cloud UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|指定节点安装ZStack Cloud<br>UI服务。<br>默认安装在本节点上|zstack-ctl install_ui --host<br>172.20.12.144|
|--ssh-key SSH_KEY|后面参数为私钥的完整路<br>径，Ansible将自动登录到指定<br>节点进行部署|zstack-ctl install_ui --ssh-key /<br>root/.ssh/id_rsa|

### **3.6 install_db**

**描述**

安装ZStack Cloud数据库。

文档版本 ： V5.5.0 15

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--host HOST|设置数据库服务器的IP或者域<br>名，默认为localhost|zstack-ctl install_db --host|
|--root-password ROOT_PA<br>SSWORD|为MySQL root用户设置新的密<br>码|zstack-ctl install_db --root-<br>password|
|--login-password LOGIN_P<br>ASSWORD|为MySQL设置原始登录密码|zstack-ctl install_db --login-<br>password password1|
|--yum YUM|使用ZStack Cloud预定义<br>的yum源。 可用的包括：<br>alibase、aliepel、163base、ust<br>local|cepel、zstack-<br>zstack-ctl install_db --yum<br>163base|
|--no-backup NO_BACKUP|如果你的数据库很大，你希望<br>手动备份，那么可以用此命令<br>关闭它。默认会自动备份，默<br>认为false|zstack-ctl install_db --no-<br>backup|
|--ssh-key SSH_KEY|设置SSH登录的私钥路径|zstack-ctl install_db --ssh-key /<br>root/.ssh/id_rsa|

### **3.7 upgrade_db**

**描述**

将数据库从当前版本升级到新的版本。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--force|更新数据库，不检查管理节点<br>的状态|zstack-ctl upgrade_db --force|
|--no-backup NO_BACKUP|如果你的数据库很大，你希望<br>手动备份，那么可以用此命令<br>关闭它。默认会自动备份，默<br>认为false|zstack-ctl upgrade_db --no-<br>backup|
|--dry-run|检查数据库是否可以升级|zstack-ctl upgrade_db --dry-<br>run|

16 文档版本 ： V5.5.0

### **3.8 deploydb**

**描述**

配置ZStack Cloud数据库。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--root-password ROOT_PA<br>SSWORD|创建一个mysql root用户，并设<br>置密码|zstack-ctl deploydb --root-<br>password root123|
|--zstack-password ZSTACK_<br>PASSWORD|创建一个新的用户**ZStack**，并<br>设置密码|zstack-ctl deploydb --zstack-<br>password zstack123|
|--host HOST|设置数据库服务器的IP或者域<br>名，默认为localhost|zstack-ctl deploydb --host<br>172.20.11.133|
|--port PORT|设置MySQL端口，默认为3306|zstack-ctl deploydb --port 3300|
|--no-update|不更新数据库信息到配置文件|zstack-ctl deploydb --no-<br>update|
|--drop|删除已存在的数据库|zstack-ctl deploydb --drop|
|--keep-db|保持已存在的数据库不再更新<br>信息|zstack-ctl deploydb --keep-db|

### **3.9 rollback_db**

**描述**

如果升级失败 ， 可以使用此命令回滚数据库的状态。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--db-dump DB_DUMP|指定要恢复的备份文件|zstack-ctl rollback_db --db-<br>dump /zstackdb/backupdb.bk|
|--root-password ROOT_PA<br>SSWORD|Mysql root密码 默认为空|zstack-ctl rollback_db --root-<br>password password|
|--force|忽略检查管理节点的状态<br>**注: ** 慎用，你应该充分<br>了解它的后果|zstack-ctl rollback_db --force|

文档版本 ： V5.5.0 17

### **3.10 clear_license**

**描述**

清除和备份ZStack Cloud许可证文件。

### **3.11 restore_config**

**描述**

从指定文件夹中的配置文件来恢复ZStack Cloud ， 包括zstack.properties和ssh host的密钥等。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--restore-from RESTORE<br>_FROM|指定需要使用的配置文件的路<br>径|zstack-ctl restore_config --<br>restore-from /usr/local/zstack/<br>apache-tomcat/webapps/<br>zstack|

### **3.12 save_config**

**描述**

保存ZStack Cloud配置文件到ZSTACK_HOME指定的路径下。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--save-to SAVE_TO|指定ZStack Cloud配置文件的<br>路径|zstack-ctl save_config --save-<br>to /usr/local/zstack/apache-<br>tomcat/webapps/zstack|

### **3.13 set_deployment**

**描述**

设置ZStack Cloud集群部署资源的规模。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--size|指定ZStack Cloud集群部<br>署资源的规模，包括：<br>small、large、medium、default|。<br>zstack-ctl set_deployment --<br>size small|

18 文档版本 ： V5.5.0

**场景实践**

从3.10.0版本开始 ， ZStack Cloud支持指定集群部署资源规模 ， 按照不同的规模为集群分配不同的

属性值 ， 分为default、small、medium、large四个场景 ， 其中default为默认规模。

不同规模下的属性值如下 ：

|属性配置|Default|Small|Medium|Large|
|---|---|---|---|---|
|已有属性：<br>DbFacadeDataSo<br>urce.maxPool<br>Size|100|64|128|128|

不同资源数量的推荐规模如下 ：

   - **default** ： 默认环境 ， 物理机数量50台以内时无需设置 ；

   - **small** ： 小型环境 ， 物理机数量100以内 ， 或云主机数量1000以内推荐使用该设置 ；

   - **medium** ： 中型环境 ， 物理机数量400以内 ， 或云主机数量4000以内推荐使用该设置 ；

   - **large** ： 大型环境 ， 物理机数量1000以内 ， 或云主机数量10000以内推荐使用该设置。

### **3.14 start_vdi**

**描述**

启动ZStack Cloud的VDI组件的UI服务。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--mn-port MN_PORT|ZStack Cloud管理节点端<br>口，默认8080|zstack-ctl start_vdi --mn-port<br>8000|
|--webhook-port WEBHOOK<br>_PORT|Webhook节点端口，默认9000|zstack-ctl start_vdi --webhook-<br>port 9050|
|--server-port SERVER_PORT|UI服务端口，默认9000|zstack-ctl start_vdi --server-<br>port 9050|
|--vdi-path VDI_PATH|VDI路径，默认_/opt/zstack-dvd/_<br>_zstack-vdi.war_|zstack-ctl start_vdi --vdi-path /<br>opt/root/zstack-vdi.war|
|--log LOG|UI日志文件夹，默认_/usr/local/_<br>_zstack/apache-tomcat/logs_|zstack-ctl start_vdi --log /usr/<br>log/logs|

文档版本 ： V5.5.0 19

### **3.15 stop_vdi**

**描述**

停止本地节点的vdi服务。

|参数|介绍|示例|
|---|---|---|
|none|停止本地节点的vdi服务|zstack-ctl stop_vdi|

### **3.16 vdi_status**

**描述**

在本地节点查询VDI服务状态。

|参数|介绍|示例|
|---|---|---|
|none|在本地节点查询VDI服务状态|zstack-ctl vdi_status|

### **3.17 setenv**

**描述**

在zstack-ctl变量文件 _/usr/local/zstack/zstack-ctl/ctl-env_ 中设置变量。

|参数|介绍|示例|
|---|---|---|
|none|在zstack-ctl变量文件_/usr/local/_<br>_zstack/zstack-ctl/ctl-env_中设置<br>变量|zstack-ctl setenv|

### **3.18 unsetenv**

**描述**

在zstack-ctl变量文件 _/usr/local/zstack/zstack-ctl/ctl-env_ 中取消设置变量。

|参数|介绍|示例|
|---|---|---|
|none|在zstack-ctl变量文件_/usr/local/_<br>_zstack/zstack-ctl/ctl-env_中取消<br>设置变量|zstack-ctl unsetenv|

20 文档版本 ： V5.5.0

### **3.19 mysql_restrict_connection**

**描述**

对管理节点的数据库账号设置白名单策略 ， 开启后 ， 仅允许数据库所在的管理节点可以访问数据

库 ， 其他非管理节点的路径无法访问数据库。

|参数|介绍|示例|
|---|---|---|
|--restrict|开启白名单策略，限制数据库<br>访问|zstack-ctl<br>mysql_restrict_connection<br>--root-password<br>zstack.mysql.password --<br>restrict|
|--restore|恢复策略，不限制数据库访问|zstack-ctl<br>mysql_restrict_connection<br>--root-password<br>zstack.mysql.password --<br>restore|

### **3.20 getenv**

**描述**

从 _/usr/local/zstack/zstack-ctl/ctl-env_ 获取变量。

|参数|介绍|示例|
|---|---|---|
|none|从_/usr/local/zstack/zstack-ctl/_<br>_ctl-env_获取变量|zstack-ctl getenv|

### **3.21 bootstrap**

**描述**

创建ZStack Cloud用户和用户组并添加到sudoers。

|参数|介绍|示例|
|---|---|---|
|none|创建ZStack Cloud用户和用户<br>组并添加到sudoers|zstack-ctl bootstrap|

文档版本 ： V5.5.0 21

### **3.22 upgrade_ctl**

**描述**

升级zstack-ctl命令到新的版本。

**使用方法**

|参数|介绍|示例|
|---|---|---|
|--package PACKAGE|指定zstack-ctl安装包路径|zstack-ctl upgrade_ctl<br>--package ./apache-<br>tomcat-7.0.35/webapps/<br>zstack/WEB-INF/classes/tools/<br>zstackctl-1.8.tar.gz|

22 文档版本 ： V5.5.0

## **术语表**

### **实例**

云平台中运行操作系统镜像的虚拟机或服务器 ， 如云主机、弹性裸金属实例。

### 云主机 （VM Instance）

运行在物理机上的虚拟机实例 ， 具有独立的IP地址 ， 可以访问公共网络 ， 运行应用服务。

### 云盘 （Volume）

为云主机提供存储 ， 包括两种类型 ： 根云盘、数据云盘。

### 根云盘 （Root Volume）

云主机的系统云盘 ， 用于支撑云主机的系统运行。

### 数据云盘 （Data Volume）

云主机的数据云盘 ， 用于云主机扩展的存储使用。

### 镜像 （Image）

云主机或云盘使用的镜像模板文件 ， 包括两种类型 ： 系统镜像、云盘镜像。

### 计算规格 （Instance Offering）

云主机涉及的CPU数量、内存、网络设置等规格定义。

### 云盘规格 （Disk Offering）

云盘涉及的容量大小的规格定义。

### SSH密钥 （SSH Key）

SSH密钥是一种安全的云主机登录认证方式 ， 由一个公钥和一个私钥组成。仅Linux云主机支持通

过SSH密钥登录。

### GPU规格 （GPU Specification）

物理GPU设备或vGPU设备涉及的GPU帧数、显存、分辨率等规格定义 ， 包括两种类型 ： 物理GPU

规格、vGPU规格。

文档版本 ： V5.5.0 23

### vNUMA配置 （vNUMA Configuration）

通过CPU绑定透传关联的物理机NUMA节点 （pNUMA Node ） 拓扑 ， 为云主机生成vNUMA节

点 （vNUMA Node ） 拓扑 ， 实现云主机CPU优先访问所在vNUMA节点本地内存 ， 提高云主机性能。

### NUMA（Non- Uniform Memory Access）

非一致性内存访问 ， 是一种计算机内存设计架构。该架构下 ，CPU 访问内存的时间取决于CPU与内

存的相对位置。通过优先访问相对位置较近的内存可缩短延迟 ， 从而可提升主机系统性能。

### pNUMA节点 （pNUMA Node）

基于物理机NUMA架构预定义的NUMA节点 ， 用于物理机CPU和内存管理。

### pNUMA拓扑 （pNUMA Topology）

CPU厂商基于NUMA架构预定义的物理机NUMA节点拓扑。

### vNUMA节点 （vNUMA Node）

基于CPU绑定透传关联的物理机NUMA节点而生成的云主机NUMA节点 ， 用于云主机CPU和内存管

理。

### vNUMA拓扑 （vNUMA Topology）

基于CPU绑定生成的云主机NUMA节点 （vNUMA Node ） 拓扑。

### 本地内存 （Local Memory）

CPU （pCPU 或vCPU ） 通过所在NUMA节点 （pNUMA 节点或vNUMA节点 ） 非CPU核部件中内存控制

器可直接访问的内存。相比非本地内存 ，CPU 访问本地内存的延迟更低。

### CPU绑定配置 （CPU Pinning）

将云主机的虚拟CPU （vCPU） 与物理机的物理CPU （pCPU） 严格关联 ， 可为云主机分配特定

的pCPU ， 提高云主机性能。

### EmulatorPin配置 （EmulatorPin Configuration）

将云主机中除vCPU和IO线程外的其他线程与物理机pCPU进行绑定 ， 使云主机相关线程只运行在对

应的pCPU上。

24 文档版本 ： V5.5.0

### 弹性伸缩组 （Auto Scaling Group）

一组具有相同应用场景的云主机集合 ， 可根据用户业务变化自动实现弹性伸缩或弹性自愈。

### 快照 （Snapshot）

某一时间点某一磁盘的数据状态文件。

### 云主机调度策略 （VM Scheduling Policy）

为云主机分配物理机的资源编排策略 ， 可用于保障业务的高性能和高可用。

### 区域 （Zone）

云平台内最大的一个资源定义 ， 包括 ： 集群、二层网络、主存储等资源。

### 集群 （Cluster）

一组物理机 （ 计算节点 ） 的逻辑集合。

### 物理机 （Host）

为云主机实例提供计算、网络、存储等资源的物理主机。

### 主存储 （Primary Storage）

用于存储云主机磁盘文件 （ 包括 ： 根云盘、数据云盘、根云盘快照、数据云盘快照、镜像缓存

等 ） 的存储服务器。

### 镜像服务器 （Backup Storage）

用于存储云主机镜像模板 （ 含ISO ） 的存储服务器。

### iSCSI存储 （iSCSI Storage）

基于iSCSI协议构建的SAN存储。用户可将iSCSI存储上划分的块设备添加为Shared Block主存

储 ， 或直接透传给云主机使用。

### FC存储 （FC Storage）

基于FC协议构建的SAN存储。用户可将FC存储上划分的块设备添加为Shared Block主存储 ， 或直

接透传给云主机使用。

文档版本 ： V5.5.0 25

### NVMe存储 （NVMe Storage）

基于NVMe-oF协议构建的存储阵列 ， 用户可将NVMe存储上划分的块设备添加为Shared Block主存

储。

### 二层网络 （L2 Network）

对应于一个二层广播域 ， 进行二层相关的隔离。一般用物理网络的设备名称标识。

### VXLAN网络池 （VXLAN Pool）

在一组VXLAN隧道端点 （VTEP） 之上创建的VXLAN网络的集合 ， 同一个VXLAN网络池内VXLAN网

络标识符 （VNI） 不能重复。

### 三层网络 （L3 Network）

云主机使用的网络配置 ， 包括IP地址范围、网关、DNS等。

### 公有网络 （Public Network）

一般表示可直接访问互联网的网络 ， 由于公有网络是一个逻辑概念 ， 在无法连接互联网的环境

中 ， 用户也可以自定义该网络。

### 扁平网络 （Flat Network）

可与物理机网络直通 ， 也可直接访问互联网的网络。云主机可使用扁平网络提供的分布式EIP访问

公有网络。

### VPC网络 （VPC Network）

云主机使用的私有网络 ， 可通过VPC路由器访问互联网。

### 管理网络 （Management Network）

管理控制云平台相关物理资源的网络 ， 例如 ： 配置访问物理机、主存储、镜像服务器、VPC路由器

时使用的网络。

### 流量网络 （Flow Network）

端口镜像的专用网络 ， 用于将网卡的网络流量镜像到远端。

### VPC路由器 （VPC vRouter）

一个定制的云主机 ， 用于提供多种网络服务。

26 文档版本 ： V5.5.0

### VPC路由器高可用组 （VPC vRouter HA Group）

一对互为主备的VPC路由器 ， 当主VPC路由器状态异常 ， 自动切换至备VPC路由器 ， 为业务高可用

提供保障。

### 路由器镜像 （vRouter Image）

封装网络服务 ， 用于创建VPC路由器。路由器镜像不能直接用于创建业务云主机。

### VPC路由器镜像 （VPC vRouter Image）

封装了多种网络服务 ， 只能用于创建VPC路由器 ， 不能直接用于创建业务云主机。

### 高性能实例型负载均衡镜像 （LB Image）

封装了高性能实例型负载均衡服务 ， 只能用于创建负载均衡实例 ， 不能直接用于创建业务云主机。

### 路由器规格 （vRouter Offering）

定义VPC路由器使用的CPU、内存、镜像、管理网络、公有网络配置 ， 用于创建VPC路由器 ， 为公

有网络/VPC网络提供多种网络服务。

### 负载均衡实例规格 （LB Offering）

定义负载均衡实例使用的CPU、内存、镜像、管理网络配置 ， 用于创建负载均衡实例 ， 为公有网

络/扁平网路/VPC网络提供负载均衡服务。

### SDN控制器 （SDN Controller）

SDN控制器是SDN架构的核心 ， 负责集中管理和控制网络设备。

### SDN集群 （SDN Cluster）

一组由定制云主机构成的集群 ， 用于提供高可用的 SDN 能力。

### SDN实例 （SDN Instance）

一台定制的云主机 ， 用于提供SDN网络能力。

### SDN镜像 （SDN Image）

封装SDN软件的镜像 ， 用于创建SDN实例。

文档版本 ： V5.5.0 27

### SDN实例规格 （SDN Instance Offering）

定义SDN实例使用的CPU、内存、SDN镜像以及管理网络配置 ， 用于创建SDN实例。

### 安全组 （Security Group）

为云主机网卡提供安全控制 ， 按照指定的安全规则对进出网卡的TCP/UDP/ICMP等数据包进行有效

过滤。

### 虚拟 IP（VIP）

在桥接网络环境中 ， 使用虚拟IP地址提供弹性IP、端口转发、负载均衡、IPsec隧道等网络服务 ， 数

据包会被发送到虚拟IP ， 再路由至云主机网络。

### 弹性 IP（EIP）

基于网络地址转换 （NAT） 功能 ， 将一个网络的IP地址转换成另一个网络的IP地址 ， 从而可通过其他

网络访问内部私有网络。

### 端口转发 （Port Forwarding）

基于VPC路由器提供的三层转发服务 ， 可将指定公有网络的IP地址端口流量转发到云主机对应协议

的端口。在公网IP地址紧缺的情况下 ， 通过端口转发可提供多个云主机对外服务 ， 节省公网IP地址

资源。

### 负载均衡 （Load Balancer）

将虚拟IP的访问流量分发到后端服务器上 ， 自动检测并隔离不可用的后端服务器 ， 从而提高业务的

服务能力和可用性。

### 监听器 （Listener）

负责监听负载均衡的前端请求 ， 按照指定策略分发给后端服务器 ， 且监听器会对后端服务器进行健

康检查。

### 转发规则 （Forwarding Rule）

将来自不同域名或者不同URL的请求转发到不同的后端服务器组处理。

### 后端服务器组 （Backend Server Group）

一组负责处理负载均衡分发的前端请求的后端服务器。负载均衡实例进行流量分发时 ， 流量分配策

略以后端服务器组为单位生效。

28 文档版本 ： V5.5.0

### 后端服务器 （Backend Server）

负责处理负载均衡分发的前端请求的服务器。支持添加云主机或云平台之外的服务器作为后端服务

器。

### 前端网络 （Frontend Network）

负载均衡的前端网络 ， 负载均衡将来自该网络的客户端请求按照指定策略分发给后端服务器。

### 后端网络 （Backend Network）

负载均衡的后端网络 ， 负责处理负载均衡分发前端请求的后端服务器所在的网络。

### 负载均衡实例 （Load Balancer Instance）

一个定制的云主机 ， 专用于提供负载均衡服务。

### 证书 （Certificate）

当负载均衡监听器使用HTTPS协议 ， 需绑定证书使用。支持上传证书和证书链。

### 防火墙 （Firewall）

在VPC网络场景下 ， 负责管控经由VPC路由器的流量 ， 通过配置规则集和规则管控网络的访问控制

策略。

### 防火墙规则集 （Firewall RuleSet）

防火墙规则的集合 ， 包含了一组规则 ， 需要绑定到VPC路由器网卡的某个方向上才能生效。

### 防火墙规则 （Firewall Rule）

配置至防火墙用于控制VPC网络流量的访问策略 ， 由规则优先级、匹配条件、以及行为三部分组

成。

### 规则模板 （Rule Template）

将一组规则保存为模板 ， 向防火墙或规则集添加规则时可直接选用该模板。

### IP/端口集合 （IP/ Port Set）

将一组IP或端口进行保存 ， 在向防火墙或规则集添加规则时可直接选用已建好的IP/端口集合。

文档版本 ： V5.5.0 29

### IPsec隧道 （IPsec Tunnel）

通过对IP协议的分组加密和认证来保护IP协议的网络传输数据 ， 实现站点到站点 （Site -to-Site ） 的

虚拟私有网络 （VPN） 连接。

### OSPF区域 （OSPF Area）

OSPF协议按照一定标准将一个自治系统划分为不同区域 ， 用于分层管理路由器。

### **NetFlow**

通过Netflow对VPC路由器网卡的进出流量进行分析监控 ， 支持两种数据流输出格式 ： V5、V9。

### 端口镜像 （Port Mirroring）

将云主机网卡的网络流量复制一份到远端 ， 对端口上的业务报文进行分析 ， 方便对网络数据进行监

控管理 ， 在网络故障时可以快速定位故障。

### 路由表 （Route Table）

用户自定义配置路由信息 ， 包括目标网段、下一跳地址、路由优先级。

### 资源编排 （CloudFormation）

一款帮助云计算用户简化云资源管理和自动化部署运维的服务。通过资源栈模板 ， 定义所需的云资

源、资源间的依赖关系、资源配置等 ， 可实现自动化批量部署和配置资源 ， 轻松管理云资源生命周

期 ， 通过API和SDK集成自动化运维能力。

### 资源栈 （Resource Stack）

资源编排通过资源栈模板快速创建和配置一组资源 （ 以及资源间的依赖关系 ）， 这组资源定义为一

个资源栈 ， 通过管理资源栈 ， 维护这组资源。

### 资源栈模板 （Stack Template）

一个UTF8编码格式的文件 ， 基于模板可快速创建资源栈 ， 用户在模板中定义所需的云资源、资源间

的依赖关系、资源配置等 ， 资源编排将解析模板 ， 自动完成所有资源的创建和配置。

### 资源栈示例模板 （Sample Template）

云平台提供了常用的示例模板 ， 用户可基于已有示例模板创建资源栈。

30 文档版本 ： V5.5.0

### 可视化编排 （Designer）

一个可视化的资源编排工具 ， 通过在画布上拖曳连线建立资源间的依赖关系 ， 直观高效编排云资

源。

### 裸金属集群 （Bare Metal Cluster）

为裸金属设备提供单独的集群管理。

### 部署服务器 （Deployment Server）

一台单独的服务器 ， 为裸金属设备提供PXE服务和控制台代理服务。

### 裸金属设备 （Bare Metal Chassis）

用于创建裸金属主机 ， 通过BMC接口以及IPMI配置进行唯一识别。

### 预配置模板 （Preconfigured Template）

通过预配置模板 ， 可快速生成预配置文件 ， 实现无人值守批量安装裸金属主机操作系统。

### 裸金属主机 （Bare Metal Instance）

安装操作系统的裸金属设备。

### 弹性裸金属管理 （Elastice Baremetal Management)

不仅可为应用提供专属物理服务器 ， 保障核心应用的高性能和稳定性 ， 而且结合云平台中资源的弹

性优势 ， 可实现灵活申请 ， 按需使用。

### 部署网络 （Provision Network）

创建弹性裸金属实例时 ， 用于PXE流程及下载镜像的专属网络。

### 弹性裸金属集群 （Elastic BareMetal Cluster）

为裸金属节点提供单独的集群管理。

### 网关节点 （Gateway Node）

云平台和弹性裸金属实例的流量转发节点。

### 裸金属节点 （BareMetal Node）

用于创建弹性裸金属实例 ， 通过BMC接口以及IPMI配置进行唯一识别。

文档版本 ： V5.5.0 31

### 弹性裸金属规格 （Elastic BareMetal Offering）

弹性裸金属实例涉及的CPU、内存、CPU架构、CPU型号等规格定义。

### 弹性裸金属实例 （Elastic BareMetal Instance）

性能媲美物理服务器的云实例 ， 结合云平台中资源的弹性优势 ， 可实现灵活申请 ， 按需使用。

### 基础资源 （vCenter）

云平台支持接管vCenter ， 并对已接管的vCenter虚拟化资源进行统一管理。

### 云主机 （VM Instance）

运行在物理机上的ESXi虚拟机实例 ， 具有独立的IP地址 ， 可以访问公共网络 ， 运行应用服务。

### 网络 （Network）

vCenter云主机使用的网络配置 ， 包括 ： IP地址范围、网关、网络服务等。

### 云盘 （Volume）

为vCenter云主机提供存储 ， 包括两种类型 ： 根云盘、数据云盘。根云盘用于支撑云主机的系统运

行 ， 数据云盘用于云主机扩展的存储使用。

### 镜像 （Image）

vCenter云主机或云盘使用的镜像模板 ， 包括两种类型 ： 系统镜像、云盘镜像。

### 事件消息 （Event Message）

对已接管vCenter的事件报警消息进行集中展示查看 ， 方便用户快速定位问题。

### 网络拓扑 （Network Topology）

通过可视化方式展示云平台网络规划 ， 帮助用户更高效地进行网络规划、管理和性能改进 ， 支持两

种类型 ： 全局拓扑、自定义拓扑。

### 性能分析 （Performance Analysis）

通过列表方式展示云平台核心资源的性能监控指标 ， 提供外部和内部两种监控方式 ， 支持按资源查

看性能分析结果和自定义导出分析报表 ， 方便用户掌控云平台性能状态 ， 提高运维效率。

32 文档版本 ： V5.5.0

### 容量管理 （Capacity Management）

通过可视化方式展示云平台核心资源的容量信息 ， 方便用户掌控云平台容量使用情况 ， 提高运维效

率。

### 管理节点监控 （MN Monitoring）

在多管理节点物理机高可用场景下 ， 可直观查看每个管理节点的健康状态。

### 报警器 （Alarm）

用于监控并响应时序性数据和事件的状态变化 ， 支持资源报警器、事件报警器和扩展报警器。

### 一键报警 （One- Click Alarm）

将种类繁多的资源监控项进行归纳整合 ， 用于快速建立各种资源的监控报警服务。

### 报警模板 （Rule Template）

一组报警器规则的通用模板 ， 关联资源分组后 ， 将对组内资源创建相应的报警器进行监控。

### 资源分组 （Resource Group）

按照业务对资源进行分组 ， 关联报警模板后 ， 报警规则将直接作用于组内全部资源。

### 消息模版 （Message Template）

报警器或事件向SNS系统的主题发送消息时使用的文本模板。

### 消息源 （Message Source）

用于连接扩展消息源 ， 接管扩展报警消息并结合报警器统一推送至各类通知对象。

### 通知对象 （Endpoint）

用户获取订阅主题信息的方式 ， 通知对象类型包括 ： 系统、邮箱、钉钉、企业微信、飞

书、Webhook、短信、Microsoft Teams、SNMP Trap接收端。

### 报警消息 （Alarm Message）

报警器触发时发送的即时提示消息。

### 当前任务 （Current Task）

展示当前正在进行中的操作 ， 提供集中查看和管理。

文档版本 ： V5.5.0 33

### 操作日志 （Operation Log）

云平台运行过程中变化的一种抽样 ， 内容为指定对象的某些操作及其操作结果按时间的有序集合。

### 审计 （Auditing）

实时监控并记录云平台的所有活动 ， 可用于操作追踪、等保合规、安全分析、问题排查、自动运维

等场景。

### 日志收集 （Log Collection）

一键收集云平台以及各类节点在指定时间段内产生的日志 ， 并支持下载查看。

### 一键巡检 （One- Click Inspection）

对云平台关键资源和服务进行全方位一键式健康检查 ， 并根据巡检结果为巡检资源和服务进行健康

评分 ， 同时提供巡检建议和巡检报告 ， 助力高效运维 ， 确保云平台资源和服务处于最佳状态。

### **灾备管理**

灾备管理以业务为中心 ， 融合定时增量备份、定时全量备份等多种灾备技术到云平台中 ， 支持本地

灾备、异地灾备等多种灾备方案 ， 用户可根据自身业务特点 ， 灵活选择合适的灾备方式。

### **灾备服务**

云主机数据在线备份到备份服务器 ， 支持本地 ， 跨地域和混合云多种备份场景 ， 数据更可靠 。

### 备份任务 （Backup Job）

通过备份任务 ， 可将本地云主机/云盘/数据库定时备份到指定的存储服务器。

### 本地备份数据 （Local Backup Data）

本地云主机/云盘/数据库的备份数据 ， 存放在本地备份服务器中。

### 本地备份服务器 （Local Backup Storage）

位于本地数据中心的存储服务器 ， 用于存放本地备份数据或CDP数据。

### 远端备份服务器 （Remote Backup Storage）

位于异地数据中心/公有云上的存储服务器 ， 用于存放远端备份数据。

34 文档版本 ： V5.5.0

### 持续数据保护 （CDP）

为云主机中的重要业务系统提供秒级细粒度的持续备份 ， 既可以将云主机数据恢复到指定时间状

态 ， 又可以在不恢复系统的情况下找回文件。

### CDP任务 （CDP Task）

通过CDP任务 ， 可将云主机数据持续备份到指定的备份服务器 ， 实现持续数据保护。

### CDP数据 （CDP Data）

对云主机进行持续数据保护产生的备份数据 ， 存放在指定的备份服务器中。

### **恢复点**

进行CDP持续备份时产生的数据点 ， 一个恢复点对应用户指定时间间隔内的云主机数据变化。

### **锁定恢复点**

支持将恢复点进行锁定或解锁 ， 锁定恢复点后 ， 恢复点对应的数据将不会被自动清理或删除。

### **恢复任务**

提供向导式的恢复流程 ， 帮助用户通过指定CDP任务和恢复点快速进行数据恢复。同时提供恢复操

作记录 ， 方便后续审计和追溯。

### **密评合规**

通过建立以商用密码为核心的云安全保障体系 ， 满足企业在密评场景的云平台合规要求。

### **密码资源**

提供身份认证和数据加密功能的密码设备。

### **第三方密码服务**

支持添加第三方密码服务平台 ， 用于对外提供验签、加密等密码服务。

### **密码机资源池**

一组密码机的逻辑集合 ， 对外提供统一的验签、加密等密码服务。

### **密码机**

运用密码技术对信息实施加解密处理和认证的专用设备。

文档版本 ： V5.5.0 35

### **平台密评合规**

通过密码机资源池提供的密码能力 ， 满足云平台密评合规要求。

### **证书登录**

可通过UKey设备对用户进行身份标识和鉴别 ， 保证用户身份的真实性。

### **数据保护**

可对云平台重要数据进行保护 ， 保证数据的机密性和完整性。

### 定时任务 （Scheduled Job）

一种预设任务 ， 在指定时间执行指定行为。与定时器配合使用。

### 定时器 （Scheduler）

承载定时任务的容器 ， 尤其适用于长时间运行的操作。

### 标签 （Tag）

一种资源标记 ， 便于快速搜索和资源聚合。

### 迁移服务 （Migration Service）

提供V2V迁移服务 ， 可将其它虚拟化平台的云主机系统及数据完整迁移至当前云平台。

### V2V迁移 （V2V Migration）

将VMware或KVM源云平台的云主机迁移至当前云平台。

### 迁移服务器 （V2V Conversion Host）

V2V迁移需指定目标集群内的一台物理机作为迁移服务器 ， 云主机系统和数据先缓存在迁移服务器

中 ， 再导入目标主存储。

### 用户 （User）

表示自然人 ， 是租户管理中的最基本单位。

### 成员组 （Member Group）

有双重含义 ， 既表示一组自然人的集合 ， 也表示一组项目成员的集合 ， 支持以成员组为单位进行权

限控制。

36 文档版本 ： V5.5.0

### 角色 （Role）

权限的集合 ， 为用户和成员组赋予权限可获得调用相关API进行资源操作的能力。包括平台角色和

项目角色两类。

### 统一认证 （Single Sign On）

云平台提供的统一认证登录服务 ， 支持无缝接入统一认证登录系统 ， 相应统一认证用户将直接登录

云平台 ， 便捷使用云资源。

### 项目 （Project）

项目即是租户 ， 指在特定时间、资源、预算下指定相关人员完成特定目标的任务。租户管理中的租

户主要指项目。支持以项目为导向进行资源规划 ， 为一个具体项目建立独立的资源池。

### 项目成员 （Project Member）

项目的基本组成人员 ， 可在权限范围内使用项目资源完成任务目标 ， 包括项目负责人、项目管理员

和普通项目成员。

### 流程管理 （Process Management）

为了更高效对项目提供基础资源支持 ， 工单审批引入流程管理 ， 包括默认流程和自定义流程两种类

型。

### 我的审批 （My Approvals）

仅admin/项目负责人/自定义审批人员拥有审批权限 ， 可通过或驳回申请。若审批通过 ， 资源会自动

部署并下发至项目生效。

### 账单 （Bills）

按计费价目在指定时间段统计的资源费用 ， 计费精确至秒级。账单类型包括 ： 项目账单、部门账

单、账户账单。

### 计费价目 （Pricing List）

一张包含不同资源计费单价的集合表 ， 资源单价基于资源规格、资源使用时间而设置。

### 控制台代理 （Console Proxy）

可通过代理地址登录云主机控制台。

文档版本 ： V5.5.0 37

### AccessKey管理 （AccessKey Management）

访问云平台API的身份凭证 ， 具有该云平台完全的权限 ， 包括 ： AccessKey ID （ 访问密钥 ID

） [和][AccessKey Secret] （ [秘密访问密钥] ） [。]

### IP黑白名单 （IP Blocklist/ Allowlist）

云平台登录IP的黑白名单 ， 通过对访客身份的识别和过滤 ， 进一步提升云平台登录安全。

### 应用市场 （Application Market）

通过内置的应用部署包或URL ， 快速部署应用服务并一键跳转使用 ， 支持默认应用、拓展应用。

### 子账户管理 （Sub- Account Management）

子账户由admin创建或统一认证系统同步 ， 且受admin管理 ， 子账户对自己创建的虚拟资源拥有管理

权限。

### 主题外观 （Theme）

用户可自定义设置云平台主题外观。

### 邮箱服务器 （Email Server）

云平台报警选择邮箱类型的通知对象 ， 需设置邮箱服务器 ， 用来发送报警邮件。

### 日志服务器 （Log Server）

添加日志服务器至云平台 ， 收集管理节点或平台操作日志 ， 可用于操作追溯和问题定位 ， 提高云平

台运维效率。

### 全局设置 （Global Setting）

提供平台层面的功能特性设置 ， 一经设置 ， 云平台全局范围内生效。

### 场景封装 （Scenario Template）

基于用户实际生产场景需求 ， 提供场景化的一键全局设置 ， 方便快速将云平台设置为所需状态 ， 提

高运维效率。

### 高可用策略 （HA Policy）

云平台内计算、存储、网络资源发生故障或云主机异常停机时 ， 确保相关业务持续稳定运行的机

制。启用后 ， 支持自定义云主机高可用策略 ， 确保业务连续性。

38 文档版本 ： V5.5.0

### **API Inspector**

云平台API调用的监视工具 ， 用于记录用户在云平台上操作时所关联调用的API。

### 版本检查 （Version Detection）

周期性自动检查最新版本并推送最新版本信息 ， 包括版本号 ， 版本亮点等。

### 时间管理 （Time Management）

管理云平台时间和配置时间源 ， 配置后云平台所有物理机将根据指定的时间源进行时间同步。

### SNMP（Simple Network Management Protocol）

SNMP是简单网络管理协议 ， 用于管理网络中的设备。第三方平台可通过该协议监控云平台上的资

源和事件 ， 并接收云平台推送的报警消息。

### 体验升级计划 （Experience Improvement Plan）

体验升级计划是ZStack Cloud为提升产品操作体验和运行性能向用户推出的项目。征得用户同意

后 ， 该计划将统计和分析用户对云平台功能的使用情况 ， 并将统计和分析数据用于指导产品改进优

化 ， 以期后续为用户提供更优质的服务。

### 共享带宽 （Shared Bandwidth）

为多个虚拟IP提供带宽共享和集中限速服务 ， 支持绑定虚拟IP的云主机使用同一条带宽 ， 降低公网

访问成本。

### GPU设备 （GPU Device）

拥有高计算能力的微处理器 ， 可用于处理复杂的图形渲染和并行计算任务 ， 帮助提高图形生产、视

频处理和机器学习等业务的效率。

### 脚本库 （Script Library）

脚本库集中存储和管理自动化脚本文件。对云主机执行脚本 ， 可以完成复杂的运维操作和自动化任

务。

### **XML Hook**

一种脚本程序 ， 用于在云主机XML文件中灵活插入或修改参数 ， 从而实现定制化配置并扩展云主机

功能。

文档版本 ： V5.5.0 39

### 容器管理 （Container Management）

简单易用的容器管理 ， 提供GPU管理调度、多租户、多集群、资源配额、CI/CD、微服务治理等

功能。服务依据传统用户使用习惯 ， 降低容器使用复杂性 ， 帮助用户轻松实现容器集群管理和部

署 ， 快速上手 ， 享受云原生便利。

### **QEMU**

计算机模拟和虚拟化工具 ， 提供完整的虚拟计算机模型用于运行客户操作系统。QEMU可完整模拟

物理机CPU和其他硬件 ， 或结合Hypervisor使客户操作系统直接执行在物理机CPU上 ， 从而实现接

近原生的性能表现。

### **Libvirt**

虚拟化环境管理工具 ， 提供稳定的API、命令行工具 (virsh) 和守护进程 (Libvirt)， 用于管理云平

台上的虚拟机 (如创建、启动、关闭、迁移云主机等 )， 并实现网络和存储配置。

### **Kernel**

操作系统内核 ， 负责管理CPU、内存、输入/输出设备等系统资源 ， 协调计算机硬件和上层应用之间

的交互 ， 提供硬件抽象、资源分配、进程管理、进程间通信、系统资源安全控制等功能。

### 高级监控服务器 （Advanced Monitoring Server）

一个定制的云主机 ， 专用于接收和处理负载均衡等资源的高级监控数据。

### 高级监控服务器镜像 （Advanced Monitoring Server Image）

封装了高级监控服务的镜像 ， 专用于创建高级监控服务器 ， 不可用于创建业务云主机。

### 高级监控服务器规格 （Advanced Monitoring Server Offering）

定义高级监控服务器使用的CPU、内存、镜像、管理网络、公有网络配置 ， 专用于创建高级监控服

务器。

### 插件管理 （Plugin Management）

将扩展资源或工具封装为标准化插件 ， 便于在云平台上快速安装和集成 ， 实现功能扩展。

### 可用区管理 （Region Management）

可用区是一套完整的云环境 ， 具有独立的管理节点、网络、硬件和云资源。多个可用区间可实现用

户同步和免密登录。

40 文档版本 ： V5.5.0
