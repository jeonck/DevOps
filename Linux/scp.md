## SCP 파일 전송 절차서

**목적**: 이 문서는 SCP(Secure Copy Protocol)를 사용하여 파일을 원격 서버로 전송하는 절차를 설명합니다.

### **사전 준비**

1. **SSH 클라이언트 설치**: SCP는 SSH 프로토콜을 기반으로 하므로, SSH 클라이언트가 설치되어 있어야 합니다. 대부분의 리눅스 배포판에는 기본적으로 설치되어 있습니다. Windows 사용자는 OpenSSH 클라이언트를 설치해야 합니다.

2. **원격 서버 접근 정보**: 원격 서버의 사용자 이름과 IP 주소 또는 도메인 이름을 준비합니다.

### **파일 전송 절차**

1. **터미널 열기**: 사용 중인 운영 체제에 따라 터미널(리눅스, macOS) 또는 PowerShell(Windows)을 엽니다.

2. **SCP 명령어 입력**: 다음 형식으로 SCP 명령어를 입력하여 파일을 전송합니다.

   ```bash
   scp [옵션] [전송할 파일 경로] [사용자 이름]@[서버 주소]:[대상 경로]
   ```

   예를 들어, 현재 디렉토리의 모든 파일을 `nucleus`라는 사용자로 `nucleus` 서버의 `~/workspace/nucleus-tools` 디렉토리로 전송하려면 다음과 같이 입력합니다.

   ```bash
   scp * nucleus@nucleus:~/workspace/nucleus-tools
   ```

3. **비밀번호 입력**: 명령어를 실행하면 비밀번호 입력을 요청받습니다. `nucleus` 사용자의 비밀번호를 입력합니다.

### **전송 결과 확인**

전송이 완료되면 각 파일의 전송 상태가 표시됩니다. 예를 들어:

```
config.json                                              100%  478    25.0KB/s   00:00
docker-compose.yml                                       100%  535    29.8KB/s   00:00
Dockerfile                                               100%  339    18.5KB/s   00:00
index.html                                               100%   24KB 712.4KB/s   00:00
README.md                                                100% 3885   223.1KB/s   00:00
server.py                                                100% 1753   102.5KB/s   00:00
start.bat                                                100%  798    44.0KB/s   00:00
start.sh                                                 100%  652    34.2KB/s   00:00
```

### **옵션 설명**

- `-r`: 디렉토리와 그 내용을 재귀적으로 복사합니다.
- `-p`: 파일의 수정 시간, 접근 시간 및 모드를 유지합니다.
- `-l [속도]`: 전송 속도를 제한합니다(예: `-l 800`은 800 KBit/s로 제한).

### **주의 사항**

- SCP는 파일 전송 중 보안을 유지하지만, 대량의 파일을 전송할 경우 SFTP를 고려하는 것이 좋습니다. SFTP는 더 많은 기능을 제공하며, 대량의 파일 전송에 더 적합합니다[2][4][6].

이 절차서를 통해 SCP를 사용하여 파일을 안전하게 전송할 수 있습니다.
[1] https://docs.omniverse.nvidia.com/nucleus/latest/enterprise/nucleus_tools.html
[2] https://kb.hosting.com/docs/transferring-files-using-scp-secure-copy
[3] https://help.rapidseedbox.com/en/articles/6942823-a-step-by-step-guide-to-transferring-files-with-scp-an-easy-to-follow-example
[4] https://www.progress.com/blogs/how-to-use-scp-to-transfer-files
[5] https://jhpce.jhu.edu/access/file-transfer/
[6] https://researchcomputing.princeton.edu/support/knowledge-base/data-transfer
[7] https://www.strongdm.com/blog/linux-scp-command
[8] https://www.wm.edu/offices/it/services/researchcomputing/using/filesandfilesystems/xfers/sftp/
[9] https://www.nccs.nasa.gov/nccs-users/instructional/adapt-instructional/adapt-file-transfer
