# Deploy to Cloudflare Pages

这个项目预期将源码、文章、图片和评论归档 JSON 全部保存在 GitHub 仓库中，Cloudflare Pages 从 GitHub 仓库拉取源码并构建静态站点。

## 基础设置

1. 在 GitHub 创建仓库并推送当前项目源码。
2. 在 Cloudflare Pages 中连接这个 GitHub 仓库。
3. Framework preset 选择 `Hugo`。
4. Build command 使用：

```powershell
hugo --gc --minify
```

5. Build output directory 使用：

```text
public
```

6. Production branch 使用：

```text
main
```

## 环境变量

建议在 Cloudflare Pages 中设置 `HUGO_VERSION`，并固定到本地 Hugo major/minor 兼容版本：

```text
HUGO_VERSION=0.157.0
```

## 注意事项

- 不要提交 `public/` 到 Git。
- PaperMod 通过 Git submodule 引入，Cloudflare Pages 构建时需要拉取子模块。
- 未来接入评论归档时，GitHub Actions 会把已审核评论导出到 `data/comments/posts/*.json`，Hugo 构建时再渲染为静态 HTML。

