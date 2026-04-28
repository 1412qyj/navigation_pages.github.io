# AI 导航

这是基于 [WebStack-Hugo](https://gitee.com/shenweiyan/WebStack-Hugo) 初始化的静态导航页，当前已内置以下大模型对话入口：

- 豆包：https://www.doubao.com/chat/
- DeepSeek：https://chat.deepseek.com/
- ChatGPT：https://chatgpt.com/

## 本地预览

安装 Hugo 后，在仓库根目录运行：

```bash
hugo server -D
```

默认访问：

```text
http://localhost:1313/
```

## 构建静态文件

```bash
hugo
```

构建产物会输出到 `public/` 目录。

## 添加导航项目

导航数据在 `data/webstack.yml`。

如果要在顶部一级分类里添加一个网站，在对应分类的 `links` 下追加：

```yaml
- title: 网站名称
  logo: https://www.google.com/s2/favicons?domain=example.com&sz=128
  url: https://example.com/
  description: 这里写一句简短说明。
```

如果要添加带二级分组的分类，使用 `list -> term -> links` 结构：

```yaml
- taxonomy: 新分类
  icon: fas fa-layer-group
  list:
    - term: 新分组
      links:
        - title: 网站名称
          logo: https://www.google.com/s2/favicons?domain=example.com&sz=128
          url: https://example.com/
          description: 这里写一句简短说明。
```

字段说明：

- `taxonomy`：左侧菜单和页面中的一级分类名称。
- `icon`：Font Awesome 图标类名。
- `term`：二级分组名称，只在使用 `list` 时需要。
- `title`：导航卡片标题。
- `logo`：图标地址，可以是完整 URL，也可以是 `static/assets/images/logos/` 下的本地文件名。
- `url`：点击后打开的网址。
- `description`：卡片上的简短说明。

## 使用本地图标

把图片放到：

```text
static/assets/images/logos/
```

然后在 `data/webstack.yml` 中写文件名：

```yaml
logo: my-logo.png
```

## 部署到 Gitee Pages

常见做法是先执行：

```bash
hugo
```

然后将 `public/` 目录中的静态文件发布到 Gitee Pages 对应分支或页面目录。具体方式取决于你的 Gitee Pages 配置。
