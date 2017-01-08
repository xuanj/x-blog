---
title: nexus3.0搭建与使用
date: 2016-06-30 11:52:00
categories: maven
tags:
- nexus
- maven
---

> nexus3.0支持docker与npm，新东西，尝试下搭建与使用。看看与之前2.13版本有什么不同。

# 下载 解压 启动
[http://www.sonatype.org/nexus/](http://www.sonatype.org/nexus/)
下载好，解压好，在bin目录下./nexus start 进行启动。
[http://localhost:8081](http://localhost:8081) 访问启动好的nexus，用户名与2.13前版本一样
admin/admin123
<!-- more -->
# 配置代理
[http://repo2.maven.org/maven2](http://repo2.maven.org/maven2)这个中央库的包比较全，所以先配置一个代理。
{% img class /images/nexus301.png 配置repo1  %}
圈红的URL不再和2.13版本那样可以访问。开源中国的maven库就是用了3.0版本，所以现在也无法直接访问。
{% img class /images/nexus302.png repo的URL不可以访问  %}
将添加好的代理添加到public上去。
{% img class /images/nexus303.png repo添加到public  %}


# deploy部署一个jar到私服
## 先建一个maven项目。
省略，常用命令先百度。或者[常用命令请看之前的博客](http://xuanjian.site/java/maven/maven-入门使用/)
## settings.xml
主要看servers那个节点，deploy要用到账户密码进行登录。这里没有配置本地私服，而是在项目的pom.xml文件里配置。
因为本地私服是在本地跑，不是天天开着，所以，将仓库配置放到pom.xml不影响全局，而且，私服没启动，项目会自动到settings.xml查询可用的仓库。
{% codeblock lang:xml %}
<settings xmlns="http://maven.apache.org/SETTINGS/1.1.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.1.0 http://maven.apache.org/xsd/settings-1.1.0.xsd">
	<mirrors>
		<mirror>
			<id>repo2</id>
			<name>repo2</name>
			<url>http://repo2.maven.org/maven2</url>
			<mirrorOf>central</mirrorOf>
		</mirror>
		<mirror>
			<id>CN</id>
			<name>OSChina Central</name>
			<url>http://maven.oschina.net/content/groups/public/</url>
			<mirrorOf>central</mirrorOf>
		</mirror>
	</mirrors>
	<servers>
		<server>
			<id>nexus-releases</id>
			<username>admin</username>
			<password>admin123</password>
		</server>
		<server>
			<id>nexus-snapshots</id>
			<username>admin</username>
			<password>admin123</password>
		</server>
	</servers>
	<profiles>
		<profile> <!-- 全局指定使用jdk1.8 -->
			<id>jdk-1.8</id>
			<activation>
				<activeByDefault>true</activeByDefault>
				<jdk>1.8</jdk>
			</activation>
			<properties>
				<maven.compiler.source>1.8</maven.compiler.source>
				<maven.compiler.target>1.8</maven.compiler.target>
				<maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
			</properties>
		</profile>
	</profiles>
</settings>
{% endcodeblock %}

## pom.xml配置
{% codeblock lang:xml %}
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>hello-mvn</groupId>
	<artifactId>hello-mvn</artifactId>
	<version>1.0-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>hello-mvn</name>
	<url>http://maven.apache.org</url>

	<repositories>
		<repository>
			<id>nexus-releases</id>
			<name>repo1</name>
			<url>http://localhost:8081/repository/maven-central/</url>
			<releases>
				<enabled>true</enabled>
			</releases>
			<snapshots>
				<enabled>true</enabled>
				<updatePolicy>always</updatePolicy>
				<checksumPolicy>warn</checksumPolicy>
			</snapshots>
		</repository>
	</repositories>
	<pluginRepositories>
		<pluginRepository>
			<id>nexus-snapshots</id>
			<name>repo1</name>
			<url>http://localhost:8081/repository/maven-central/</url>
			<releases>
				<enabled>true</enabled>
			</releases>
			<snapshots>
				<enabled>true</enabled>
			</snapshots>
		</pluginRepository>
	</pluginRepositories>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>

	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>3.8.1</version>
			<scope>test</scope>
		</dependency>
	</dependencies>
	<distributionManagement>
		<snapshotRepository>
			<id>nexus-releases</id>
			<name>repo1</name>
			<url>http://localhost:8081/repository/maven-releases/</url>
		</snapshotRepository>
		<repository>
			<id>nexus-snapshots</id>
			<name>repo1</name>
			<url>http://localhost:8081/repository/maven-snapshots/</url>
		</repository>
	</distributionManagement>
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-shade-plugin</artifactId>
				<version>2.2</version>
				<executions>
					<execution>
						<phase>package</phase>
						<goals>
							<goal>shade</goal>
						</goals>
						<configuration>
							<transformers>
								<transformer
									implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
									<mainClass>com.x.test.mvn.App</mainClass>
								</transformer>
							</transformers>
						</configuration>
					</execution>
				</executions>
			</plugin>
		</plugins>
	</build>

	<profiles>
		<profile>
			<id>dev</id>
			<build>
				<plugins>
					<plugin>
						<groupId>org.apache.maven.plugins</groupId>
						<artifactId>maven-deploy-plugin</artifactId>
						<version>2.8.2</version>
						<goals>
							<goal>deploy-file</goal>
						</goals>
						<configuration>
							<repositoryId>nexus-snapshots</repositoryId>
							<url>http://localhost:8081/repository/maven-snapshots/</url>
							<packaging>jar</packaging>
							<artifactId>${project.artifactId}</artifactId>
							<groupId>${project.groupId}</groupId>
							<version>${project.version}</version>
							<file>${project.build.directory}/${project.artifactId}-${project.version}.jar</file>
							<generatePom>false</generatePom>
							<pomFile>${basedir}/pom.xml</pomFile>
						</configuration>
					</plugin>
				</plugins>
			</build>
		</profile>
		<profile>
			<id>prd</id>
			<build>
				<plugins>
					<plugin>
						<groupId>org.apache.maven.plugins</groupId>
						<artifactId>maven-deploy-plugin</artifactId>
						<version>2.8.2</version>
						<goals>
							<goal>deploy-file</goal>
						</goals>
						<configuration>
							<repositoryId>nexus-releases</repositoryId>
							<url>http://localhost:8081/repository/maven-releases/</url>
							<packaging>jar</packaging>
							<artifactId>${project.artifactId}</artifactId>
							<groupId>${project.groupId}</groupId>
							<version>${project.version}</version>
							<file>${project.build.directory}/${project.artifactId}-${project.version}.jar</file>
							<generatePom>false</generatePom>
							<pomFile>${basedir}/pom.xml</pomFile>
						</configuration>
					</plugin>
				</plugins>
			</build>
		</profile>
	</profiles>

</project>
{% endcodeblock %}

## 部署
``` bash
mvn clean package deploy:deploy-file -P dev
```

成功部署
``` bash
[INFO] --- maven-deploy-plugin:2.8.2:deploy-file (default-cli) @ hello-mvn ---
Downloading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/maven-metadata.xml
Uploading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/hello-mvn-1.0-20160630.035051-1.jar
Uploaded: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/hello-mvn-1.0-20160630.035051-1.jar (4 KB at 16.2 KB/sec)
Uploading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/hello-mvn-1.0-20160630.035051-1.pom
Uploaded: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/hello-mvn-1.0-20160630.035051-1.pom (4 KB at 49.3 KB/sec)
Downloading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/maven-metadata.xml
Uploading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/maven-metadata.xml
Uploaded: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/1.0-SNAPSHOT/maven-metadata.xml (762 B at 10.9 KB/sec)
Uploading: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/maven-metadata.xml
Uploaded: http://localhost:8081/repository/maven-snapshots/hello-mvn/hello-mvn/maven-metadata.xml (276 B at 4.6 KB/sec)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 4.383 s
[INFO] Finished at: 2016-06-30T11:50:51+08:00
[INFO] Final Memory: 20M/170M
[INFO] ------------------------------------------------------------------------
```