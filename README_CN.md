# gowebly – 新一代 CLI 工具，可使用 htmx 和 hyperscript 在 Go 中构建令人惊叹的网络应用程序

[![Go version][go_version_img]][go_dev_url]
[![Go report][go_report_img]][go_report_url]
[![Code coverage][go_code_coverage_img]][repo_url]
[![License][repo_license_img]][repo_license_url]

[English][repo_url] | [Русский][repo_readme_ru_url] | **中文** | 
[Español][repo_readme_es_url]

这款 CLI 工具可在后端使用 **Go**，在前端使用 [**htmx**][htmx_url] 和 
[**hyperscript**][hyperscript_url] 以及最流行的原子/实用工具优先 **CSS 框架**，轻松构建令人惊叹的网络应用程序。

特点

- 根据 [Apache 2.0][repo_license_url] 许可，100%免费开源；
- 适用于任何知识水平和技术专长的开发人员；
- 文档齐全，作者提供了大量提示和帮助；
- 智能 CLI，可完成大部分常规设置和生产准备工作；
- 有助于更快地进入 Go + htmx + hyperscript 技术栈；
- 可在项目中添加即用型和完全定制的原子/实用工具优先 CSS 框架；
- 为你的 Go 代码提供一个用户友好型助手库；
- 包含如何使用该框架的综合示例。

> 💬 作者的话： 为了让您充分了解该项目，我们录制了一段简短的 [📺视频][gowebly_youtube_video_url]，并准备了一篇介绍 
> [📝文章][gowebly_devto_article_url]，演示了 `gowebly` CLI 的主要功能。

<img width="100%" alt="gowebly logo" src="https://github.com/gowebly/gowebly/assets/11155743/55c80da2-30c6-45e7-a813-1ddc42764480">

## ⚡️ 快速启动

首先，[下载][go_download_url] 并安装 Go。需要安装 `1.21`（或更高版本）。

现在，无需安装即可使用 `gowebly`。只需 [`go run`][go_run_url] 即可创建一个新项目，并使用 
[默认][repo_default_config] 配置：

```console
go run github.com/gowebly/gowebly@latest create
```

就是这样！🔥 一个精彩的网络应用程序，使用内置的 net/http 包（作为 Go 后端）、htmx 和 hyperscript，可以在你的 Go 
HTML 模板中使用。

### 🔹 快速启动的完整 Go-way

如果还想通过 Golang 将 `gowebly` CLI 安装到系统中，请使用 [`go install`][go_install_url] 命令：

```console
go install github.com/gowebly/gowebly@latest
```

### 🍺 通过自制软件快速启动

GNU/Linux 和 Apple macOS 用户可以通过 [Homebrew][brew_url] 安装 `gowebly` CLI。

点击新公式：

```console
brew tap gowebly/tap
```

安装 `gowebly`：

```console
brew install gowebly/tap/gowebly
```

### 🐳 通过 Docker 快速启动

请随意使用我们 [官方 Docker 镜像][docker_image_url] 中的 `gowebly` CLI，并在隔离的容器中运行它：

```console
docker run --rm -it -v ${PWD}:${PWD} -w ${PWD} gowebly/gowebly:latest create
```

### 📦 其他快速入门方法

从 [Releases][repo_releases_url] 页面为 Windows、`deb`、`rpm`、`apk` 或 Arch Linux 
软件包下载现成的 `exe` 文件。

## 📖 完整的用户指南

为了获得完整的使用指南并理解 `gowebly` CLI 的基本原理，我们在 README 文件中对每条命令都做了全面的解释。

> 💬 作者的话 我们一直非常珍惜您的时间，并希望您能尽快开始在这个超棒的技术栈上构建真正出色的网络产品！

我们希望您能找到所有问题的答案！👌 但是，如果您没有找到所需的信息，请随时创建一个 [issue][repo_issues_url] 或发送一个 
[PR][repo_pull_request_url] 到此版本库。

### `init`

命令在当前文件夹下创建默认配置文件（[`.gowebly.yml`][repo_default_config]）。

```console
gowebly init
```

