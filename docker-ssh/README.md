
## ssh工具

方便构建流程中免密执行服务器命令部署新版本

禁用远程主机公钥检查，不用再固化公钥到known_hosts里面

/keys/config

```
StrictHostKeyChecking no
UserKnownHostsFile /dev/null
```

## 构建过程

1. 生成ssh免密私钥与公钥

```
$ cd keys && ssh-keygen -f id_rsa
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in id_rsb.
Your public key has been saved in id_rsb.pub.
The key fingerprint is:
SHA256:4cfHp68JL68M0Vk9a+nguXrFJLIfZ1F9hKELsJw3PS0 docker@docker.local
The key's randomart image is:
+---[RSA 2048]----+
|        .     .+o|
|       . + . +. +|
|        = + E +..|
|       . =.*.+o+ |
|        S =o=+=. |
|         o.o.B=  |
|        . ..+=.  |
|         o.oo+   |
|          +**..  |
+----[SHA256]-----+
```
2. 构建

```
docker build -t your.domain/ssh .
docker push your.domain/ssh
```

3. 拷贝./keys/id_rsa.pub公钥内容到目标服务器用户目录.ssh/authorized_keys

4. 在构建工具部署阶段使用，gitlab-ci示例

```
deploy:
  image: your.domain/ssh
  stage: deploy
  script:
    - ssh root@dev.server 'docker-compose pull some-service && docker-compose up -d some-service'
  only:
    - dev
```

