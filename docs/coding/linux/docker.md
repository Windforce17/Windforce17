## swarm 
下面问题需要考虑下：  
网络隔离?  
代理?  

## 一些命令和脚本
- 删除所有None镜像`docker rmi -f $(docker images -f "dangling=true" -q)`  
- 删除所有运行中镜像docker rm -f $(docker ps -aq)
- docker ubuntu 安装脚本
```bash
sudo apt-get install -y\
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common &&
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add - &&

sudo add-apt-repository \
   "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
   $(lsb_release -cs) \
   stable" &&
sudo apt-get update &&
sudo apt-get install -y docker-ce


sudo echo -e "{\n 
  \"registry-mirrors\": [\"https://docker.mirrors.ustc.edu.cn/\"]
}" >/etc/docker/daemon.json 
sudo systemctl restart docker
```

- 或者`curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun`


- docker 监听tcp，打开api
```bash
# 查看配置文件位于哪里
systemctl show --property=FragmentPath docker 
#编辑配置文件内容，接收所有ip请求
sudo vim /lib/systemd/system/docker.service  
ExecStart=/usr/bin/dockerd -H unix:///var/run/docker.sock -H tcp://0.0.0.0:2376
#重新加载配置文件，重启docker daemon
sudo systemctl daemon-reload
sudo systemctl restart docker
```
- docker proxt set
```sh
if [ ! -d "/etc/systemd/system/docker.service.d/"]; then
    mkdir /etc/systemd/system/docker.service.d/
fi

if [ ! -d "/etc/systemd/system/docker.service.d/"]; then
    mkdir /etc/systemd/system/docker.service.d/
fi
echo '[Service]
Environment="HTTP_PROXY=http://127.0.0.1:8123" "HTTPS_PROXY=http://127.0.0.1:8123" "NO_PROXY=localhost,127.0.0.1"' > /etc/systemd/system/docker.service.d/http-proxy.conf

systemctl daemon-reload
systemctl restart docker
```

- 利用ssh转发unix sock
```sh
ssh -nNT -L /tmp/docker.sock:/var/run/docker.sock  <USER>@<IP> &
export DOCKER_HOST=unix:///tmp/docker.sock # docker client will communicate with this sock
```