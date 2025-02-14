Multipass란?

Multipass는 여러 운영 체제의 가상 머신을 손쉽게 설치, 관리 및 실행할 수 있도록 하는 경량 가상화 도구입니다. Canonical이 개발한 이 도구는 간단한 명령을 사용하여 데스크톱이나 서버에서 가상 머신을 만들고 실행하는 데 사용됩니다.

Multipass 설치법:

macOS:

Homebrew를 사용하여 설치할 수 있습니다.
bash

brew install --cask multipass
Windows:

공식 웹사이트에서 MSI 인스톨러를 다운로드하고 실행하여 설치합니다.
https://multipass.run/
Linux:

Snap을 사용하여 설치할 수 있습니다.
bash

sudo snap install multipass --classic
Multipass 사용법:

가상 머신 생성:

bash

multipass launch -n <가상머신이름> -c <CPU코어수> -m <메모리크기>
가상 머신 목록 확인:

bash

multipass list
가상 머신에 접속:

bash

multipass shell <가상머신이름>
가상 머신 삭제:

bash

multipass delete <가상머신이름>
파일 복사:

bash

multipass transfer <로컬파일> <가상머신이름>:
Multipass 활용:

개발 및 테스트 환경 구축: Multipass를 사용하면 로컬 머신에서 가상 머신을 실행하여 다양한 운영 체제와 환경에서 애플리케이션을 테스트할 수 있습니다.

클라우드 환경 시뮬레이션: 가상 머신을 사용하여 클라우드 환경을 시뮬레이션하고 개발 및 디버깅을 수행할 수 있습니다.

애플리케이션 배포 및 관리: Multipass를 사용하여 로컬에서 가상 머신을 생성하고 애플리케이션을 배포하고 관리할 수 있습니다.

컨테이너 개발 및 테스트: Multipass를 사용하여 다양한 운영 체제에서 컨테이너 개발 및 테스트 환경을 설정할 수 있습니다.

교육 및 교육용 환경: Multipass를 사용하여 학생들에게 가상 머신을 제공하여 프로그래밍 및 시스템 관리 등을 학습할 수 있습니다.

Multipass 명령어:

launch: 새로운 가상 머신을 생성합니다.
list: 현재 실행 중인 가상 머신 목록을 표시합니다.
shell: 가상 머신에 로그인하여 셸을 엽니다.
start: 중지된 가상 머신을 시작합니다.
stop: 실행 중인 가상 머신을 중지합니다.
delete: 가상 머신을 삭제합니다.
exec: 가상 머신에서 명령을 실행합니다.
transfer: 로컬 파일을 가상 머신으로 전송합니다.
위의 명령어들을 활용하여 Multipass를 사용하여 가상 머신을 쉽게 관리하고 다양한 작업을 수행할 수 있습니다.
