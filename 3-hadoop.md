

## hadoop

### root 작업 내용은 virtualBox  hadoop계정 작업은 mobaXterm

<br><br>

* < 자바 및 Hadoop 환경 변수 추가 >

 ( 설정파일 수정할 때는 MultiExe 보다 하나씩 하는 것이 나을 수도 있다 )

  1. vi ~/.bash_profile
  
  <br>
  
  <hr/>
  
  2. 여기 복붙
  #### HADOOP 2.7.7 start ############
  PATH=$PATH:$HOME/bin
  export HADOOP_HOME=/opt/hadoop/current
  export PATH=$PATH:$HADOOP_HOME/bin
  export PATH=$PATH:$HADOOP_HOME/sbin
  #### HADOOP 2.7.7end############

  #### JAVA 1.8.0 start#############
  export JAVA_HOME=/opt/jdk/current
  export PATH=$PATH:$JAVA_HOME/bin
  #### JAVA 1.8.0 end##############
  
  <br>
  
  <hr/>
  
  3. 변경한 부분 적용하기
  source ~/.bash_profile
  
  <br>
  
  4. 적용되었는지 확인하기
  java -version
  hadoop version
  
  <br>
  
  * hadoop 계정 밑에 tmp 폴더 만들기
  mkdir tmp
  cd tmp
  
  <br>
  
  * java 파일 만들어보기
  vi Hello.java
  
  <br>
  
  * <b> hadoop로 로그인 한 후 실행
  * <b> 여기까지 과정 nn01,dn01,dn02 전부 다 적용( multi로하지말고 각각)
  
  <br><br>
