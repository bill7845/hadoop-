
## Jdk 설치

<br><br><br>

### protobuf 설치

<br><br>

* 설치전 필요 툴 설치 ( 3개 가상머신에서 ,root 계정)

<b> => yum install -y autoconf automake libtool curl gcc-c++ unzip </b>

<br>

<hr/>

<br><br>

* tmp 폴더(다운받은 파일 넣을것)에 wget 다운로드

![1 wget 다운](https://user-images.githubusercontent.com/35517797/62442077-a4879280-b791-11e9-9bdc-f7c9f525d213.PNG)

<br>

</hr>

<br><br>

* 압축풀기

![2 다운 후 압축풀기](https://user-images.githubusercontent.com/35517797/62442080-a5b8bf80-b791-11e9-817a-9fcebc0cc8c0.PNG)

<br>

</hr>

<br><br>

* </b> mv protobuf-2.5.0  /opt/ </b> 로 파일 이동시키기

<br>

</hr>

<br><br>

<b> =>  cd /opt/protobuf 폴더이동 하기 </b>
<b> => ./configure </b>
<b> => make </b>
<b> => make install </b>
<b> =>  protoc --version 으로 확인하기 </b>
![3 완료화면](https://user-images.githubusercontent.com/35517797/62442322-8cfcd980-b792-11e9-80c2-472942529bdf.PNG)

<br>

</hr>

<br><br>

### jdk 설치

* * jdk,hadoop 등은 opt 폴더에 설치할것

<br><br>

* => cd /tmp
* => wget --no-check-certificate --no-cookies - --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz
* 이대로 붙여넣기
* Local에 이미 다운로드 한 경우 Winscp를 이용하여 업로드해도됨
* => ls jdk*
* => tar -xvzpf jdk-8u131-linux-x64.tar.gz    : 압축풀기 
* =>  mkdir -p /opt/jdk/1.8.0_131         :  디렉토리 생성
* =>  mv jdk1.8.0_131/* /opt/jdk/1.8.0_131/       :  파일 이동
* => ln -s /opt/jdk/1.8.0_131 /opt/jdk/current        :  심볼릭 링크
* => install java with alternatives (에러)        :  

<br>

</hr>

<br><br>

* => alternatives --install /usr/bin/java java /opt/jdk/1.8.0_131/bin/java 2
* => alternatives --config java 
* => Enter to keep the current selection[+], or type selection number:1  (1 입력해주기)
![4 1누르기](https://user-images.githubusercontent.com/35517797/62445317-ed901480-b79a-11e9-8a72-763a201fbb24.PNG)

<br>

</hr>

<br><br>

## hadoop 설치

<br><br><br>

* cd /tmp
* => wget http://apache.tt.co.kr/hadoop/common/hadoop-2.7.7/hadoop-2.7.7.tar.gz 다운하기















