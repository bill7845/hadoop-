
## 하둡 설치

<br><br>

#### VirtualBox 설치하기


<br><br>

* virtualBox older builder 다운

![1](https://user-images.githubusercontent.com/35517797/62436033-48b10f80-b779-11e9-8100-5f6d716070cf.PNG)

<br>

<hr/>

<br><br>

* winodw host 설치

![2 windowhost 설치](https://user-images.githubusercontent.com/35517797/62436696-71d29f80-b77b-11e9-964a-f01809fc2f6a.PNG)

<br>

<hr/>

<br><br>

* 2.2.2 버전 다운

![2 2 2 다운](https://user-images.githubusercontent.com/35517797/62436700-74cd9000-b77b-11e9-9122-6d73899cb71f.PNG)

<br>

<hr/>

<br><br>

* 설치 과정 전부 next

![3 전부다 next](https://user-images.githubusercontent.com/35517797/62436711-7c8d3480-b77b-11e9-9969-8692fec11f08.PNG)

<br>

<hr/>

<br><br>

* 새 버전 설치하라고 뜰 경우 닫기 

![4 새버전설치뜨면 x](https://user-images.githubusercontent.com/35517797/62436712-7c8d3480-b77b-11e9-9cf6-8a7bf09f5e2c.PNG)

<br>

<hr/>

<br><br>

* 설치 완료 화면

![5 설치완료](https://user-images.githubusercontent.com/35517797/62436713-7c8d3480-b77b-11e9-8f9b-b785876395f5.PNG)

<br>

<hr/>

<br><br> 

* 가상머신 여러개 설치 수월하게 하기 위한 베이그란트 설치

![6 가상머신설치 쉽게하기위한 베이그란트 설치](https://user-images.githubusercontent.com/35517797/62436714-7c8d3480-b77b-11e9-99b3-71e3db585f8f.PNG)

<br>

<hr/>

<br><br>

* down old version

![7 download oldversion](https://user-images.githubusercontent.com/35517797/62436715-7d25cb00-b77b-11e9-9f4d-2449ead8048f.PNG)

<br>

<hr/>

<br><br>

* version

![8](https://user-images.githubusercontent.com/35517797/62436716-7d25cb00-b77b-11e9-8c0b-451a482b8449.PNG)

<br>

<hr/>

<br><br>

* 재시작하기 

![9 재시작하기](https://user-images.githubusercontent.com/35517797/62436717-7d25cb00-b77b-11e9-962b-359abf77f20e.PNG)

<br>

<hr/>

<br><br>

* 설치 완료 화면

![10 설치완료](https://user-images.githubusercontent.com/35517797/62436718-7dbe6180-b77b-11e9-9f51-707d4366d7fd.PNG)

<br>

<hr/>

<br><br>

* 관리자 모드로 cmd 열기

![11 관리자모드로cmd](https://user-images.githubusercontent.com/35517797/62436719-7dbe6180-b77b-11e9-9b27-d2719ab5f499.PNG)

<br>

<hr/>

<br><br>

* 베이그란트 초기화 시키기

<b> vagrant init </b>

<br><br>

* 초기화 후 새로 생긴파일 노트패드로 열어서 내용 전부 지운 후 내용 복붙(*ref에 있음)

<br><br>

* 초기화 설정 후 변경한 내용으로 실행하기

![13 초기화설정 후 변경내용으로 실행](https://user-images.githubusercontent.com/35517797/62436721-7dbe6180-b77b-11e9-9d5d-c16655df07f3.PNG)

<br>

<hr/>

<br><br>

* virtualBox 관리자 권한 실행 시 3개 생겨있어야함

![14 virtualbox 관리자 권한으로 실행 후 3개가상머신 접속 확인](https://user-images.githubusercontent.com/35517797/62436723-7e56f800-b77b-11e9-9c75-a968a17578be.PNG)

<br>

<hr/>

<br><br>

#### putty 설치 (서버접속 도구?)

![15 putty 설치](https://user-images.githubusercontent.com/35517797/62436724-7e56f800-b77b-11e9-9669-ab71b02cb066.PNG)

<br>

<hr/>

<br><br>

* putty 실행 후 가상 머신별 ip 설정 후 save

![16 putty 실행 후 설정 가상 머신별 ip 설정 후 save](https://user-images.githubusercontent.com/35517797/62436725-7e56f800-b77b-11e9-8307-49fc00371356.PNG)

<br>

<hr/>

<br><br>

* vi editor로 각각(nn01,dn01,dn02)의 config 열어서 수정해주기 (* 수정후 적용 필수)

![17 nn01에서 vi 에디터로 설정파일 열기](https://user-images.githubusercontent.com/35517797/62438039-9f6e1780-b780-11e9-9b0c-c8bc6f265af7.PNG)

<br>

<hr/>

<b> [root@nn01 ~]vi /etc/ssh/sshd_config </b>
<b> 65 line의 PasswordAuthentication no를 PasswordAuthentication yes로 변경한다. </b>
<b> [root@nn01 ~]systemctl restart sshd 명령으로 적용 후 putty로 가서 실행 시켜보기 (root,vagrant id/pass/로 접속되야함) </b> 

<br>

<hr/>

<br><br>

#### MobaXterm 설치하기

<br><br>

* movaXterm 실행 후 nn01,dn01,dn02 open 

![22 movaxterm 실행 후 nn01,dn01,dn02 open](https://user-images.githubusercontent.com/35517797/62438037-9f6e1780-b780-11e9-93e8-5eb86c586762.PNG)

<br>

<hr/>

<br><br> 

* 3개 다 접속하기

![23 3개 다 접속하기](https://user-images.githubusercontent.com/35517797/62438038-9f6e1780-b780-11e9-8aad-34cd81e1125a.PNG)

<br>

<hr/>

<br>

<hr/>

<br><br>

* multiExec로 다중제어해보기

![24 멀티제어하기](https://user-images.githubusercontent.com/35517797/62438256-92055d00-b781-11e9-8051-3e9d4ada945e.PNG)

<br>

<hr/>

<br><br>

* 멀티제어로 동시에 여러 가상머신 업데이트 해보기

![25 멀티제어로 한번에 업데이트해보기](https://user-images.githubusercontent.com/35517797/62438258-93cf2080-b781-11e9-8ad3-84e419fa028e.PNG)

<br>

<hr/>

<br><br>

<b> yum install telnet svn git nc ntp wget vim net-tools </b> multi로 설치하기 
* 우측 상단 multipaste로 붙여넣기 가능
* multiExec 사용 시 line 조정 해줘야함 (clear)

<br>

<hr/>

<br><br>

* 방화벽 해제하기

<b> systemctl stop firewalld </b>
<b> systemctl disable firewalld </b>

<br>

<hr/>

<br><br>

* 
  