=====================================================================================================================================
  
  * 비밀번호없이 각노드를 접속할 수 있도록 공개키 공유(SSH)
  
  1. vi /etc/hosts (root 권한으로 ) - localhost 꼭 지운다 ( 모든 노드 다 )   ## root 계정으로 들어가서 하기(3개 가상머신 전부다)
  
  <br>
  
  2. 이거 복붙 ( 원래 있던거 다 지우고)
     192.168.56.101 nn01
     192.168.56.102 dn01
     192.168.56.103 dn02
     
     ![host](https://user-images.githubusercontent.com/35517797/62506047-14e9ee80-b83a-11e9-8bba-b6946de77a93.PNG)

<br>

  3. ssh 키 생성하기
  
  * [hadoop@nn01 ~]$ ssh-keygen
  * [hadoop@dn01 ~]$ ssh-keygen
  * [hadoop@dn02 ~]$ ssh-keygen
  
  enter 3번치면 됨
  
  <br> 
  
  * multi 풀고 각각 작업
  
- nno01에서  
[hadoop@nn01 ~]$ ssh-copy-id hadoop@dn01
[hadoop@nn01 ~]$ ssh-copy-id hadoop@nn01
[hadoop@nn01 ~]$ ssh-copy-id hadoop@dn02
- dn01에서
[hadoop@dn01 ~]$ ssh-copy-id hadoop@dn01
[hadoop@dn01 ~]$ ssh-copy-id hadoop@nn01
[hadoop@dn01 ~]$ ssh-copy-id hadoop@dn02
- dn02에서
[hadoop@dn02 ~]$ ssh-copy-id hadoop@dn01
[hadoop@dn02 ~]$ ssh-copy-id hadoop@nn01
[hadoop@dn02 ~]$ ssh-copy-id hadoop@dn02

이렇게 하면 패스워드없이 이동가능해짐
****패스워드없이 이동이 가능하다.  ( 나올 때는 exit 또는 logout 으로 나온다 )
[hadoop@nn01 ~]$ ssh dn01
[hadoop@nn01 ~]$ ssh dn02

[hadoop@dn01 ~]$ ssh nn01
[hadoop@dn01 ~]$ ssh dn02

[hadoop@dn02 ~]$ ssh nn01
[hadoop@dn02 ~]$ ssh dn01

<br><br>

============================================================================================================================

#### 환경변수 설정하기

<br>

* 1. coresite.xml

=> vi /opt/hadoop/current/etc/hadoop/core-site.xml
=> <configuration> 태그안에 아래태그들 붙여넣기
<property>
<name>fs.defaultFS</name>
<value>hdfs://nn01:9000</value>
</property>

<br>

* 2. hdfs-site.xml
=> vi /opt/hadoop/current/etc/hadoop/hdfs-site.xml
=> <configuration> 태그안에 아래태그들 붙여넣기 * 이렇게 내용이 많을 경우 붙여넣기시 깨질위험 있으므로 잘 확인

<property>
<name>dfs.replication</name>
<value>1</value>
</property>
<property>
<name>dfs.namenode.http-address</name>
<value>nn01:50070</value>
</property>
<property>
<name>dfs.namenode.secondary.http-address</name>
<value>nn01:50090</value>
</property>
<property>
<name>dfs.namenode.name.dir</name>
<value>file:/home/hadoop/hadoop_data/hdfs/namenode</value>
</property>
<property>
<name>dfs.datanode.data.dir</name>
<value>file:/home/hadoop/hadoop_data/hdfs/datanode</value>
</property>
<property>
<name>dfs.namenode.checkpoint.dir</name>
<value>file:/home/hadoop/hadoop_data/hdfs/namesecondary</value>
</property>
<property>
<name>dfs.webhdfs.enabled</name>
<value>true</value>
</property>

<br>

* 3. yarn-site.xml
=> vi /opt/hadoop/current/etc/hadoop/yarn-site.xml
=> <configuration> 태그안에 아래태그들 붙여넣기

<property>
<name>yarn.nodemanager.aux-services</name>
<value>mapreduce_shuffle</value>
</property>
<property>
<name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
<value>org.apache.hadoop.mapred.ShuffleHandler</value>
</property>
<property>
<name>yarn.resourcemanager.scheduler.address</name>
<value>nn01:8030</value>
</property>
<property>
<name>yarn.resourcemanager.resource-tracker.address</name>
<value>nn01:8031</value>
</property>
<property>
<name>yarn.resourcemanager.address</name>

<br>

* 4. mapred-site.xml 템플릿 복사
=> cp /opt/hadoop/current/etc/hadoop/mapred-site.xml.template /opt/hadoop/current/etc/hadoop/mapred-site.xml

<br>

* 5. mapred-site.xml * 

=> vi /opt/hadoop/current/etc/hadoop/mapred-site.xml
=> <configuration> 태그안에 아래태그들 붙여넣기

<property>
<name>mapreduce.framework.name</name>
<value>yarn</value>
</property>
<property>
<name>mapreduce.jobtracker.hosts.exclude.filename</name>
<value>$HADOOP_HOME/etc/hadoop/exclude</value>
</property>
<property>
<name>mapreduce.jobtracker.hosts.filename</name>
<value>$HADOOP_HOME/etc/hadoop/include</value>
</property>

<br> 

* 6. masters        (*name node가 아니라 secondary node 지정임)

=> vi /opt/hadoop/current/etc/hadoop/masters
=> nn01 입력 후 저장

<br>

* 7. slaves

=> vi /opt/hadoop/current/etc/hadoop/slaves
dn01 <br>
dn02 <br>
입력 후 저장 (localhost 지우고)

<br>

* 8. hadoop-env.sh

=> vi /opt/hadoop/current/etc/hadoop/hadoop-env.sh 
=> export JAVA_HOME=/opt/jdk/current (25liine 수정)

<br>

* 9. yarn-env.sh

=> vi /opt/hadoop/current/etc/hadoop/yarn-env.sh
=> export JAVA_HOME=/opt/jdk/current  (22line 찾고 23라인 주석푼다음 이걸로 수정 )

<br>


* 10. dn01,dn02에도 설정해주기

=> [root@nn01 ~]# scp -r /opt/hadoop/* dn01:/opt/hadoop    ( root 계정에서 하기! // nn01의 설정을 dn01로 복사)
=> [root@nn01 ~]# scp -r /opt/hadoop/* dn02:/opt/hadoop    ( root 계정에서 하기! // nn01의 설정을 dn02로 복사)

<br>

=> 복사 후 dn01,dn02 계정 링크,소유자 설정해주기
[dn01(root 계정)] 심볼릭링크와 소유자를 다시 설정한다. 
a. [root@dn01 ~]# rm -rf /opt/hadoop/current
b. [root@dn01 ~]# ln -s /opt/hadoop/2.7.7 /opt/hadoop/current
c. [root@dn01 ~]# chown -R hadoop:hadoop /opt/hadoop/
[dn02(root 계정)] 심볼릭링크와 소유자를 다시 설정한다. 
a. [root@dn02 ~]# rm -rf /opt/hadoop/current
b. [root@dn02 ~]# ln -s /opt/hadoop/2.7.7 /opt/hadoop/current
c. [root@dn02 ~]# chown -R hadoop:hadoop /opt/hadoop/ <br>

=> 확인하기 : ll /opt/hadoop (엘엘임, hadoop 계정에서)

<br><br>

* 11. Hadoop namenode 디렉토리 생성 (nn01 : Namenode  // 멀티창 x)

=> mkdir -p ~/hadoop_data/hdfs/namenode
=> mkdir -p ~/hadoop_data/hdfs/namesecondary

<br>

Hadoop datanode 디렉토리 생성 (dn01 : Datanode)
=>  mkdir -p ~/hadoop_data/hdfs/datanode <br>
Hadoop datanode 디렉토리 생성 (dn02 : Datanode)
=>  mkdir -p ~/hadoop_data/hdfs/datanode

<br>

* 12. name node 포맷
=> hadoop namenode -format

<br>

* 13. Daemon 시작 (nn01)
=> start-all.sh

* 14. 정상확인
=> jps <br>

[hadoop@nn01 ~]$ jps  // 쳤을때 아래꺼 뜨면 성공
16624 ResourceManager
16883 Jps
16232 NameNode
16462 SecondaryNameNode
 
 
[hadoop@dn01 ~]$ jps  // 쳤을때 아래꺼 뜨면 성공
10518 DataNode
10650 NodeManager
10780 Jps
 
[hadoop@dn02 ~]$ jps  // 쳤을때 아래꺼 뜨면 성공
7041 DataNode
7141 NodeManager
7271 Jps

<br><br>










  

