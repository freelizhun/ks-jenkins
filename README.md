# ks-jenkins
Jenkins distribution for [kubesphere](https://github.com/kubesphere/kubesphere)

`ks-jenkins` is an out-of-the-box solution which base on [custom-war-packager](https://github.com/jenkinsci/custom-war-packager).

# Get started
The docker images are below:

| | |
|---|---|
| official | `kubesphere/ks-jenkins:2.249.1` |
| experimental | `kubespheredev/ks-jenkins:2.249.1` |

## Build from source

[jcli](https://github.com/jenkins-zh/jenkins-cli) is a handy tool which can generate jenkins.war and docker image by one command line,此处需要注意将settings.xml文件放置到root/.m2/settings.xml目录
且需确保java与maven已经安装成功
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

`jcli cwp --install-artifacts --config-path formula.yaml`

# Plugins
Please pay attention to these plugins, we still need to keep use a special version of them:

| Name | Version | Description |
|---|---|---|
| `pipeline-input-step` | `2.12-rc390.24ce2a334298` | Depends on [PR-33](https://github.com/jenkinsci/pipeline-input-step-plugin/pull/33) |
