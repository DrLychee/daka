# 打卡 · 个人工具 App

一个轻量、离线、可无限扩展模块的个人打卡工具（Android APK + PWA）。

## 功能模块

| 图标 | 模块 | 说明 |
|---|---|---|
| 📚 | 学习打卡 | 时长/科目/模板 → 生成群格式文字 → 复制 → 跳微信发送 |
| 🎮 | 游戏打卡 | 小黑盒一键签到（原生通道，绕过跨域） |
| 🏃 | 运动打卡 | 项目/时长/距离/备注，连续天数与本周次数统计 |
| 📅 | 日历 | 月视图自动汇总学习、运动、待办完成情况 |
| ✅ | 待办 | 增删任务、日期记录、日历同步 |
| 🍅 | 专注 | 番茄钟，今日/累计番茄统计 |
| ⚙️ | 设置 | 主题切换、模板管理、数据备份与恢复、更新日志 |

## 特点

- **完全离线运行**：不依赖任何服务器，数据存在手机本地
- **插件式架构**：新增功能只需追加一个模块对象（见 `app/index.html` 顶部模板）
- **原生 HTTP**：小黑盒签到走 Capacitor 原生通道，彻底解决 CORS
- **数据可备份**：设置页支持导出/导入 JSON 备份

## 目录结构

```
app/                     网页源码（PWA 版本，可直接部署）
  index.html             全部代码（模块 + 外壳）
  manifest.json          PWA 配置
  icon-*.png             图标
assets/                  安卓图标源（1024×1024）
capacitor.config.json    Capacitor 配置
package.json             依赖与脚本
```

## 本地打包 APK

```bash
npm install
npx cap init "打卡" com.lcz.daka --web-dir app   # 首次
npx cap add android                              # 首次
npx cap sync android
cd android && ./gradlew assembleRelease
```

签名：在 `android/app/build.gradle` 的 `signingConfigs.release` 中配置自己的 jks（仓库已忽略 `*.jks`，不要提交密钥）。

## 部署 PWA

把 `app/` 整个目录放到任意静态服务器（如 nginx）即可，手机浏览器打开后「添加到主屏幕」就是全屏 App。

## 更新日志

见 `app/index.html` 内的 `CHANGELOG` 常量，或 App 内「设置 → 更新日志」。

- **v1.2.0** 新增运动打卡、日历模块；待办支持日期与日历同步
- **v1.1.0** 新增设置（主题/模板/备份）、更新日志
- **v1.0.0** 首个版本，四模块 + 原生打包

## 声明

仅供个人学习使用，请勿用于违规用途。第三方平台 Cookie 属于个人登录凭证，注意保管。