> 💡 注意：当然，如果你对新项目的以下默认配置感到满意，也可以跳过这一步：
>
> - Go 模块 (`go.mod`) 和 `package.json` 名称设置为项目；
> - 后端部分不使用任何 Go 框架（仅使用内置的 net/http 包）；
> - 前端部分不使用任何 CSS 框架（仅使用代码示例的默认样式）；
> - 前端部分的 JavaScript 运行环境将使用 Node.js；
> - 服务器端口为 `5000`，超时（秒）： 读取超时 5 秒，写入超时 10 秒；
> - 最新版本的 htmx 和 hyperscript。

<img width="720" alt="gowebly init" src="https://github.com/gowebly/gowebly/assets/11155743/679dd0e1-ecd6-4cfb-b145-c9f551ab2d9c">

通常情况下，创建的配置文件包含以下选项：

```yaml
backend:
   module_name: project # (string) option can be any name of your Go module (for example, 'github.com/user/project')
   go_framework: default # (string) option can be one of the values: 'fiber', 'echo', 'chi', or 'default'
   port: 5000 # (int) option can be any port that is not taken up on your system
   timeout:
      read: 5 # (int) option can be any number of seconds, 5 is recommended
      write: 10 # (int) option can be any number of seconds, 10 is recommended

frontend:
   package_name: project # (string) option can be any name of your package.json (for example, 'project')
   css_framework: default # (string) option can be one of the values: 'tailwindcss', 'unocss', or 'default'
   runtime_environment: default # (string) option can be one of the values: 'bun', or 'default'
   htmx: latest # (string) option can be any existing version
   hyperscript: latest # (string) option can be any existing version
```

但是，您可以为项目后台选择任何 Go 框架：

| Go framework | 说明                                               |
|--------------|--------------------------------------------------|
| `default`    | 不使用任何 Go 框架（仅使用内置的 [net/http][net_http_url] 软件包） |
| `fiber`      | 使用 Go 后端和 [Fiber][fiber_url] 网络框架                |
| `echo`       | 使用 Go 后端和 [Echo][echo_url] 网络框架                  |
| `chi`        | 使用 Go 后端和 [chi][chi_url] 可组合路由器                  |

此外，您还可以为您的项目选择 htmx、hyperscript 和最流行的原子/实用工具优先 CSS 框架之一的版本：

| CSS framework | 说明                                           |
|---------------|----------------------------------------------|
| `default`     | 不使用任何 CSS 框架（代码示例仅使用默认样式）                    |
| `tailwindcss` | 使用 [Tailwind CSS][tailwindcss_url] 作为 CSS 框架 |
| `unocss`      | 使用 [UnoCSS][unocss_url] 作为 CSS 框架            |

此外，您还可以为前端部分设置一个 JavaScript 运行环境：

| JavaScript runtime | 说明                                         |
|--------------------|--------------------------------------------|
| `default`          | 将 [Node.js][nodejs_url] 用作 JavaScript 运行环境 |
| `bun`              | 将 [Bun][bun_url] 用作 JavaScript 运行环境        |

### `create`

命令创建一个新项目，该项目包含 Go 后端、htmx 和 hyperscript 以及（可选）原子/实用工具优先 CSS 框架。

```console
gowebly create
```

> 💡 注意：如果不运行 `init` 命令来创建配置文件（`.gowebly.yml`），则 `gowebly` CLI 会以 
> [default][repo_default_config] 配置创建一个新项目。

<img width="720" alt="gowebly create" src="https://github.com/gowebly/gowebly/assets/11155743/35b15677-4991-406d-b666-dfbc40beb1ce">

每次为项目执行 `create` 命令时：

1. CLI 会验证配置并将所有设置应用到当前项目；
2. CLI 准备项目的后台部分（生成项目结构和所需的实用程序文件，运行 `go mod tidy`）；
3. CLI 准备项目的前端部分（生成所需的实用程序文件，首次运行 `npm|bun install` 和 `npm|bun run build:dev`）；
4. CLI 会下载最小化版本的 htmx 和 hyperscript（来自官方和可信的 [unpkg.com][unpkg_url] CDN）到
   `./static` 文件夹，并将它们作为分隔的 `<script>` 标记（位于 `<body>` 标记的底部）放入 Go HTML 模板 
   [`templates/main.html`][repo_main_layout]。

通常情况下，创建的项目包含以下文件和文件夹：

```console
.
├── assets
│   └── styles.css
├── static
│   ├── favicon.ico
│   ├── htmx.min.js
│   ├── hyperscript.min.js
│   └── styles.css
├── templates
│   ├── pages
│   │   └── index.html
│   └── main.html
├── .gitignore
├── go.mod
├── go.sum
├── handlers.go
├── main.go
├── package-lock.json
├── package.json
└── server.go
```

