# lxdapi-web-server
~~~
bash <(curl -Ls https://raw.githubusercontent.com/xkatld/lxdapi-web-server/refs/heads/v2.0.0-main/install.sh)
~~~

~~~
root@runnervmwmpaq:~# bash <(curl -Ls https://raw.githubusercontent.com/xkatld/lxdapi-web-server/refs/heads/v2.0.0-main/install.sh)

========================================
      步骤 1/5: 初始化环境
========================================

[OK] 语言环境设置为 C.utf8
[INFO] 更新软件包列表...
[OK] wget 已安装
[OK] curl 已安装
[OK] sudo 已安装
[OK] unzip 已安装
[OK] lxcfs 已安装
[OK] iptables-persistent 已安装
[OK] nginx 已安装
[OK] lxcfs 服务已启动并设置为自动启动
[OK] nginx 服务已启动并设置为自动启动
[OK] 环境初始化完成

========================================
      步骤 2/5: 安装 LXD
========================================

[INFO] 开始安装 snap...
[OK] snapd 已安装
[INFO] 开始安装 LXD...
lxd 6.5-ccdfb39 from Canonical✓ installed
[OK] LXD 安装完成

========================================
      步骤 3/5: 配置存储资源
========================================

是否需要指定存储池的自定义路径？(y/n) [n]：
宿主机需要开设多大的存储池？单位 GB，需要 10G 则输入 10：10
[OK] 使用 lvm 类型，存储池大小为 10 GB
[INFO] 初始化存储：

[OK] 使用 lvm 初始化成功
[OK] 存储配置完成

========================================
      步骤 4/5: 导入容器镜像
========================================

[INFO] 检测系统架构...
[OK] 检测到架构: aarch64

============================================================================================================
 1) alma8          2) alma9         3) alma10        4) alpine319     5) alpine320                       
 6) alpine321      7) alpine322     8) alpineEdge    9) amazon2023   10) centos9                         
11) centos10      12) debian11     13) debian12     14) debian13     15) fedora41                        
16) fedora42      17) oracle8      18) oracle9      19) rocky8       20) rocky9                          
21) rocky10       22) suse155      23) suse156      24) suseTumbleweed                                   
25) ubuntu2204    26) ubuntu2404   27) ubuntu2410                                                        
============================================================================================================

请输入镜像编号，多个用逗号分隔如 1,2,3 或输入 all 全部导入 [默认: 2,5,13,26]：

[OK] 已选择 4 个镜像

[1/4]
[INFO] 下载: alma9-arm64.tar.gz
/tmp/tmp.c94O4E3Pbk                                               100%[=============================================================================================================================================================>] 152.84M   197MB/s    in 0.8s    
[INFO] 导入到 LXD...
Image imported with fingerprint: edc1c07dfbef9ba0c21151c9d006dd6de569faed11f53bb18aaba783503c6f36
[OK] 成功导入: alma9

[2/4]
[INFO] 下载: alpine320-arm64.tar.gz
/tmp/tmp.CvhhT3vDKB                                               100%[=============================================================================================================================================================>]   9.73M  --.-KB/s    in 0.06s   
[INFO] 导入到 LXD...
Image imported with fingerprint: cf0fd2f659d8ac848f4b086fcb5474be52af4c96b16bc0dfa830374049df6512
[OK] 成功导入: alpine320

[3/4]
[INFO] 下载: debian12-arm64.tar.gz
/tmp/tmp.IfTtrpwIWH                                               100%[=============================================================================================================================================================>] 124.46M   201MB/s    in 0.6s    
[INFO] 导入到 LXD...
Image imported with fingerprint: d681189b5c4c18351930268270e44acf81e3d5b8cb604872a7cdfacd948658b3
[OK] 成功导入: debian12

[4/4]
[INFO] 下载: ubuntu2404-arm64.tar.gz
/tmp/tmp.4zntL02T19                                               100%[=============================================================================================================================================================>] 136.36M   282MB/s    in 0.5s    
[INFO] 导入到 LXD...
Image imported with fingerprint: 254c0e31bf05ca0ef273e95beebe4eb01376e7ffec201a4402d274e40041a9a5
[OK] 成功导入: ubuntu2404

[OK] 镜像导入完成

========================================
      步骤 5/5: 部署 lxdapi
========================================

[INFO] 检测系统架构...
[OK] 检测到架构: aarch64
[INFO] 获取最新版本...
[OK] 最新版本: v2.0.0-main
[INFO] 下载 lxdapi...
[INFO] 下载地址: https://github.com/xkatld/lxdapi-web-server/releases/download/v2.0.0-main/lxdapi-linux-arm64.tar.gz
/tmp/tmp.bpEhae6ByR                                               100%[=============================================================================================================================================================>]  30.82M  --.-KB/s    in 0.1s    
[OK] 下载完成
[INFO] 解压到 /opt/lxdapi...
[INFO] 配置 lxdapi...
请输入服务端口 [8848]：
请输入API密钥 [随机生成]：
[OK] API密钥已生成: a3ffb166b896f34abe67d50a5f91d5e2
请输入流量采集间隔秒数 [20]：
请输入流量批量更新数量 [5]：
请选择数据库类型 sqlite/mysql/postgres [sqlite]：
请选择任务队列后端 memory/redis [memory]：
请输入管理员用户名 [admin]：
请输入管理员密码 [随机生成]：
[OK] 管理员密码已生成: d08cc16b
请输入Session密钥 [随机生成]：
[OK] Session密钥已生成: 945e2568fba2208054b2d3ec57ae8708
[INFO] 写入配置文件...
[OK] 配置文件已更新
[INFO] 配置 lxdapi 系统服务...
[OK] 服务文件已创建: /etc/systemd/system/lxdapi.service
[INFO] 重载 systemd 配置...
[INFO] 启用开机自启...
Created symlink /etc/systemd/system/multi-user.target.wants/lxdapi.service → /etc/systemd/system/lxdapi.service.
[INFO] 启动 lxdapi 服务...
[OK] lxdapi 服务已启动

