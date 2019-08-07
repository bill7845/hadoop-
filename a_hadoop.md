
## hadoop 명령어

<br><br>

[참고] https://wikidocs.net/26496

명령어들을  dfs로 하나씩 확인해보자.
 
* 파일목록보기 : ls, lsr <br>
 ls : 지정한 디렉토리에 있는 파일의 정보를 출력 <br>
 lsr : 하위 디렉토리 정보까지 출력 <br>
 
 hdfs        dfs -ls <br>
 hdfs        dfs -lsr <br>

<br><br> 
 
* 파일내용보기 : cat, text <br>
 cat : 지정한 파일의 내용을 출력 <br>
 text : cat은 텍스트파일만 출력하는데 text는 zip 파일 형태로 압축한 파일도 텍스트형태로 출력 <br>
 
 hdfs        dfs -cat <br>
 hdfs        dfs -text <br>
 
<br><br>

* 디렉토리생성 : mkdir <br>

 hdfs        dfs -mkdir <br>
  
* 파일복사 <br>

  put / copyFromLocal  : 로컬 파일 시스템의 파일 및 디렉토리를 HDFS의 경로로 복사 <br>
 
  hdfs        dfs -put 로컬디렉토리/파일명 목적지디렉토리/파일명 <br>
  
  <br><br>
  
 * cp : HDFS에서 디텍토리나 파일 복사 <br>

  hdfs        dfs -cp [소스디렉토리|파일] [목적지디렉토리|파일] <br>


* 파일이동 <br>

 mv : 디렉토리나 파일을 목적지 경로로 이동 <br>
 
 hdfs        dfs -mv 로컬디렉토리/파일 목적지디렉토리/파일 <br>

* 삭제 <br>
 

[hadoop@nn01 ~]$ hdfs dfs -rm -r /output/airline1[hadoop@nn01 ~]$ hdfs dfs -rm -r /output/airline1  <br>

 
