---
published: false
comments: true
category: docker
tags: docker dns bind
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
* Docker 이미지를 실행합니다.
	* HostIP '192.168.0.200'를 기준으로 작성하였습니다. 이 부분을 각자 환경에 맞게 수정하셔야 합니다.
	* Password는 Docker 설치후에 웹으로 로그인하여 변경합니다.
	```
    docker run -d --name=bind --dns=127.0.0.1 --publish=192.168.0.200:53:53 --publish=192.168.0.200:10000:10000 --volume=/srv/docker/bind:/data --env='ROOT_PASSWORD=SecretPassword' sameersbn/bind:latest
    ```

### Webmin에 로그인
* 다음 주소로 Webmin에 로그인 합니다.(인증서가 없으므로 예외 설정을 추가합니다.)
** [https://192.168.0.200:10000/](https://192.168.0.200:10000/)
** ![bind_001.png]({{site.baseurl}}/_posts/bind_001.png)
** 로그인 후 화면 초기화까지 약 2분정도 소요됩니다.
* root 계정의 Password와 언어 설정을 변경하고 저장 후 F5(새로고침)을 실행합니다.
** ![bind_002.png]({{site.baseurl}}/_posts/bind_002.png)

### BIND DNS 서버 설정
* 전달 및 전송에 외부 DNS 서버 주소 추가
** ![bind_003.png]({{site.baseurl}}/_posts/bind_003.png)
** ![bind_004.png]({{site.baseurl}}/_posts/bind_004.png)

### 역방향 영역 추가(IP -> Domain name)
* 새 마스터 영역 작성
** ![bind_005.png]({{site.baseurl}}/_posts/bind_005.png)
* 역방향 영역 추가(도메인 이름 부분에 IP 마지막 부분을 제거하고 입력한다.)
** ![bind_006.png]({{site.baseurl}}/_posts/bind_006.png)

## 정방향 영역 추가(Domain name -> IP)
* 새 마스터 영역 작성
** ![bind_007.png]({{site.baseurl}}/_posts/bind_007.png)
* 정방향 영역 추가
** ![bind_008.png]({{site.baseurl}}/_posts/bind_008.png)
* ns.rossheo.local 추가
** ![bind_009.png]({{site.baseurl}}/_posts/bind_009.png)
** ![bind_010.png]({{site.baseurl}}/_posts/bind_010.png)
* 추가된 주소 적용하기
** ![bind_011.png]({{site.baseurl}}/_posts/bind_011.png)

## 네트워크 어댑터에 DNS 주소 설정 및 DNS 접미사 추가
* 네트워크 어댑터 설정
** ![bind_012.png]({{site.baseurl}}/_posts/bind_012.png)
* nslookup으로 dns 확인하기
** ![bind_013.png]({{site.baseurl}}/_posts/bind_013.png)





### 참조
* http://www.damagehead.com/blog/2015/04/28/deploying-a-dns-server-using-docker/
* http://html5around.com/wordpress/tutorials/ubuntu-bind9-local-dns-setup/