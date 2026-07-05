# 项目结构说明

这个仓库是 DUTIR-BioNLP 课题组主页的源代码，使用 Jekyll 静态站点生成器和 Minimal Mistakes 主题构建。日常维护时，大多数内容只需要修改 `_pages/`、`_data/` 和 `assets/images/` 里的文件。

## 快速定位：想改哪里就看这里

| 想修改的内容 | 主要修改文件 | 说明 |
| --- | --- | --- |
| 首页大图、首页标题、欢迎语、研究方向、联系地址 | `_pages/home.md` | 首页 URL 是 `/`，大图来自 `assets/images/dut.jpg`，三块图文内容在 `row_research`、`row_code`、`row_about_us` 中。 |
| 顶部导航栏菜单 | `_data/navigation.yml` | 控制导航栏显示的栏目名称和链接，例如 News、People、Publications。 |
| 课题组成员信息 | `_data/authors.yml` | 成员姓名、身份、头像、简介、主页链接等都在这里。 |
| 成员页分组和展示顺序 | `_pages/people.md` | 这里按 `role` 调用 `_data/authors.yml` 中的成员，例如 Professors、PhD、Master。 |
| 成员头像 | `assets/images/bio/` | 头像文件放在这里，然后在 `_data/authors.yml` 的 `avatar` 字段引用。 |
| 新闻动态 | `_pages/News.md` | 直接用 Markdown 列表维护新闻。 |
| 论文成果列表 | `_pages/publications.md` | 当前论文是直接写在这个 Markdown 文件中的，按年份分组。 |
| 旧版论文成果页 | `_pages/publications-old.md` | 保留的旧页面，一般不用改，除非你明确要恢复旧展示方式。 |
| 资源与工具 | `_pages/resources&tools.md` | 工具介绍、图片和 GitHub 链接在这里维护。 |
| 工具图片 | `assets/images/tools/` | 例如 `taiyi.png`。 |
| 竞赛/挑战赛成果 | `_pages/challenges.md` | 直接用 Markdown 列表维护。 |
| 联系页面 | `_pages/contact.md` | 目前内容仍是模板示例，若要正式使用应改成课题组真实地址、邮箱和表单。 |
| 网站标题、描述、Logo、页脚链接、主题配置 | `_config.yml` | 改完后通常需要重新启动本地 Jekyll 服务才会生效。 |
| Logo 和 favicon | `assets/images/logo/`、`favicon.ico` | `_config.yml` 中的 `logo` 字段引用 `assets/images/logo/logo.png`。 |
| 自定义样式 | `_sass/custom/` | 人员卡片、页眉页脚、无侧边栏、论文展示等样式在这里。 |
| 页面模板和组件 | `_layouts/`、`_includes/` | 控制页面渲染结构，普通内容维护一般不需要改。 |

## 目录结构说明

```text
DUTIR-BioNLP.github.io/
├── _config.yml                 # Jekyll 全站配置：标题、描述、Logo、主题、插件、默认布局等
├── _data/
│   ├── authors.yml             # 课题组成员数据
│   └── navigation.yml          # 顶部导航栏
├── _pages/
│   ├── home.md                 # 首页
│   ├── News.md                 # 新闻页
│   ├── people.md               # 成员页
│   ├── publications.md         # 论文成果页
│   ├── resources&tools.md      # 资源与工具页
│   ├── challenges.md           # 挑战赛成果页
│   ├── contact.md              # 联系页
│   ├── teaching.md             # 教学页，目前基本为空
│   ├── 404.md                  # 404 页面
│   ├── category-archive.md     # 分类归档页
│   ├── tag-archive.md          # 标签归档页
│   ├── year-archive.md         # 年份归档页
│   └── profiles/               # 单独成员或个人 profile 页面
├── _includes/                  # Jekyll 可复用组件
├── _layouts/                   # 页面布局模板
├── _sass/
│   ├── custom/                 # 本项目自定义样式
│   └── skins/                  # 明暗主题配色
├── assets/
│   ├── css/                    # 样式入口文件
│   └── images/
│       ├── bio/                # 成员头像
│       ├── home/               # 首页内容配图
│       ├── logo/               # 网站 Logo
│       └── tools/              # 资源工具图片
├── src/python/                 # 自动添加/更新成员和论文的辅助脚本
├── records/                    # 自动化脚本使用的记录文件
├── .github/                    # GitHub 工作流、Issue 模板等
├── Gemfile                     # Ruby/Jekyll 依赖
└── README.md                   # 原项目说明文档
```

## 页面和 URL 对应关系

Jekyll 页面文件开头的 `permalink` 决定网页地址。当前主要页面如下：

| 页面文件 | 网页地址 | 导航栏中是否出现 |
| --- | --- | --- |
| `_pages/home.md` | `/` | 首页，一般通过网站根地址访问 |
| `_pages/News.md` | `/news/` | 是 |
| `_pages/people.md` | `/people/` | 是 |
| `_pages/publications.md` | `/publications/` | 是 |
| `_pages/resources&tools.md` | `/resources&tools/` | 是 |
| `_pages/challenges.md` | `/challenges/` | 是 |
| `_pages/contact.md` | `/contact/` | 否 |
| `_pages/teaching.md` | `/teaching/` | 否 |

如果你新增一个页面，通常需要做两件事：

1. 在 `_pages/` 下新增一个 `.md` 文件，并在文件开头写好 `title` 和 `permalink`。
2. 如果希望它出现在顶部导航栏，继续修改 `_data/navigation.yml`。

