---
published: true
comments: true
category: linux
tags: ssh ubuntu terminal
---
## ubuntu에 SSH 터미널 설치하기

- 처음 ubuntu를 설치하고 ssh 터미널을 설치하기 위해 다음과 같이 진행합니다.
-- `sudo apt-get update`

- ssh 터미널 설치
-- ssh 설치 : `sudo apt-get -y install ssh`
-- 환경 설정 : `sudo vi /etc/ssh/sshd_config`

- ssh 설치시 같이 설치해야 하는 프로그램(fail2ban)
-- fail2ban 설치 : `sudo apt-get -y install fail2ban`
-- 환경 설정 : `sudo vi /etc/fail2ban/jail.conf`
