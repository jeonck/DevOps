```
ping -c 4 google.com
PING google.com (142.250.206.206) 56(84) bytes of data.
64 bytes from kix07s07-in-f14.1e100.net (142.250.206.206): icmp_seq=2 ttl=115 time=70.7 ms
64 bytes from kix07s07-in-f14.1e100.net (142.250.206.206): icmp_seq=3 ttl=115 time=70.4 ms
64 bytes from kix07s07-in-f14.1e100.net (142.250.206.206): icmp_seq=4 ttl=115 time=69.1 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3034ms
rtt min/avg/max/mdev = 69.141/70.095/70.716/0.684 ms
``` 

위의 명령어는 `ping` 명령어를 사용하여 google.com에 4개의 패킷을 전송하고 응답을 확인하는 과정입니다. 결과는 다음과 같은 정보를 포함합니다:

- **전송된 패킷 수**: 4개
- **수신된 패킷 수**: 3개
- **패킷 손실률**: 25%
- **응답 시간**: 최소 69.141ms, 평균 70.095ms, 최대 70.716ms

이 결과는 네트워크 연결 상태를 확인하는 데 유용하며, 패킷 손실이 발생했음을 나타냅니다. 패킷 손실은 네트워크의 성능 문제를 나타낼 수 있으며, 추가적인 진단이 필요할 수 있습니다.
[1] https://www.reddit.com/r/Stadia/comments/bdrez2/survey_ping_googlecom/
[2] https://hostarmada.com/kb/ssh-and-linux/ssh-commands/the-ping-command/
[3] https://superuser.com/questions/1521036/ping-google-com-not-sending-any-response
[4] https://www.hostitsmart.com/manage/knowledgebase/420/how-to-ping-google
[5] https://support.google.com/meet/thread/291676469/high-packet-loss-to-google-com?hl=en
[6] https://community.cloudflare.com/t/ping-to-google-com-and-google-com-au-now-over-200ms/17165
[7] https://forums.xfinity.com/conversations/your-home-network/test-ping-googlecom-t-run-in-command-promp-has-too-high-max-ping-215-ms-about-to-lose-my-workfromhome-job/65123acb1f2d714c3a6f3547
[8] https://www.kentik.com/kentipedia/ping-command-in-network-troubleshooting-and-monitoring/
[9] https://piazza.com/class_profile/get_resource/hq81u04tkcj539/hr2htxzll25f3
[10] https://forum.netgate.com/topic/169559/unable-to-ping-google-com-but-successfully-ping-8-8-8-8
[11] https://www.reddit.com/r/networking/comments/5r1on7/question_about_pinging_googlecom/
[12] https://www.redhat.com/en/blog/ping-usage-basics
[13] https://askubuntu.com/questions/1300210/i-can-ping-google-com-but-nothing-else
[14] https://www.cloudns.net/blog/what-is-ping-how-to-use-ping/
[15] https://gist.github.com/mwlang/11400904
[16] https://www.hostinger.com/tutorials/linux-ping-command-with-examples
[17] https://www.reddit.com/r/linux4noobs/comments/qmkr0j/cant_fix_ping_googlecom_temporary_failure_in_name/
[18] https://discourse.pi-hole.net/t/ping-google-com-fails-nslookup-google-com-times-out-otherwise-fine/67396
[19] https://play.google.com/store/apps/details?id=com.lipinic.ping&hl=en_US
[20] https://cloud.google.com/blog/products/networking/using-netperf-and-ping-to-measure-network-latency
[21] https://unix.stackexchange.com/questions/435414/ping-google-com-by-using-ip-address
[22] https://pagertree.gitbook.io/blog/ping-command-network-connection-test
[23] https://support.n4l.co.nz/s/article/How-to-use-Ping
[24] https://www.freecodecamp.org/news/how-to-identify-basic-internet-problems-with-ping/
[25] https://service.alaska.edu/TDClient/36/Portal/KB/ArticleDet?ID=513
[26] https://discussion.fedoraproject.org/t/100-packet-loss-on-ping-but-computer-can-still-browse-the-internet/72981
[27] https://play.google.com/store/apps/details?id=ua.com.streamsoft.pingtools&hl=en_US
