---
title: "Gradle : 도메인 객체"
permalink: /gradle/object/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-18 00:00:00 -0000
last_modified_at: 2020-04-18 00:00:00 -0000
sidebar:
  title: "etc"
  nav: etc
---

* [강좌](https://www.youtube.com/watch?v=hbZJPhceVg4&list=PL7mmuO705dG2pdxCYCCJeAgOeuQN1seZz&index=13)

## Project 객체

* 프로젝트의 환경 구성, 의존관계, 태스크 등의 내용을 제어 및 참조
* build.gradle과 대응
* Project 객체의 생명주기
    * 빌드 수행을 위한 Settings 객체 생성
    * settings.gradle 스크립트 파일이 있을 경우 Settings 객체 비교
    * 구성된 Settings 객체를 이용하여 Project 객체 계층 구조 생성
    * 멀티 프로젝트일 경우 부모 프로젝트 부터 Project 객체 생성 후 자식 프로젝트의 Project 객체 생성

* Project Object
    * TaskContainer
    * DependencyHandler
    * ArtifactHandler
    * RepositoryHandler
    * Gradle
    * ConfigurationContainer

```groovy
defaultTasks = ['exeTask001', 'exeTask002']

gradle.allprojects{
    project->
        project.beforeEvaluate{
            println project.name + ' : check start'
        }
        project.afterEvaluate{
            println project.name + ' : check end'
        }
}

project.description = 'Project Object Description'
project.version = 'exeTask v1.0'
task exeTask001{
    doLast{
        println 'Project Name : ' + project.name
        println 'Project description : ' + project.description
        println 'Project group : ' + project.group
        println 'Project path : ' + project.path
        println 'Project projectDir : ' + project.projectDir
        println 'Project status : ' + project.status
        println 'Project state : ' + project.state
        println 'Project version : ' + project.version
    }
}

task exeTask002{
    doLast{
        println project.description
    }
}
```

![](/file/image/gradle-object-01.png)

```groovy

```