### `run`

命令在开发（非生产）模式下运行项目。

```console
gowebly run
```

> 💡 注意：如果不运行 `init` 命令来创建配置文件（`.gowebly.yml`），则 `gowebly` CLI 会以 
> [default][repo_default_config] 配置运行项目。

<img width="720" alt="gowebly run" src="https://github.com/gowebly/gowebly/assets/11155743/51c05652-4601-4f8b-8722-20401d0099d1">

每次为项目执行 `run` 命令时：

1. CLI 会验证配置并将所有设置应用到当前项目；
2. CLI 准备项目的前端部分（运行 `npm|bun run build:dev`）；
3. CLI 将所选 CSS 框架的开发（非生产）版本放入 `./static` 文件夹，并将其作为 `<link>` 标记（位于 `<head>` 
   标记的底部）放入 Go HTML 模板 [`templates/main.html`][repo_main_layout]；
4. 通过简单的 `go run` 命令，CLI 可使用默认配置（或 `.gowebly.yml` 配置文件）中的设置启动项目的后端。

### `build`

命令来为生产构建项目，并为部署准备 Docker 文件。

```console
gowebly build [OPTION]
```

> 💡 注意：如果不运行 `init` 命令来创建配置文件（`.gowebly.yml`），则 `gowebly` CLI 会以 
> [default][repo_default_config] 配置来构建项目。

<img width="720" alt="gowebly build" src="https://github.com/gowebly/gowebly/assets/11155743/ac35b01f-0596-4d33-832e-1618709497d3">

您可以添加以下选项：

| Option          | 说明                                          | 是否需要？ |
|-----------------|---------------------------------------------|-------|
| `--skip-docker` | 跳过生成 Docker 文件的过程（如果您有自己的 Docker 文件，这将很有帮助） | 没有    |

每次为项目执行 `build` 命令时：

1. CLI 会验证配置并将所有设置应用到当前项目；
2. CLI 会下载最小化版本的 htmx 和 hyperscript（来自官方和可信的 [unpkg.com][unpkg_url] CDN）到
   `./static` 文件夹，并将它们作为分隔的 `<script>` 标记（位于 `<body>` 标记的底部）放入 Go HTML 模板 
   [`templates/main.html`][repo_main_layout]；
3. CLI 为选定的 CSS 框架准备一个生产版本，并将其作为一个 `<link>` 标记（位于 Go HTML 模板 
   [`templates/main.html`][repo_main_layout] 中 `<head>` 标记的底部）；
4. 如果未设置 `-skip-docker` 选项，CLI 会在项目文件夹根目录下生成清晰且文档齐全的 Docker 文件（
   `.dockerignore`、`Dockerfile`、`docker-compose.yml`），以便通过
   [Portainer][portainer_url] （推荐）或手动将其部署到远程服务器的隔离容器中。

## 🙋 用户友好型助手

`gowebly` CLI 有一个用户友好的 [helpers][gowebly_helpers_url] 库，可用于编写代码。这将帮助您以更快的速度在 
Go 中构建精美的网络应用程序。

```console
go get -u github.com/gowebly/helpers
```

> 💡 注意：`create` 命令创建的 Go 后端已经包含了 `gowebly helpers` 库，但你也可以在其他项目中使用这些助手。

## 🎯 创作动力

请告诉我们，您有多少次不得不从头开始一个新项目，并进行痛苦的手动配置？
进行痛苦的手动配置？🤔 特别是当你刚刚熟悉一种新技术或堆栈时，一切对你来说都是新的。

对于包括我们在内的许多开发人员来说，这个过程尽可能乏味甚至令人沮丧，而且没有任何有用的工作量。这是一个非常令人沮丧的过程，会让任何开发人员远离技术。

为什么不把这些可怕的手工工作交给机器呢？让它们为我们完成所有的艰苦工作，我们只需创建出色的网络产品，而不必考虑构建和部署。

这就是我们创建 `gowebly` CLI 及其助手库的原因，它可以帮助您使用 htmx、hyperscript 和流行的原子/实用工具优先 CSS 
框架，在 Go 语言中创建令人惊叹的网络应用程序。

我们就是来帮你（和我们自己）免去这些日常的痛苦的！✨

