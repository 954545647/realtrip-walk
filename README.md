# RealTrip · 实景自由漫游

线上站点：https://realtrip-walk.onrender.com/

当前仅保留三个场景：
- 荣誉连廊：`/honor-corridor/?scene=honor-corridor`
- 2号楼（默认）：`/?scene=building2`；旧 `?scene=insta360` 兼容。
- 露台：`/?scene=terrace`

2026-10-17 已清理六个旧场景的入口、配置、专用资源与构建依赖。桌面移动、手机摇杆、转头、跳跃、横屏，以及三个场景的现有模型和碰撞校准继续保留。

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

清理前版本：`1764a6019f6ed86f96dea48571843440feb82aaa`。需要恢复时，通过 Git 历史恢复对应发布文件并重新部署，或使用 Render 历史部署回退。

原始视频和训练依赖不进入发布包。
