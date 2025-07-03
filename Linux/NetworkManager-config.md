우분투에서 **GUI(NetworkManager)**로 네트워크를 설정할 경우, 실제 설정 정보는 **/etc/NetworkManager/system-connections/** 디렉토리에 저장됩니다[1][2]. 이 폴더에는 네트워크 연결별로 하나씩 파일이 생성되며, 각 파일은 일반 텍스트 형식의 INI 스타일로 구성되어 있습니다. 이 파일들은 관리자(root) 권한이 있어야 읽거나 수정할 수 있습니다[1].

### 관리 파일 위치

- **/etc/NetworkManager/system-connections/**  
  (예: `/etc/NetworkManager/system-connections/Wired connection 1.nmconnection`)

### 샘플 파일 예시

아래는 유선 네트워크(Wired) 연결에서 **수동(Static) IP**로 설정된 예시입니다.

```ini
[connection]
id=Wired connection 1
uuid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
type=ethernet
autoconnect=true

[ethernet]
mac-address-blacklist=

[ipv4]
method=manual
addresses=192.168.10.5/24;  # IP 주소/서브넷
gateway=192.168.10.1        # 게이트웨이
dns=8.8.8.8;8.8.4.4;        # DNS 서버
dns-search=
may-fail=false

[ipv6]
method=auto
```

- **id**: 연결 이름 (GUI에서 지정한 이름)
- **uuid**: 연결의 고유 식별자
- **type**: 네트워크 유형(ethernet, wifi 등)
- **method**: 수동(manual) 또는 자동(DHCP)
- **addresses**: IP 주소와 서브넷 마스크
- **gateway**: 기본 게이트웨이
- **dns**: DNS 서버 목록(세미콜론으로 구분)

### 참고 사항

- GUI에서 설정을 변경하면 이 파일이 자동으로 생성·수정됩니다[1][2].
- 파일을 직접 수정한 경우, 변경 사항을 적용하려면 다음 명령어로 NetworkManager를 재시작해야 합니다:
  ```
  sudo systemctl restart NetworkManager
  ```
- 대부분의 데스크탑 환경에서는 `/etc/network/interfaces` 또는 `/etc/netplan/`이 아닌, 위 경로의 파일이 실제 설정을 담당합니다[1][2][3].

**요약**:  
GUI(NetworkManager)로 네트워크를 설정하면, 실제 설정 파일은 `/etc/NetworkManager/system-connections/`에 저장되며, 각 연결별로 `.nmconnection` 파일이 생성됩니다. 이 파일을 직접 수정할 때는 root 권한이 필요하며, 수정 후에는 NetworkManager 재시작이 필요합니다.

출처
[1] Where is Ubuntu 20.04 default network configuration? https://askubuntu.com/questions/1397164/where-is-ubuntu-20-04-default-network-configuration
[2] How does Ubuntu Desktop read network configuration https://serverfault.com/questions/362244/how-does-ubuntu-desktop-read-network-configuration
[3] Configure Static IP on Ubuntu - Edun's blog https://jubriledun.hashnode.dev/how-to-configure-static-ip-on-ubuntu-from-the-terminal
[4] Configuring networks - Ubuntu Server documentation https://documentation.ubuntu.com/server/explanation/networking/configuring-networks/
[5] How to configure network settings on Ubuntu? https://www.tencentcloud.com/techpedia/103146
[6] Can I configure Ubuntu Desktop network using ip command? https://askubuntu.com/questions/1470026/can-i-configure-ubuntu-desktop-network-using-ip-command
[7] NetworkManager.conf - NetworkManager configuration file https://manpages.ubuntu.com/manpages/jammy/man5/NetworkManager.conf.5.html
[8] Configuring Network Interfaces on Ubuntu 20.04 - Reintech https://reintech.io/blog/configuring-network-interfaces-ubuntu-2004
[9] NetworkManager.conf - NetworkManager configuration file https://manpages.ubuntu.com/manpages/bionic/en/man5/NetworkManager.conf.5.html
[10] Configuring the network interface in Ubuntu 18.04 https://serverspace.io/support/help/configuring-the-network-interface-in-ubuntu-18-04/
