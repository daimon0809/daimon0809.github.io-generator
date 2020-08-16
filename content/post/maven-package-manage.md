---
title: "maven解决包冲突"
date: 2020-05-20T11:00:07+08:00
draft: false
---

## maven传递性依赖的⾃动管理
原则：绝对不允许最终的classpath出现同名不同版本的jar包

## maven依赖冲突的解决
原则：最近的胜出
即：如下依赖D0.1版本胜出
```
A-->B-->C-->D0.2
A-->E-->D0.1
```
## 包冲突场景（包冲突通常会如下一些错误打屏）：
* ========== AbstractMethodError ==========
* ========== NoClassDefFoundError =========
* ========== ClassNotFoundException =======
* ========== LinkageError =================
* ========== NoSuchMethodError ============


## 情景还原（NoSuchMethodError）:
如下图：<br>
    ![](/images/maven-conflit_20200608000102.png)

## 解决方式：

根据上图信息查看Class文件MappingJacksonValue<br>
确没有getJsonpFunction()方法
    ![](/images/calss-method_20200608002846.png)

### 找到差异位置

#### 命令行方式对比差异：
1. mvn dependency:tree  执行得到如下依赖树<br>
    ![](/images/mvn-dependency_20200608003702.png)
2. 查看所有maven依赖<br>
    ![](/images/mvn-dependency3_20200608004340.png)
3. 对比差异<br> org.springframework:spring-web4.3.6RELEASE 版本被省略<br>
4. 查看org.springframework:spring-web4.3.6RELEASE源码,确有getJsonpFunction()方法<br>
    ![](/images/class-method2_20200608005513.png)

#### 插件方式对比差异：
1. 安装插件 maven helper<br>
    ![](/images/maven-helper_20200608005857.png)
2. ![](/images/maven-helper-resolve_20200608010249.png)

### 解决冲突
1. 导入需要的版本jar包,如下图<br>
    ![](/images/jar4.3.6_20200608011321.png)

2. 去除不需要的版本jar包，如下图<br>
    ![](/images/jar5.1.8_20200608011439.png)



