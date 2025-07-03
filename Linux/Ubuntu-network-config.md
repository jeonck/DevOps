우분투에서 네트워크 설정을 변경하는 방법은 **데스크탑**과 **서버** 환경, 그리고 **버전**에 따라 다릅니다. 아래에 대표적인 설정 방법을 정리합니다.

**1. 우분투 데스크탑 네트워크 설정**

- **GUI(그래픽 환경)에서 설정**
  - 화면 우측 상단 네트워크 아이콘(네모 3개 또는 Wi-Fi 아이콘)을 클릭하거나, 좌측 하단 "Show Applications"에서 "Network"를 검색해 실행합니다[5][2][4].
  - 유선(Wired) 또는 무선(Wi-Fi) 네트워크를 선택 후, "IPv4" 탭에서 "Manual"을 선택합니다.
  - IP Address, Netmask(Subnet), Gateway, DNS 정보를 입력하고 "Apply"를 클릭합니다.
  - 설정 적용을 위해 네트워크를 껐다 켜거나 재부팅합니다[5][2][4].

- **중요:** 데스크탑에서는 NetworkManager가 네트워크를 관리하므로, `/etc/network/interfaces`나 `/etc/resolv.conf`를 직접 수정해도 반영되지 않습니다[2][4].

**2. 우분투 서버 네트워크 설정**

- **18.04 이상 (netplan 사용)**
  - 우분투 18.04부터는 netplan을 통해 네트워크를 설정합니다[3][6].
  - 설정 파일 위치: `/etc/netplan/` 디렉토리 내의 `.yaml` 파일(예: `00-installer-config.yaml`)
  - 예시 설정(고정 IP):
    ```yaml
    network:
      version: 2
      renderer: networkd
      ethernets:
        eth0:
          addresses: [192.168.10.5/24]
          gateway4: 192.168.1.1
          nameservers:
            addresses: [1.1.1.1, 8.8.8.8]
    ```
  - 저장 후 적용:
    ```
    sudo netplan apply
    ```
  - 적용 후 `ip addr` 또는 `ifconfig`로 확인[6].

- **18.04 미만 (interfaces 파일 사용)**
  - 설정 파일 위치: `/etc/network/interfaces`
  - 예시 설정:
    ```
    auto eth0
    iface eth0 inet static
      address 192.168.0.20
      netmask 255.255.255.0
      gateway 192.168.0.1
      dns-nameservers 8.8.8.8 8.8.4.4
    ```
  - 저장 후 적용:
    ```
    sudo /etc/init.d/networking restart
    ```
  - DNS 설정은 `/etc/resolv.conf` 대신 `resolvconf` 유틸리티를 사용하는 것이 권장됨[2][4].

**3. 네트워크 인터페이스 이름 확인**

- 터미널에서 다음 명령어로 확인:
  ```
  ip addr
  ```
  또는
  ```
  ifconfig
  ```
  (ifconfig는 net-tools 패키지 설치 필요)[9][7].

**4. 기타 참고사항**

- **DNS 설정**: 최신 우분투는 `/etc/resolv.conf`를 직접 수정해도, 시스템이 자동으로 덮어쓸 수 있으므로, netplan 또는 interfaces 파일에서 DNS를 지정하거나, resolvconf를 통해 관리해야 합니다[2][4].
- **적용이 안 될 때**: 설정 파일의 들여쓰기, 인터페이스 이름(eth0, ens33 등)이 정확한지 반드시 확인하세요[6][3].

**정리**
- **데스크탑**: GUI에서 NetworkManager로 설정.
- **서버(18.04 이상)**: `/etc/netplan/*.yaml`에서 설정 후 `sudo netplan apply`.
- **서버(18.04 미만)**: `/etc/network/interfaces` 파일 수정 후 네트워크 재시작.

필요한 환경에 맞는 방법을 선택해 적용하시면 됩니다.

출처
[1] Ubuntu 네트워크 설정(22.04, 20.04, 18.04) - 쪼꼬의 이중생활 https://choco-life.tistory.com/39
[2] [Ubuntu] 우분투 네트워크 설정 (ubuntu 18.04) https://velog.io/@kio0207/Ubuntu-%EC%9A%B0%EB%B6%84%ED%88%AC-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%84%A4%EC%A0%95-ubuntu-18.04
[3] Ubuntu Server 20.04.3 LTS netplan, interfaces 고정 IP설정 https://feelsogoodcamp.tistory.com/35
[4] [Ubuntu] 우분투 네트워크 설정 - WEBDIR - 티스토리 https://webdir.tistory.com/188
[5] Ubuntu 인터넷 연결 / 우분투 네트워크 설정 - Justee - 티스토리 https://justee.tistory.com/2
[6] 우분투 고정 IP 설정 Ubuntu Server 22.04 - IT너구리 - 티스토리 https://it-racoon.tistory.com/3
[7] [UBUNTU] CLI 환경에서 네트워크 설정하는 법 - (주)다인엔시스 https://dain2013.tistory.com/55
[8] 리눅스 네트워크 설정(Debian 계열, Ubuntu) https://catnails.tistory.com/414
[9] [Linux]linux-ubuntu 20.04 실전 기본 명령어 -4(네트워크2) https://generalcoder.tistory.com/21
