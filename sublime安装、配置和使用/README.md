# package control被墙后，安装package control插件

*更新日期2019/5/19

## 手动安装package control插件:

1. 点击 Preferences > Browse Packages 菜单
2. 进入打开的目录的上层目录，然后再进入 Installed Packages/ 目录
3. 下载 Package Control.sublime-package 并复制到Installed Packages/目录
4. 重启 Sublime Text。

## 同样channel_v3.json也被墙了需要手动配置到项目中

1. 点击 Preferences > Package settings > Package control > Setting-User菜单
2. 添加键值对，将channel_v3.json配置到本地中。 "channels":["D:\\channel_v3.json"]。