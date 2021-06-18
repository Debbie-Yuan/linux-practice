# Services in Linux



** **



### 1. Command line service 
```shell
  difference between systemctl and /etc/init.d/
```

- > Service is an "high-level" command used for starting and stopping services in different unixes and linuxes. Depending on the "lower-level" service manager, service redirects on different binaries.

- > For example, on CentOS 7 it redirects to systemctl, while on CentOS 6 it directly calls the relative /etc/init.d script. On the other hand, in older Ubuntu releases it redirects to upstart

- > Service is adequate for basic service management, while directly calling systemctl give greater control options.

- > Mind that although more powerful, systemctl is not a new version of service. It is not designed to replace service. Rather, service is designed as a high-level wrapper to "abstract" out various service managers like init.d, initctl, and (of course) systemctl. 


### 2. Unit File



### 3. Masked Service

- > A masked service is one whose unit file is a symlink to /dev/null
  > this makes it "impossible" to load the service, even if it is required by another, enabled service.
  > 
- > When you mask a service, a symlink is created from /etc/systemd/system to /dev/null, leaving the original unit file
  > elsewhere untouched. When you unmask a service the symlink is deleted.
  > 
- It's not always honoured to unmask a service only if the service is non-critical.
  

- ```$ sudo systemctl mask bluetooth.service```
- ``` Failed to execute operation: Invalid argument.```


***
### 5. 命令
```shell
  systemctl list-nuits --all # 查看所有注册在systemd文件夹下的服务与设备
  journalctl -xe # 查看系统日志
  apt list --installed # 查看已安装的包
  apt --reinstall install [pkg name] # 重新安装已安装的包
  apt --fix-broken install # 修复破裂的包
```