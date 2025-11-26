# Caddy-Naive 项目说明

## 项目目的

本项目用于自动编译带有 NaiveProxy forwardproxy 插件的 Caddy 服务器。

## 文件说明

- `README.md` - 项目说明文档
- `.github/workflows/build.yml` - GitHub Actions 自动编译配置
- `LICENSE` - 许可证

## 使用方式

### 1. 创建 GitHub 仓库

在 https://github.com/new 创建名为 `caddy-naive` 的公开仓库

### 2. 推送代码

```powershell
cd "G:\GitHub\caddy-naive"
git init
git add .
git commit -m "Initial commit: Caddy with NaiveProxy build system"
git branch -M main
git remote add origin https://github.com/Michaol/caddy-naive.git
git push -u origin main
```

### 3. 触发编译

1. 访问 https://github.com/Michaol/caddy-naive/actions
2. 选择 "Build Caddy with NaiveProxy"
3. 点击 "Run workflow"
4. 等待编译完成

### 4. 下载编译好的 Caddy

访问 https://github.com/Michaol/caddy-naive/releases/latest

## 注意事项

- 编译的 Caddy 是**公开的**，任何人都可以下载
- Caddyfile 配置文件存储在**私有 Gist** 中，需要 Token 才能下载
- deploy.sh 保留在 VPS Caddy 目录中，不上传到此仓库