> 💬 作者的话： 此前，我们已经拯救过世界一次，那就是 [Create Go App][cgapp_url]（没错，那也是我们的项目）。
> [GitHub stars][cgapp_stars_url] 对这个项目的统计不会说谎：超过 2.2 千名不同国家、不同水平的开发者通过这个 CLI 
> 工具启动了一个新项目。

## 🏆 双赢合作

现在，我邀请您参与这个项目！让我们共同努力，为开发人员打造当今网络上最实用的工具。

- [Issues][repo_issues_url]：提出问题并提交您的功能。
- [Pull requests][repo_pull_request_url]：提交您对当前版本的改进。

欢迎您提交 PR 和问题！谢谢 😘

## ⚠️ 许可证

[`gowebly`][repo_url] 是根据 [Apache 2.0 License][repo_license_url] 授权的免费开源软件，由 
[Vic Shóstak][author_url] 创建和支持，其中 🩵 代表人和机器人。 根据 
[Creative Commons 许可][repo_cc_license_url] 发布的官方徽标 (CC BY-SA
4.0 International).

<!-- Go links -->

[go_download_url]: https://golang.org/dl/
[go_run_url]: https://pkg.go.dev/cmd/go#hdr-Compile_and_run_Go_program
[go_install_url]: https://golang.org/cmd/go/#hdr-Compile_and_install_packages_and_dependencies
[go_report_url]: https://goreportcard.com/report/github.com/gowebly/gowebly
[go_dev_url]: https://pkg.go.dev/github.com/gowebly/gowebly
[go_version_img]: https://img.shields.io/badge/Go-1.21+-00ADD8?style=for-the-badge&logo=go
[go_code_coverage_img]: https://img.shields.io/badge/code_coverage-33.8%25-success?style=for-the-badge&logo=none
[go_report_img]: https://img.shields.io/badge/Go_report-A+-success?style=for-the-badge&logo=none

<!-- Repository links -->

[repo_url]: https://github.com/gowebly/gowebly
[repo_issues_url]: https://github.com/gowebly/gowebly/issues
[repo_pull_request_url]: https://github.com/gowebly/gowebly/pulls
[repo_releases_url]: https://github.com/gowebly/gowebly/releases
[repo_license_url]: https://github.com/gowebly/gowebly/blob/main/LICENSE
[repo_license_img]: https://img.shields.io/badge/license-Apache_2.0-red?style=for-the-badge&logo=none
[repo_cc_license_url]: https://creativecommons.org/licenses/by-sa/4.0/
[repo_readme_ru_url]: https://github.com/gowebly/gowebly/blob/main/README_RU.md
[repo_readme_cn_url]: https://github.com/gowebly/gowebly/blob/main/README_CN.md
[repo_readme_es_url]: https://github.com/gowebly/gowebly/blob/main/README_ES.md
[repo_default_config]: https://github.com/gowebly/gowebly/blob/main/internal/attachments/configs/default.yml
[repo_main_layout]: https://github.com/gowebly/gowebly/blob/main/internal/attachments/templates/frontend/main.html

<!-- Author links -->

[author_url]: https://github.com/koddr

<!-- Readme links -->

[gowebly_youtube_video_url]: https://www.youtube.com/watch?v=qazYscnLku4
[gowebly_devto_article_url]: https://dev.to/koddr/a-next-generation-cli-tool-for-building-amazing-web-apps-in-go-using-htmx-hyperscript-336d
[gowebly_helpers_url]: https://github.com/gowebly/helpers
[cgapp_url]: https://github.com/create-go-app/cli
[cgapp_stars_url]: https://github.com/create-go-app/cli/stargazers
[nodejs_url]: https://nodejs.org
[bun_url]: https://bun.sh
[docker_image_url]: https://hub.docker.com/repository/docker/gowebly/gowebly
[portainer_url]: https://docs.portainer.io
[brew_url]: https://brew.sh
[htmx_url]: https://htmx.org
[hyperscript_url]: https://hyperscript.org
[tailwindcss_url]: https://tailwindcss.com
[unocss_url]: https://unocss.dev
[unpkg_url]: https://unpkg.com
[net_http_url]: https://pkg.go.dev/net/http
[fiber_url]: https://github.com/gofiber/fiber
[echo_url]: https://github.com/labstack/echo
[chi_url]: https://github.com/go-chi/chi
