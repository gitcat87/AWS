# AWS EC2를 이용하여 웹 서버 구축하기

## 인스턴스 시작하기

![](https://github.com/gitcat87/AWS/blob/main/images/capture1.png)

#

먼저 인스턴스를 시작하며 기본 설정을 잡습니다. 사용할 베이스 서버는 Ubuntu Linux

<br>
<br>

## 보안 규칙 확인하기

![](https://github.com/gitcat87/AWS/blob/main/images/capture2.png)

#

데이터 통신이 원활하도록 인바운드/아웃바운드 설정이 잘 되었는지 확인합니다.

<br>
<br>

## 인스턴스 IPv4 주소 확인

![](https://github.com/gitcat87/AWS/blob/main/images/capture3.png)

#

현재 인스턴스 서버의 ip주소를 확인합니다.

<br>
<br>

## Xshell 클라이언트로 생성한 인스턴스에 접속하기

![](https://github.com/gitcat87/AWS/blob/main/images/capture4.png)
![](https://github.com/gitcat87/AWS/blob/main/images/capture5.png)

#

Xshell 클라이언트로 새 연결을 만들면서 생성할 때 설정한 호스트 정보와 공개키 값을 입력해줍니다.

<br>
<br>

## 접속 확인

![](https://github.com/gitcat87/AWS/blob/main/images/capture6.png)

#

입력한 내용을 바탕으로 '연결' 시도를 합니다. 정상적으로 연결이 되는 것을 확인 할 수 있습니다.


<br>
<br>

## Docker를 이용하여 VPC에 Oracle DB 컨테이너 생성하기

![](https://github.com/gitcat87/AWS/blob/main/images/capture7.png)

![](https://github.com/gitcat87/AWS/blob/main/images/capture8.png)

```linux
# 리눅스
sudo docker run -d --name myoracle -p 1521:1521 wnameless/oracle-xe-11g-r2:latest
0329541ffc7ef0c70a20c5ffe0f110b39fc40ada4d9a40d0fd9b37a2e4bf4e92
ubuntu@ip-172-31-43-232:~$ sudo docker ps
CONTAINER ID   IMAGE                               COMMAND                  CREATED         STATUS         PORTS                                                         NAMES
0329541ffc7e   wnameless/oracle-xe-11g-r2:latest   "/bin/sh -c '/usr/sb…"   8 seconds ago   Up 7 seconds   22/tcp, 8080/tcp, 0.0.0.0:1521->1521/tcp, :::1521->1521/tcp   myoracle

```

#
(현재는 VPC에 Docker를 미리 설치한 상태입니다.)
oracle DB 이미지를 다운로드 함과 동시에 백그라운드에서도 실행되도록 -d 명령어를 추가해 컨테이너를 생성합니다.

<br>
<br>

## DB접속 확인

![](https://github.com/gitcat87/AWS/blob/main/images/capture9.png)

#

작성한 프로그램에서 DB에 잘 접속 되는지 확인해줍니다.

<br>
<br>

## 데이터 넣고 확인하기

![](https://github.com/gitcat87/AWS/blob/main/images/capture10.png)
![](https://github.com/gitcat87/AWS/blob/main/images/capture11.png)
![](https://github.com/gitcat87/AWS/blob/main/images/capture12.png)

#

DB연결이 정상적이므로 데이터 통신도 원활하게 이루어지는지 확인을 합니다.
작성한 프로그램과 SQL Developer 내에서도 정상적으로 조회가 되는 것을 알 수 있습니다.
