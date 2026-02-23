![](/blogs/2-23/a3fd43eb39fcd43e.jpg)
Ubuntu+macos式美化+linux-surface，运行优雅流畅，触控可用



安装好系统后建议看看这个视频选择性配置一些⬇️（https://www.bilibili.com/video/BV1A5SFYMEtD/?spm_id_from=333.337.search-card.all.click&vd_source=22ecf2049a0ba85a7dc1aa1cbfcd2df1）
![](/blogs/2-23/6d6e324ec13e3ab7.png)

然后再参照这个视频美化⬇️
![](/blogs/2-23/fe4cceb09b27101c.png)

./sudo apt update && sudo apt upgrade -y    ##更新和升级一下软件包

./sudo apt install gcc make cmake curl perl wget git wmctrl sassc ##安装工具
./sudo apt install gnome-tweaks gnome-shell-extension-manager 

然后在ulauncher.io下载ulaunch的Debian包

./cd Downloads/
./sudo chmod atx ulauncher_5.15.8 all.deb #以实际文件名为准
./sudo apt install ./ulauncher_5.15.8 all.deb

我安装了这些插件
![](/blogs/2-23/957d5475e849d166.jpg)

./gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize-or-previews' ##启用终端的点击最小化功能

git clone https://github.com/kayozxo/GNOME-macOS-Tahoe
## 主题安装/卸载
./install.sh -l    # Light theme only
./install.sh -d    # Dark theme only
./install.sh -u    # Uninstall

## 壁纸安装
./install.sh -w    # Tahoe 26 dynamic wallpapers

## 生成强调色
./install.sh --colors        # Generate all 16 variants
./install.sh --color blue    # Generate specific color

## 带 libadwaita 支持的安装
./install.sh -d -la                 # Dark + libadwaita
./install.sh -d --color blue -la    # Dark blue + libadwaita + GNOME Shell

最后配置linux-surface

添加 Linux-Surface 仓库#
# 添加仓库
./sudo add-apt-repository ppa:linux-surface/ppa
./sudo apt update

# 安装内核（包含 Surface 驱动补丁）
./sudo apt install linux-image-surface linux-headers-surface
 
# 安装工具
./sudo apt install linux-surface-secureboot-mok surface-utilities surface-firmware

#验证
./uname -r  # 输出应为x.x.x-surface

# 更新
sudo surface-firmware-update

# 检查驱动是否加载
lsmod | grep surface  

安装surface-control，可调节充电阈值、风扇转速等硬件参数：
# 安装 surface-control（已在 3.3 步骤中安装）
./sudo apt install surface-control
# 设置充电阈值（20%~80%，减少电池损耗）
./sudo surface-control --set-charge-threshold 20 80
# 查看电池状态
./surface-control --battery-status

安装tlp，优化后台进程和硬件功耗
./sudo apt install tlp tlp-rdw
./sudo systemctl enable --now tlp

安装 gnome-shell-extension-x11gestures 扩展，支持三指切换工作区、四指显示桌面：
./sudo apt install gnome-shell-extension-x11gestures

好，结束~