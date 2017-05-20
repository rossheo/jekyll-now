---
published: true
---
## GitExtensions IME Patch

- GitExtensions의 경우 다음과 같이 한글 IME가 깨지는 문제가 발생합니다.
 ![GitExtensions IME 문제]({{site.baseurl}}/assets/gitextensions_ime_problem.png)
 
- GitExtensions 프로젝트를 Fork하여 IME 패치가 필요한 코드를 수정하였습니다.
 - [GitExtensions IME 문제 패치](https://github.com/gitextensions/gitextensions/compare/master...rossheo:release/ime-patch)
 
- 위 코드를 수정하면 정상적으로 한글을 입력할 수 있습니다.
 ![GitExtensions IME 문제]({{site.baseurl}}/assets/gitextensions_ime_problem_fixed.png)
