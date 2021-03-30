# ks-jenkins
Jenkins distribution for [kubesphere](https://github.com/kubesphere/kubesphere)

`ks-jenkins` is an out-of-the-box solution which base on [custom-war-packager](https://github.com/jenkinsci/custom-war-packager).

# Get started
The docker images are below:

| | |
|---|---|
| official | `kubesphere/ks-jenkins:2.249.1` |
| experimental | `kubespheredev/ks-jenkins:2.249.1` |

## Build from source(kubesphere/jenkins-ks:2.176.2 arm64版本)

> [jcli](https://github.com/jenkins-zh/jenkins-cli) is a handy tool which can generate jenkins.war and docker image by one command line,此处需要注意将settings.xml文件放置到root/.m2/settings.xml目录且需确保java与maven已经安装成功
```bash
java -version

openjdk version "1.8.0_242"
OpenJDK Runtime Environment (build 1.8.0_242-b08)
OpenJDK 64-Bit Server VM (build 25.242-b08, mixed mode)

mvn -v

Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /usr/local/apache-maven-3.6.3
Java version: 1.8.0_242, vendor: Huawei Technologies Co., Ltd, runtime: /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.242.b08-1.h5.ky10.aarch64/jre
Default locale: zh_CN, platform encoding: UTF-8
OS name: "linux", version: "4.19.90-17.ky10.aarch64", arch: "aarch64", family: "unix"
```

```
git clone https://github.com/kubesphere/ks-jenkins.git
cd ks-jenkins
git checkout arm64
jcli cwp --install-artifacts --config-path formula.yaml
```
## kubesphere/jenkins-uc:v3.0.0 arm64版本编译
> kubesphere/jenkins-uc:v3.0.0官方无Dockerfile文件，对于arm64的编译只需对x86镜像`kubesphere/jenkins-uc:v3.0.0`中的/webroot用 `docker cp` 命令拷贝到宿主机，
然后构建如下Dockerfile即可
```bash
FROM busybox:latest
COPY webroot/ /webroot/
```
## maven的安装
```
tar -xvf  apache-maven-3.6.3-bin.tar.gz
sudo mv -f apache-maven-3.6.3 /usr/local/
vim /etc/profile
export MAVEN_HOME=/usr/local/apache-maven-3.6.3
export PATH=${PATH}:${MAVEN_HOME}/bin
source /etc/profile
```
# Plugins
Please pay attention to these plugins, we still need to keep use a special version of them:

| Name | Version | Description |
|---|---|---|
| `pipeline-input-step` | `2.12-rc390.24ce2a334298` | Depends on [PR-33](https://github.com/jenkinsci/pipeline-input-step-plugin/pull/33) |
