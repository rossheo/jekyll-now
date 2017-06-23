---
published: false
comments: true
category: keybinding
tags: vscode visualstudio code vim
title: VisualStudio Code Vim binding에 복사(CTRL+C) 붙여넣기(CTRL+V) 키 바인딩 추가하기
---
## VisualStudio Code에서 복사 붙여넣기 키 바인딩을 추가하는 방법

* 메뉴 이동
 * 파일 -> 기본 설정 -> 바로가기 키
![vscode_key_binding_01.png]({{site.baseurl}}/assets/vscode_key_binding_01.png)

 * keybinding.json 열기
 ![vscode_key_binding_02.png]({{site.baseurl}}/assets/vscode_key_binding_02.png)
 
 * 다음 설정 값 추가
 ![vscode_key_binding_03.png]({{site.baseurl}}/assets/vscode_key_binding_03.png)


```json
[
{ "key" : "ctrl+a", "command" : "editor.action.selectAll",
                       "when" : "editorTextFocus && !inDebugRepl" },
{ "key" : "ctrl+c", "command" : "editor.action.clipboardCopyAction",
                       "when" : "editorTextFocus && !inDebugRepl && vim.mode != 'Insert'" },
{ "key" : "ctrl+v", "command" : "editor.action.clipboardPasteAction",
                       "when" : "editorTextFocus && !inDebugRepl && vim.mode == 'Insert'" },
{ "key" : "ctrl+x", "command" : "editor.action.clipboardCutAction",
                       "when" : "editorTextFocus && !inDebugRepl" }
]
```