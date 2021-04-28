# 说明
整个项目采用[Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)，按照说明使用模板即可，透明，只是修改了sh脚本增加了一些插件源，修改了默认IP，账号密码仍为root/password。

## 改动部分
### 1 build-openwrt.yml
将 'SSH connection to Actions' 默认改成了 true， 用于触发config自定义， 也可以改回false， 将根目录下某个合适2021xxxconfig改名为`.config`后启动编译

### 2 diy-part1.sh
添加源
```

sed -i '$a src-git kenzok8 https://github.com/kenzok8/openwrt-packages' feeds.conf.default
sed -i '$a src-git small https://github.com/kenzok8/small' feeds.conf.default
```


### 3 diy-part2.sh
修改默认IP

## 编译更新

- 20210426 第一次编译，已Actions-OpenWrt的Lean为整合Lienol和各插件，形成config记录 https://molezz.lanzous.com/b0263301g
密码:g8w0
- 20210427 第二次编译，去除默认的迅雷快鸟，uu加速等用不上的组件，加了一部分主题和iperf3测速，不占多少资源。启动内存较低，详见config中luci部分。或自行注释



## 参考引用

- [helloworld](https://github.com/fw876/helloworld)
- [Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)
- [PVE下LXC模式部署OpenWRT](http://molezz.net/proxmox-pve-kvm-ct-lxc-openwrt/)
- [添加源参考](https://mianao.info/2020/05/05/%E7%BC%96%E8%AF%91%E6%9B%B4%E6%96%B0OpenWrt-PassWall%E5%92%8CSSR-plus%E6%8F%92%E4%BB%B6)

## Tips

- 软件包升级提示wget 8， 需要注释掉这几行，因为不存在更新ipk地址，或者采用其他编译好更新源.
- 如想修改默认IP，可以在编译前修改diy-part2.sh中192.168.1.83部分为自己的

