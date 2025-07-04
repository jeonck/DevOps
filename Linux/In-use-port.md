## 현재 서비스에 동작 중인 포트 확인 방법 (우분투)

우분투에서 현재 서비스에 동작 중인 포트를 확인하기 위해 사용할 수 있는 몇 가지 명령어가 있습니다. 아래에 주요 방법을 정리하였습니다.

### **1. netstat 명령어 사용하기**

`netstat` 명령어는 네트워크 연결 상태를 확인하는 데 유용합니다. 이 명령어를 사용하기 위해서는 `net-tools` 패키지가 설치되어 있어야 합니다. 설치가 되어 있지 않다면 다음 명령어로 설치할 수 있습니다.

```bash
sudo apt install net-tools
```

설치 후, 현재 서비스 중인 포트를 확인하려면 다음 명령어를 입력합니다.

```bash
sudo netstat -tnlp
```

- `-t`: TCP 포트만 표시
- `-n`: 숫자 형식으로 주소 및 포트 번호 표시
- `-l`: 리스닝 중인 소켓만 표시
- `-p`: 포트를 사용하는 프로세스의 이름 표시

#### **예제 출력**

```plaintext
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      32530/sshd: nucleus
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      20931/docker-proxy
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN      2860/docker-proxy
...
```

이 명령어를 실행하면 현재 리스닝 중인 포트와 해당 포트를 사용하는 프로세스 정보를 확인할 수 있습니다[1][4][6].

### **2. 특정 포트 확인하기**

특정 포트가 사용 중인지 확인하고 싶다면, `grep` 명령어를 사용하여 필터링할 수 있습니다. 예를 들어, 포트 8080이 사용 중인지 확인하려면 다음과 같이 입력합니다.

```bash
sudo netstat -tnlp | grep 8080
```

#### **예제 출력**

```plaintext
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      20931/docker-proxy
```

또는 포트 8082가 사용 중인지 확인하려면 다음과 같이 입력합니다.

```bash
sudo netstat -tnlp | grep 8082
```

이 명령어는 해당 포트를 사용하는 프로세스 정보를 출력합니다. 만약 포트가 사용 중이지 않다면 아무 출력도 나타나지 않습니다[2][5].

### **3. ss 명령어 사용하기**

`ss` 명령어는 `netstat`의 대안으로, 소켓 통계 정보를 확인하는 데 사용됩니다. 다음 명령어로 현재 리스닝 중인 포트를 확인할 수 있습니다.

```bash
sudo ss -tuln
```

- `-t`: TCP 소켓만 표시
- `-u`: UDP 소켓만 표시
- `-l`: 리스닝 중인 소켓만 표시
- `-n`: 숫자 형식으로 주소 및 포트 번호 표시

이 명령어를 통해서도 현재 열려 있는 포트를 확인할 수 있습니다[3][5].

이 명령어들을 통해 우분투에서 현재 서비스에 동작 중인 포트를 효과적으로 확인할 수 있습니다.
[1] https://cafe24.zendesk.com/hc/ko/articles/9801441063449-LINUX-netstat-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%83%81%EC%84%B8-%EC%84%A4%EB%AA%85
[2] https://bright-tech.tistory.com/28
[3] https://studyforus.tistory.com/244
[4] https://docs.rackspace.com/docs/checking-listening-ports-with-netstat
[5] https://yooloo.tistory.com/155
[6] https://m.blog.naver.com/jooeun0502/221949733876
[7] https://blog.naver.com/wtkduq23247/220675740321
[8] http://m.blog.naver.com/minki0127/220710139663
[9] https://m.blog.naver.com/7979market/222384336231
[10] https://solfany.github.io/network/netstat/
[11] https://blog.naver.com/baeckwind18/220318005277?viewType=pc
[12] https://xzio.tistory.com/m/821
[13] https://run-it.tistory.com/33
[14] https://blog.skills.kro.kr/9
[15] https://hbase.tistory.com/227
[16] https://www.hivelocity.net/kb/how-to-monitor-network-services-using-netstat-command/
[17] https://gbminnote.com/entry/Linux-command-netstat-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%82%AC%EC%9A%A9%EB%B2%95-%EB%B0%8F-%EC%98%88%EC%A0%9C
[18] https://leeyujin.tistory.com/50
[19] https://slow-and-steady-wins-the-race.tistory.com/50
[20] https://rondeveloper.tistory.com/63
[21] https://kingofbackend.tistory.com/216
[22] https://help.duo.com/s/article/7440
[23] https://seokhyun2.tistory.com/73
[24] https://blog.naver.com/drods/222450215711
[25] https://yian.tistory.com/45
[26] https://byounghee.tistory.com/191
[27] https://private-space.tistory.com/121
[28] https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D-%EA%B3%BC-grep-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%B3%B5%ED%95%98%EA%B8%B0-%ED%8C%A8%ED%84%B4-%EA%B2%80%EC%83%89-%ED%99%95%EC%9E%A5%EB%B8%8C%EB%9E%98%ED%82%B7
[29] https://seculog.tistory.com/52
[30] https://unix.stackexchange.com/questions/62247/how-do-i-know-what-service-is-running-on-a-particular-port-in-linux
[31] https://superuser.com/questions/602049/how-to-use-netstat-on-a-specific-port-in-linux
[32] https://stackoverflow.com/questions/12010631/command-line-for-looking-at-specific-port
[33] https://stackoverflow.com/questions/10628972/how-to-grep-listening-on-port-80-that-can-also-filter-other-port-contain-80-such
[34] https://askubuntu.com/questions/573631/how-to-find-the-running-network-services-and-the-port-and-user
[35] https://www.tecmint.com/find-out-which-process-listening-on-a-particular-port/
[36] https://serverfault.com/questions/1078483/how-to-find-out-what-service-is-listening-on-a-specific-port-of-a-ubuntu-server
[37] https://velog.io/@s2ilver8/%EC%82%AC%EC%9A%A9%EC%A4%91%EC%9D%B8-%ED%8F%AC%ED%8A%B8-%ED%99%95%EC%9D%B8-%EB%B0%8F-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95
[38] https://velog.io/@yellowbutter0327/%EC%9C%88%EB%8F%84%EC%9A%B0-%EC%82%AC%EC%9A%A9%EC%A4%91%EC%9D%B8-%ED%8F%AC%ED%8A%B8-%ED%99%95%EC%9D%B8-%EB%B0%8F-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B8%B0
[39] https://surfshark.com/ko/blog/what-is-my-port?srsltid=AfmBOoqYthn3t8mB1pV0FM6wr9cKrtZMGJicdpC0Ucg1_BPBGo45KS5t
[40] https://kb.synology.com/ko-kr/DSM/tutorial/Whether_TCP_port_is_open_or_closed
