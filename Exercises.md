# DO322 Exercises

## EPub readerのインストール
```
flatpak install com.github.johnfactotum.Foliate
```
### Foliateの設定
- Font&Layout Settings
- Layout > Page > Maximum Number of Columns を 1 に設定
- Scrolled Modeにチェック

## 教室環境のリージョン
```
nexus-registry-int.apps.tools-na150.prod.ole.redhat.com
```
## pxelinux.cfg

### MASTER
```
default menu.c32
prompt 0
timeout 0
menu title **** OpenShift 4 MASTER PXE Boot Menu ****

label Install RHCOS 4.6.1 Master Node
 kernel http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-kernel-x86_64
 append ip=dhcp rd.neednet=1 coreos.inst.install_dev=vda console=tty0 console=ttyS0 coreos.inst=yes coreos.live.rootfs_url=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-rootfs.x86_64.img coreos.inst.ignition_url=http://192.168.50.254:8080/openshift4/4.6.4/ignitions/master.ign initrd=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-initramfs.x86_64.img
```
### BOOTSTRAP
```
default menu.c32
prompt 0
timeout 0
menu title **** OpenShift 4 BOOTSTRAP PXE Boot Menu ****

label Install RHCOS 4.6.1 Bootstrap Node
 kernel http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-kernel-x86_64
 append ip=dhcp rd.neednet=1 coreos.inst.install_dev=vda console=tty0 console=ttyS0 coreos.inst=yes coreos.live.rootfs_url=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-rootfs.x86_64.img coreos.inst.ignition_url=http://192.168.50.254:8080/openshift4/4.6.4/ignitions/bootstrap.ign initrd=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-initramfs.x86_64.img
```

### WORKER
```
default menu.c32
prompt 0
timeout 0
menu title **** OpenShift 4 WORKER PXE Boot Menu ****

label Install RHCOS 4.6.1 Worker Node
 kernel http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-kernel-x86_64
 append ip=dhcp rd.neednet=1 coreos.inst.install_dev=vda console=tty0 console=ttyS0 coreos.inst=yes coreos.live.rootfs_url=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-rootfs.x86_64.img coreos.inst.ignition_url=http://192.168.50.254:8080/openshift4/4.6.4/ignitions/worker.ign initrd=http://192.168.50.254:8080/openshift4/images/rhcos-4.6.1-x86_64-live-initramfs.x86_64.img
```
## pxelinux.cfgのソリューション
```
cd /tmp
wget -r http://classroom.example.com/materials/solutions/pxelinux.cfg/
diff -r /var/lib/tftpboot/pxelinux.cfg/ classroom.example.com/materials/solutions/pxelinux.cfg/
```
