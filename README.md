# hello-word

This is a config repository center for spring cloud study.

springcloud配置的order.yml order-dev.yml...读取order-dev.yml时也会加载order.yml(存放order公共代码)

springcloud bus自动刷新配置webhook http://yuanpengs.free.idcfengye.com/monitor


c.s.e.MultipleJGitEnvironmentRepository : Cannot pull from remote the working tree is not clean.
后来在Spring Cloud官网找到了答案
https://github.com/spring-cloud/spring-cloud-config/blob/master/docs/src/main/asciidoc/spring-cloud-config.adoc#force-pull-in-git-repositories
 Spring Cloud配置服务器会复制远程git存储库，如果本地副本变得不干净(例如，通过OS进程更改文件夹内容)，那么Spring Cloud配置服务器就不能更新远程存储库中的本地副本。为了解决这个问题，有一个强制拉属性，如果本地副本是脏的，它将使Spring Cloud配置服务器从远程存储库中强制pull.

spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/spring-cloud-samples/config-repo
          force-pull: true
添加 force-pull 属性 默认是true
