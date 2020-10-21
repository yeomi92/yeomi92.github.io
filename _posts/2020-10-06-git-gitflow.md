---
layout: post
title: "git flow"
subtitle: "git"
date: 2020-10-06 -0400
background: "/img/posts/06.jpg"
category: "git"
---

git으로 개발할 때 거의 표준과 같이 사용되는 방법론

기능이 아닌 방법론

5가지 브랜치

master: 기준이 되는 브랜치, 제품 배포 브랜치

develop: 개발 브랜치, 이 브랜치를 깆준으로 각자 작업한 기능을 merge한다.

feature: 단위 기능을 개발하는 브랜치, 완료되면 develop에 merge한다.

release: 배포를 위해 master브랜치로 보내기 전에 QA를 하기위한 브랜치

hotfix: master브랜치로 배포를 했는데 버그가 생겼을 때 긴급 수정하는 브랜치

규모가 있는 개발을 할 경우 브랜치보다는 Fork와 Pull request를 활용

Fork: 프로젝트를 통째로 외부로 복제해서 개발하는 방식

Fork를 해서 로컬에서 개발하고 Pull request로 원프로젝트 관리자에게 merge 요청

코드를 확인 후 관리자가 merge