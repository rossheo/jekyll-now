---
published: true
title: GitExtensions 한글 IME 패치
comments: true
category: opensource
tags: git ime bugfix
---

- GitExtensions의 경우 다음과 같이 한글 IME가 깨지는 문제가 발생합니다.
 ![GitExtensions IME 문제]({{site.baseurl}}/assets/gitextensions_ime_problem.png)

- GitExtensions 프로젝트를 Fork하여 IME가 정상 동작하도록 코드를 수정하였습니다.
  - [GitExtensions IME 문제 패치](https://github.com/gitextensions/gitextensions/compare/release/2.49...rossheo:release/ime-patch)
 
- 위 코드를 수정하면 정상적으로 한글을 입력할 수 있습니다.
  ![GitExtensions IME 문제 수정]({{site.baseurl}}/assets/gitextensions_ime_problem_fixed.png)

- [2.49.03.GitUI.7z 다운로드](http://rossheo.com/downloads/2.49.03.GitUI.7z) 압축을 풀고,
  GitExtensions 설치 폴더에 GitUI.dll 파일을 덮어쓰기 합니다.
