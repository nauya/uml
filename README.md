LKL版本
不仅是ovz可用，其他虚拟化方式也是可以用的(有一台vmware原本是用升级内核的方法来装bbr，但是后来安装了多个版本的内核都出现了kernel-panic，使用这个解决) 补充说明：升级内核的方法应该谨慎考虑，一旦出现kernel-panic就无法开机，只能重建了

本人使用的是这个脚本
注意，在使用前要在VPS的控制面板把TUN/TAP功能打开做NAT表(部分OVZ没有这项功能)

wget --no-check-certificate https://github.com/91yun/uml/raw/master/lkl/install.sh && bash install.sh
检查：
运行top，如果有haproxy就成功了

ping 10.0.0.2
能通说明成功

如果修改转发端口:

修改 /root/lkl/run.sh ，查找 9000-9999 ，改成你想要的端口段
修改 /root/lkl/haproxy.cfg 查找 9000-9999 ，改成你想要的端口段
重启 vps
