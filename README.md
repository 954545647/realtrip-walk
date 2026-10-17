# RealTrip · 实景自由漫游

线上站点：https://realtrip-walk.onrender.com/

当前仅保留三个场景：
- 荣誉连廊：`/honor-corridor/?scene=honor-corridor`
- 2号楼（默认）：`/?scene=building2`；旧 `?scene=insta360` 兼容。
- 露台：`/?scene=terrace`

2026-10-17 已清理六个旧场景的入口、配置、专用资源与构建依赖。桌面移动、手机摇杆、转头、跳跃、横屏，以及三个场景的现有模型和碰撞校准继续保留。

## 界面更新

场景切换使用统一的深灰半透明面板，显示当前空间、图标与简短说明；支持键盘、点击外部关闭和 Escape。跳跃、复位、全屏收进统一操作栏，摇杆缩小，适配手机安全区、横屏及 320px 窄屏。打开菜单时停止移动，避免方向键操作菜单时误走动。

构建与导航测试通过，已验证三个场景互相切换、摇杆、跳跃、复位和全屏。浏览器视口检查不替代真实手机验收。原模型、地面和碰撞参数不变。

## 部署

沿用现有 Render 静态站点 realtrip-walk，main 分支，自动部署关闭。

构建命令：`unzip -o realtrip-render.zip -d site && cd site && npm ci && npm run build`

发布目录：`site/public`。构建先清理 public 中不再发布的旧路径，再校验并装配以下模型，最后重新生成查看器。

- `building2-doorway-20261017.sog`
- `terrace-20261017.sog`
- `honor-corridor-20261017-return-feedback.sog.part001` 至 `.part003`

模型的大小和 SHA-256 在包内准备脚本中校验。其他保留的旧模型仅用于版本回退，不复制到线上 public。

## 验证与回退

`npm test` 验证共用控制、双向路线、2号楼和露台碰撞、横屏交互。发布前已验证默认入口、三个场景切换、键盘移动和旧 public 路径清理。

本次界面更新前版本：`e5cb07ff2db3d14a0c16ca30d85d8df42657d84c`。需要恢复时，通过 Git 历史恢复对应发布文件并重新部署，或使用 Render 历史部署回退。

原始视频和训练依赖不进入发布包。