示例：

```yaml
main:
  - title: "New Page"
    url: /new-page/
```

## 常见修改方式

### 修改首页

打开 `_pages/home.md`：

- `title`：浏览器和页面使用的首页标题。
- `header.overlay_image`：首页顶部大图。
- `header.actions`：首页顶部按钮。
- `excerpt`：首页顶部简介。
- `row_research`：欢迎介绍。
- `row_code`：研究方向。
- `row_about_us`：联系信息。

首页使用的图片主要在：

- `assets/images/dut.jpg`
- `assets/images/home/home_1.jpg`
- `assets/images/home/home_2.jpg`
- `assets/images/home/blackbuilding.jpg`

### 修改成员信息

成员数据在 `_data/authors.yml`。每个成员是一个 YAML 数据块，大致格式如下：

```yaml
Member Name:
  name: Member Name
  role: PhD
  avatar: /assets/images/bio/member.jpg
  note: 2024-
  bio: Research direction
  alumni: false
  links:
    - label: Website
      url: https://example.com
```

常用字段：

- `name`：页面上显示的姓名。
- `role`：成员身份，需要和 `_pages/people.md` 中调用的分组一致，例如 `Professors`、`PhD`、`Master`。
- `avatar`：头像路径，图片通常放到 `assets/images/bio/`。
- `note`：入学年份、备注等。
- `bio`：研究方向或简介。
- `alumni`：是否为毕业成员，`false` 表示当前成员，`true` 表示校友。
- `links`：个人主页、Google Scholar、GitHub 等链接。

成员页 `_pages/people.md` 通过下面这种 include 自动筛选成员：

```liquid
{% include card-authors-with-role.html authors=site.data.authors role="PhD" alumni=false %}
```

如果要新增一个身份分组，例如 Postdoc，需要同时：

1. 在 `_data/authors.yml` 中把成员的 `role` 写成同一个值。
2. 在 `_pages/people.md` 中增加对应标题和 include。

### 修改论文成果

当前论文成果直接维护在 `_pages/publications.md` 中，不是从 `_posts/` 自动生成。

修改时注意：

- 年份目录在文件顶部，例如 `[[2024]](#2024)`。
- 每个年份段落用标题和锚点配合：

```markdown
# 2024
<a name="2024"></a>
```

- 论文条目目前使用 Markdown 有序列表：

```markdown
1. Author A, Author B. **Paper Title** [J]. *Venue*, Year. [[paper]](https://example.com)
```

如果新增年份，记得同时更新顶部的年份导航。

### 修改资源与工具

打开 `_pages/resources&tools.md`。当前页面使用 HTML 表格展示工具。工具图片放在 `assets/images/tools/`，引用方式类似：

```html
<img src="/assets/images/tools/taiyi.png?raw=true" />
```

如果新增工具，建议复制已有 `<tr>...</tr>` 结构，再替换图片、标题、链接和描述。

### 修改新闻和挑战赛

新闻在 `_pages/News.md`，挑战赛成果在 `_pages/challenges.md`。两者都是 Markdown 列表，直接追加新条目即可。

示例：

```markdown
- [07/2026] News content here.
```

### 修改样式

普通内容维护一般不用改样式。如果需要调整显示效果，可以优先看这些文件：

- `_sass/custom/people-card.scss`：成员卡片样式。
- `_sass/custom/header-footer.scss`：页眉和页脚样式。
- `_sass/custom/no-sidebar.scss`：无侧边栏页面样式。
- `_sass/custom/display-publications.scss`：论文展示相关样式。
- `_sass/skins/light.scss`、`_sass/skins/dark.scss`：浅色和深色主题配色。

### 修改模板组件

如果页面数据没问题，但展示结构需要变，才需要看 `_includes/` 和 `_layouts/`：

- `_includes/card-authors-with-role.html`：成员卡片渲染逻辑。
- `_includes/infer-icon.html`：根据链接类型推断图标。
- `_includes/masthead.html`：顶部区域。
- `_layouts/publication.html`：publication 类型页面布局。

这类文件会影响多个页面，修改前建议先确认影响范围。

## 辅助脚本和记录文件

`src/python/` 中有一些自动维护脚本，主要用于添加或更新成员、论文：

- `add_update_member.py`
- `add_update_publication.py`
- `add_publication_by_id.py`
- `add_publications_by_author.py`
- `auto_update_publications.py`

`records/semantic_paper_ids_ignored.json` 用于记录自动论文更新时忽略的 Semantic Scholar 论文 ID。

如果只是手动维护主页内容，可以暂时不用这些脚本。

## 维护注意事项

1. 修改 `_config.yml` 后，本地预览服务通常需要重启才会读取新配置。
2. `_data/authors.yml` 是 YAML 文件，缩进很重要，建议统一使用两个空格缩进。
3. 图片路径一般以 `/assets/...` 开头，表示从网站根目录引用。
4. 文件名和路径尽量避免空格。当前已有 `resources&tools.md`，修改或引用时注意 `&` 字符。
5. 当前仓库没有 `_posts/` 目录，论文成果主要写在 `_pages/publications.md`，不要被 README 中模板项目的 `_posts/papers` 说明误导。
6. `_data/authors.yml` 中部分中文图片路径看起来存在编码异常。如果成员头像显示不出来，可以优先检查 `avatar` 字段是否和 `assets/images/bio/` 下的真实文件名一致。
