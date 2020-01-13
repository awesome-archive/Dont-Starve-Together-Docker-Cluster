# Dont-Starve-Together-Docker-Cluster

根据配置文件快速建立饥荒联机版 (DST)Docker 集群

## 运行状况

- 镜像大约 `580m`，包括底层 Ubuntu 镜像的话大约 `1G`
- 大概每个实例(带洞穴的)占内存`1G`左右，CPU似乎不怎么占用
- 存档在生成的 `data/名字/Master/save` 里面，要备份的话，请用 `chown` 到自己的用户名，再进行备份
- Mod的话请查看 `./template/dedicated_server_mods_setup.lua` 文件，有具体说明，建议 PC 机先建立一个世界，再把 Mod 配置好，最后再复制到对应位置( `dedicated_server_mods_setup.lua` 文件需要自行整理)

## 运行环境配置

### 不推荐使用 Windows

如果需要使用，则需要手动修改 Python 脚本文件中的对应 `mkdir cp` 等命令——因为这里是直接使用 `system(shell)` 脚本实现的。

### Python3 环境配置

1. 在 [Python官网](https://www.python.org/downloads/)下载对应自己操作系统的安装包
2. 然后安装环境，再配置环境变量(如果没有自动配置的话)

### Docker环境配置

1. 请根据自己的操作系统，在 [Docker 官方网站](https://docs.docker.com/engine/installation/#server)选择适合的 **DockerCE**
2. 如果是 Linux 的话，最好把自己的管理员用户添加到 Docker 用户组里，以免每次打命令都得加入 sudo，命令：`sudo usermod -aG docker $USER`
3. 安装 `docker-compose` :如果你是 Ubuntu ，可以直接使用命令:`sudo apt install docker-compose`，如果不是，请前往 [Docker官方网站](https://docs.docker.com/compose/install/)，并寻找自己的操作系统的安装方式
4. 至此，你应该有了一个正常的 Docker 环境，如果有问题可以根据 END 区的联系方式提交

## 基本使用说明

### 步骤介绍

1. Clone 项目:`git clone https://github.com/Thoxvi/Dont-Starve-Together-Docker-Cluster.git`
2. 进入目录:`cd ./Dont-Starve-Together-Docker-Cluster`
3. 根据模板修改 infos 文件，提供一个测试 Token (每一行对应一个实例,# 号注释，如果不需要密码的话请留空对应位置)
4. 执行生成脚本:`python3 makedata.py`
5. 转到工作目录:`cd data`
6. 启动容器:`docker-compose up`
7. 若不想查看 Log 的话，可以在`启动容器`步骤使用:`docker-compose up -d`
8. 更新,转到工作目录, `docker-compose stop` , 然后 `docker-compose up -d`

### 一套带走

```shell
git clone https://github.com/Thoxvi/Dont-Starve-Together-Docker-Cluster.git
cd ./Dont-Starve-Together-Docker-Cluster
python3 makedata.py
cd ./data
docker-compose up
```

## END

- 如果有任何建议或者 Bug 可以提 issue ，或者可以邮箱联系`A@Thoxvi.com`
- (｡･ω･｡)ﾉ♡
