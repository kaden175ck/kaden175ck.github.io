# 基于 **Jekyll** 的博客

## 📦 环境要求

- [Ruby](https://rubyinstaller.org/downloads/)

验证安装是否成功：

```bash
ruby -v
gem -v
```

## 🚀 安装与运行

**安装依赖**

```bash
bundle install
```

**启动本地服务**

```bash
bundle exec jekyll serve --livereload
```

**构建生产环境**

```bash
bundle exec jekyll build
```

构建后的静态文件会生成在 `_site/` 目录下。
