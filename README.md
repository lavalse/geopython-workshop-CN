[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/geopython/geopython-workshop/master?labpath=workshop%2Fjupyter%2Fcontent%2Fnotebooks%2F01-introduction.ipynb)

# 使用 Python 进行地理空间分析（Doing Geospatial in Python）

## 关于本仓库（About This Repository）

本仓库 fork 自官方项目  
**geopython / geopython-workshop**  
https://github.com/geopython/geopython-workshop

原项目由 Geopython 社区维护，是在 FOSS4G 等会议中广泛使用的
**“Doing Geospatial in Python”** 官方 Workshop 教材。

---

### 本仓库的目标

本仓库的目标是：

- 将官方 Workshop 内容 **翻译成中文**
- 为中文使用者补充必要的背景说明（GIS / Python / 环境）
- 降低中文学习者进入 Geopython 生态的门槛
- 作为个人与中文社区学习、教学、分享之用

本仓库 **不改变原始 Workshop 的结构和技术路线**，  
仅在内容层面进行翻译与说明补充。

---

### 与官方仓库的关系

- 本仓库为 **非官方中文翻译版本**
- 核心结构、Notebook 顺序与官方仓库保持一致
- 将尽可能 **跟随官方仓库的更新节奏进行同步**
- 如官方内容发生较大变更，将以官方版本为准

如需获取**最新英文内容或参与官方开发**，  
请直接参考原始仓库：

https://github.com/geopython/geopython-workshop

---

Workshop 的入口文档请参见：  
https://geopython.github.io/geopython-workshop

## 安装（Installation）

### 系统要求（Requirements）

本 Workshop 需要你的系统中已安装：
- [Docker](https://docker.com)
- [Docker Compose](https://docs.docker.com/compose/)

### Docker 镜像（Docker Images）

本 Workshop 使用的 Docker 镜像可在 [DockerHub](https://hub.docker.com/r/geopython/geopython-workshop) 获取。
Workshop 镜像名称为 `geopython/geopython-workshop[:latest]`。
请注意：Docker 镜像主要包含所有（Python）组件/依赖。实际的 workshop 内容（数据 + notebooks）将通过
Docker Volume 的方式挂载。除测试与开发外（见下文），无需自行构建 Docker 镜像。

## 运行（Running）

所有服务均通过一个 [Docker Compose 文件](https://github.com/geopython/geopython-workshop/blob/master/workshop/docker-compose.yml) 启动。

Linux、macOS 或 WSL：

```bash
cd workshop
# start workshop
./geopython-workshop-ctl.sh start
# display URL and open in default web browser, if a browser does not open, then copy the url from the command output to your browser.
./geopython-workshop-ctl.sh url
# stop workshop
./geopython-workshop-ctl.sh stop
```

Windows（Powershell 或 Command Prompt）：

```bat
cd workshop
.\win-geopython-workshop-ctl.bat start
.\win-geopython-workshop-ctl.bat url
.\win-geopython-workshop-ctl.bat stop
```

Windows（Powershell + bash）：

```bash
cd workshop
# start workshop
bash ./geopython-workshop-ctl.sh start
# display URL and open in default web browser
bash ./geopython-workshop-ctl.sh url
# stop workshop
bash ./geopython-workshop-ctl.sh stop
```

NB [Jupyter notebook](https://en.wikipedia.org/wiki/Project_Jupyter) 需要 **token**。该 token 会在启动时显示在 jupyter 容器日志中：

`http://127.0.0.1:8888/?token=<longtokenhexstring>`.

由于 Docker Compose 可能在后台运行，你可以通过 `docker logs --follow geopython-workshop-jupyter` 查看日志输出。或者在
Docker Desktop UI 中选择 jupyter 容器查看其日志。

### 构建（Building）

你也可以随时从本仓库自行构建 Docker 镜像，例如用于修复 bug：

```bash
git clone https://github.com/geopython/geopython-workshop.git
cd geopython-workshop.git/workshop/jupyter
./build.sh
```

### 说明（Notes）

- 在 Linux 上，Docker 必须由非 root 用户进行管理。请务必完成以下 [安装后步骤](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)。
- 默认情况下，Web 服务 pygeoapi 和 pycsw 并非普通 workshop（如 FOSS4G）所必需。
- 如果你使用 pygeoapi：在 macOS Monterey 上存在端口 5000 已被占用的问题，因此会与 pygeoapi 使用的端口冲突。若你遇到错误 `OSError: [Errno 48] Address already in use`，说明你的机器受到该问题影响。解决方法是：在 macOS 的 `System Preferences->Sharing` 中禁用 *Airplay Receiver*（详见此博客 [post](https://progressstory.com/tech/port-5000-already-in-use-macos-monterey-issue/)）。

### Bugs and Issues

所有 bug、功能增强与问题均在 [GitHub](https://github.com/geopython/geopython-workshop/issues) 上进行管理。

## 联系方式（Contact）

https://gitter.im/geopython/geopython-workshop
