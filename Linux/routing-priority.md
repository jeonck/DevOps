네트워크 인터페이스 `enp1s0`와 `enp2s0`가 있는 시스템에서 라우팅 우선 순위를 조정하는 예시를 설명드리겠습니다.

### 1. 현재 라우팅 테이블 확인

먼저, 현재 라우팅 테이블을 확인합니다.

```bash
route -n
```

또는

```bash
ip route show
```

### 2. 라우팅 우선 순위 조정

라우팅 우선 순위를 조정하려면, 각 인터페이스에 대해 기본 게이트웨이를 설정하고, 메트릭(metric) 값을 조정하여 우선 순위를 변경할 수 있습니다.

#### 예시: `enp1s0`를 기본 인터페이스로, `enp2s0`를 보조 인터페이스로 설정

1. **기본 게이트웨이 제거**

   기존 기본 게이트웨이를 제거합니다.

   ```bash
   sudo ip route del default
   ```

2. **새로운 기본 게이트웨이 설정**

   `enp1s0`를 기본 인터페이스로 설정합니다.

   ```bash
   sudo ip route add default via 172.20.40.1 dev enp1s0 metric 100
   ```

   여기서 `172.20.40.1`은 `enp1s0`의 네트워크에 있는 게이트웨이 IP입니다.

3. **보조 게이트웨이 설정**

   `enp2s0`를 보조 인터페이스로 설정합니다.

   ```bash
   sudo ip route add default via 192.168.122.1 dev enp2s0 metric 200
   ```

   여기서 `192.168.122.1`은 `enp2s0`의 네트워크에 있는 게이트웨이 IP입니다.

### 3. 라우팅 테이블 확인

변경된 라우팅 테이블을 다시 확인합니다.

```bash
ip route show
```

이제 `enp1s0`가 메트릭 값이 더 낮기 때문에 우선 순위가 더 높습니다. 만약 `enp1s0`가 다운되면, `enp2s0`가 자동으로 사용됩니다.

### 4. 영구적으로 설정하기

위 설정은 시스템 재부팅 시 초기화됩니다. 영구적으로 설정하려면, 네트워크 설정 파일(예: `/etc/network/interfaces` 또는 `/etc/sysconfig/network-scripts/ifcfg-enp1s0` 등)을 수정해야 합니다.

#### 예시: Debian/Ubuntu 계열

`/etc/network/interfaces` 파일에 다음과 같이 추가합니다.

```plaintext
auto enp1s0
iface enp1s0 inet static
    address 172.20.40.114
    netmask 255.255.255.0
    gateway 172.20.40.1
    metric 100

auto enp2s0
iface enp2s0 inet static
    address 192.168.122.131
    netmask 255.255.255.0
    gateway 192.168.122.1
    metric 200
```

#### 예시: CentOS/RHEL 계열

`/etc/sysconfig/network-scripts/ifcfg-enp1s0` 파일에 다음과 같이 추가합니다.

```plaintext
DEVICE=enp1s0
BOOTPROTO=static
IPADDR=172.20.40.114
NETMASK=255.255.255.0
GATEWAY=172.20.40.1
ONBOOT=yes
METRIC=100
```

`/etc/sysconfig/network-scripts/ifcfg-enp2s0` 파일에 다음과 같이 추가합니다.

```plaintext
DEVICE=enp2s0
BOOTPROTO=static
IPADDR=192.168.122.131
NETMASK=255.255.255.0
GATEWAY=192.168.122.1
ONBOOT=yes
METRIC=200
```

### 요약

- `enp1s0`를 기본 인터페이스로, `enp2s0`를 보조 인터페이스로 설정했습니다.
- `enp1s0`의 메트릭 값을 100, `enp2s0`의 메트릭 값을 200으로 설정하여 우선 순위를 조정했습니다.
- 영구적으로 설정하려면, 사용하는 리눅스 배포판에 맞는 네트워크 설정 파일을 수정해야 합니다.

이 방법을 통해 네트워크 인터페이스의 라우팅 우선 순위를 조정할 수 있습니다.
