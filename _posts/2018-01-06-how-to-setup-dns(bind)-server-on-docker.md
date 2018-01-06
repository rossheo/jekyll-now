---
published: false
---
## Docker로 DNS 서버 설치하기

### 도입하게 된 배경
* 내부 네트워크에 관리할 서버가 늘어날수록 IP주소를 외워서 관리하기 어려워집니다.
* DNS Server를 내부 네트워크용으로 설치하여 내부 IP와 도메인 이름을 연결하여 사용하면 편리합니다.
* Docker를 이용하여 짧은 시간에 내부 네트워크에서 사용할 수 있는 DNS 서버를 설치해봅시다.

### Docker 이미지 설치
* Docker에서 Bind 서비스를 사용할 수 있는 이미지중에서 Web 관리 툴이 포함되어 있는 이미지를 다운로드 받습니다.
	```
    docker pull sameersbn/bind:latest
    ```

### 참조
* http://www.damagehead.com/blog/2015/04/28/deploying-a-dns-server-using-docker/
* http://html5around.com/wordpress/tutorials/ubuntu-bind9-local-dns-setup/