[INFO] ===== 服务状态 =====
● lxdapi.service - LXD API Server
     Loaded: loaded (/etc/systemd/system/lxdapi.service; enabled; preset: enabled)
     Active: active (running) since Sat 2025-11-15 19:52:19 UTC; 2s ago
   Main PID: 8640 (lxdapi-arm64)
      Tasks: 6 (limit: 19097)
     Memory: 26.6M (peak: 27.2M)
        CPU: 127ms
     CGroup: /system.slice/lxdapi.service
             └─8640 /opt/lxdapi/lxdapi-arm64

[OK] lxdapi 部署完成

========================================
        lxdapi 安装完成
========================================

[INFO] LXD 版本: 6.5
[INFO] LXC 版本: 6.5

[INFO] ===== 1. 网络配置 =====
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+
|   NAME    |   TYPE   | MANAGED |      IPV4      |           IPV6            | DESCRIPTION | USED BY |  STATE  |
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| docker0   | bridge   | NO      |                |                           |             | 0       |         |
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| enP2807s1 | physical | NO      |                |                           |             | 0       |         |
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| eth0      | physical | NO      |                |                           |             | 0       |         |
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| lxdbr0    | bridge   | YES     | 10.72.236.1/24 | fd42:3b78:e2b0:d197::1/64 |             | 1       | CREATED |
+-----------+----------+---------+----------------+---------------------------+-------------+---------+---------+

[INFO] ===== 2. 存储配置 =====
+---------+--------+--------------------------------------------+-------------+---------+---------+
|  NAME   | DRIVER |                   SOURCE                   | DESCRIPTION | USED BY |  STATE  |
+---------+--------+--------------------------------------------+-------------+---------+---------+
| default | lvm    | /var/snap/lxd/common/lxd/disks/default.img |             | 1       | CREATED |
+---------+--------+--------------------------------------------+-------------+---------+---------+

[INFO] ===== 3. 镜像配置 =====
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+
|   ALIAS    | FINGERPRINT  | PUBLIC |      DESCRIPTION      | ARCHITECTURE |   TYPE    |   SIZE    |         UPLOAD DATE          |
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+
| alma9      | edc1c07dfbef | no     | Almalinux 9 ARM64     | aarch64      | CONTAINER | 152.84MiB | Nov 15, 2025 at 7:52pm (UTC) |
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+
| alpine320  | cf0fd2f659d8 | no     | Alpine 320 ARM64      | aarch64      | CONTAINER | 9.73MiB   | Nov 15, 2025 at 7:52pm (UTC) |
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+
| debian12   | d681189b5c4c | no     | Debian bookworm ARM64 | aarch64      | CONTAINER | 124.46MiB | Nov 15, 2025 at 7:52pm (UTC) |
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+
| ubuntu2404 | 254c0e31bf05 | no     | Ubuntu noble ARM64    | aarch64      | CONTAINER | 136.36MiB | Nov 15, 2025 at 7:52pm (UTC) |
+------------+--------------+--------+-----------------------+--------------+-----------+-----------+------------------------------+

[INFO] ===== 4. 后端配置 =====
[INFO] 服务端口: 8848
[INFO] API密钥: a3ffb166b896f34abe67d50a5f91d5e2
[INFO] 流量间隔: 20 秒
[INFO] 批量大小: 5
[INFO] 数据库: sqlite
[INFO] 任务队列: memory
[INFO] 管理员: admin
[INFO] 管理员密码: d08cc16b
[INFO] Session密钥: 945e2568fba2208054b2d3ec57ae8708

[INFO] ===== 5. lxdapi 服务状态 =====
[INFO] 等待服务启动...
● lxdapi.service - LXD API Server
     Loaded: loaded (/etc/systemd/system/lxdapi.service; enabled; preset: enabled)
     Active: active (running) since Sat 2025-11-15 19:52:19 UTC; 7s ago
   Main PID: 8640 (lxdapi-arm64)
      Tasks: 6 (limit: 19097)
     Memory: 26.6M (peak: 27.2M)
        CPU: 127ms
     CGroup: /system.slice/lxdapi.service
             └─8640 /opt/lxdapi/lxdapi-arm64

Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] Nginx 插件已启动
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 插件启动: nginx
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 所有插件启动成功
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 异步任务队列初始化成功，Worker数: 4
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 任务队列初始化成功
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 流量监控器已启动
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 任务自动清理已启动，保留最近 7 天
Nov 15 19:52:19 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:19 [OK] 自动清理任务已启动
Nov 15 19:52:20 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:20 [OK] 模板加载完成
Nov 15 19:52:20 runnervmwmpaq lxdapi-arm64[8640]: 2025-11-15 19:52:20 [OK] 自签名证书生成成功 (有效期10年)
~~~
