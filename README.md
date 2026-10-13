# 行前漫游 · Render 发布仓库

公开网站：https://realtrip-walk.onrender.com/

`realtrip-render.zip` 是完整发布包，包含前端源码、构建产物、许可说明，以及用户授权公开的公司实拍重建模型。原始视频、音频和训练文件不包含在发布包内。

## 当前版本

2026-10-13，同步现有公开网站 v11（源提交 `4c02aab7ad7fca721e517e46b96f4539c4688a68`）。

- 公司院子、大厅、楼梯、二楼使用同一个模型，支持连续步行和起点切换。
- 保留八大山人纪念馆庭院、池塘、东阳卢宅和梅岭妙济桥。
- 电脑 WASD 移动、空格跳跃；手机左侧摇杆移动、右侧滑动转头、点击跳跃。
- 公司模型由用户视频的 212 帧重建；玻璃、栏杆和未拍清方向仍有模糊，行走地面和楼梯高度为估计值。

## 入口

- 公司：`/?scene=office`
- 大厅：`/?scene=office-lobby`
- 楼梯：`/?scene=office-stairs`
- 二楼：`/?scene=office-upstairs`
- 卢宅：`/luzhai`
- 妙济桥：`/?scene=miaoji`

## 构建与发布

现有 Render 静态站点使用 `main` 分支，手动触发部署。

```sh
unzip -o realtrip-render.zip -d site
cd site
npm ci
npm run build
npm test
```

发布目录为 `site/public`。包内同时包含 `/luzhai.html` 和 `/luzhai/index.html`，支持直接访问卢宅入口。
