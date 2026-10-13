# 行前漫游 · Render 发布仓库

公开网站：https://realtrip-walk.onrender.com/

`realtrip-render.zip` 是完整发布包，包含前端源码、构建产物、许可说明，以及用户授权公开的公司实拍重建模型。原始视频、音频和训练文件不包含在发布包内。

## 当前版本

2026-10-13，v13：优化公司门口 → 大厅 → 楼梯的清晰度与连续行走。

- 在同一公司模型上进行 12,000 步重点二次训练；门口至楼梯的训练采样权重增加，保留院子及二楼。
- 校准入口高度，平滑行走速度和上下楼过渡；初始俯仰贴近拍摄方向。
- 加入可关闭的轻微步行起伏，尊重系统减少动态效果偏好。
- 12 个固定参考视角均比旧模型更贴近原片；仍需注意未拍摄方向的模糊。
- 保留八大山人纪念馆庭院、池塘、东阳卢宅和梅岭妙济桥。
- 电脑 WASD 移动、空格跳跃；手机左侧摇杆移动、右侧滑动转头、点击跳跃。
- 公司模型由用户视频的 212 帧重建；玻璃、栏杆和未拍清方向仍有模糊，行走地面和楼梯高度为估计值。

## 入口

- 门口（推荐本轮体验）：`/?scene=office-entrance`
- 公司：`/?scene=office`
- 大厅：`/?scene=office-lobby`
- 楼梯：`/?scene=office-stairs`
- 二楼：`/?scene=office-upstairs`
- 卢宅：`/luzhai`
- 所有目的地及区域切换均使用 `?scene=...`。首页和旧的 `/luzhai` 入口加载后也会补全对应参数，复制地址即可分享当前所选场景。
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
