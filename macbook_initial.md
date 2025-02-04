1. 시스템 기본 설정
1.1 macOS 업데이트
최신 macOS로 업데이트하여 보안 및 성능을 최적화하세요. (2025년 현재, macOS Ventura 또는 그 이후 버전이 최신일 수 있습니다.)

bash
# macOS 업데이트 확인 및 설치
softwareupdate -i -a
1.2 Xcode Command Line Tools 설치
개발에 필요한 필수 도구를 설치합니다.

bash
xcode-select --install
2. 패키지 관리자 - Homebrew 설치
Homebrew는 macOS에서 필수적인 패키지 관리 도구입니다.

bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Homebrew 환경 설정
bash
# Homebrew 환경 변수 추가
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/사용자이름/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
export PATH="/opt/homebrew/bin:$PATH"
3. 기본 개발 도구 설치
3.1 필수 개발 도구 설치
bash
brew install git zsh curl wget
brew install tmux tree htop
3.2 iTerm2 설치
bash
brew install --cask iterm2
3.3 Zsh 자동 완성 활성화
bash
echo 'source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh' >> ~/.zshrc
3.4 Oh My Zsh 설치 및 플러그인 설정
bash
# Oh My Zsh 설치
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 플러그인 설치
brew install zsh-autosuggestions zsh-syntax-highlighting
4. Python 개발 환경 세팅
4.1 Python 버전 관리 도구 (pyenv) 설치
bash
brew install pyenv
4.2 Python 3.12.4 설치 및 설정
bash
pyenv install 3.12.4
pyenv global 3.12.4
4.3 가상 환경 관리 도구 (virtualenv) 설치
bash
alias pip='pip3'
pip install virtualenv
5. Poetry 설치 (Python 프로젝트 관리 도구)
5.1 Poetry 설치
bash
brew install poetry
5.2 Poetry 환경변수 설정
bash
export PATH="/opt/homebrew/bin:$PATH"
5.3 Poetry 프로젝트 생성 예시
bash
poetry new my-fastapi-project
cd my-fastapi-project
poetry add fastapi uvicorn requests sqlalchemy
6. PyCharm 설치
PyCharm (Community/Professional) 설치:

bash
brew install --cask pycharm
7. Streamlit 설치
Poetry를 사용해 Streamlit 및 관련 패키지 설치:

bash
poetry add streamlit streamlit-elements streamlit-folium streamlit-lottie
8. Docker 설치
8.1 Docker Desktop 설치
bash
brew install --cask docker
8.2 Docker 명령어 테스트
bash
docker --version
docker run hello-world
9. Kubernetes 관련 도구
9.1 kubectl 설치
bash
brew install kubectl
9.2 Minikube 설치 (로컬 Kubernetes 클러스터)
bash
brew install minikube
minikube start
minikube status
9.3 Helm 설치 (Kubernetes 패키지 관리자)
bash
brew install helm
helm repo add stable https://charts.helm.sh/stable
helm repo update
9.4 k9s 설치 (Kubernetes CLI 관리 도구)
bash
brew install k9s
9.5 Lens 설치 (Kubernetes IDE)
bash
brew install --cask lens
9.6 kubectx & kubens 설치
bash
brew install kubectx
9.7 Kind (Kubernetes in Docker) 설치
bash
brew install kind
kind create cluster
10. DevOps 도구 설치
10.1 Docker Registry 설치
Docker 이미지를 저장하고 관리하기 위한 레지스트리 설치:

bash
brew install registry
10.2 Argo CD 설치
Kubernetes에서 GitOps를 위한 지속적 배포 도구:

bash
brew install argocd
11. 버전 관리 및 협업 도구
11.1 Sourcetree 설치
bash
brew install --cask sourcetree
11.2 Git 설정
bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
12. 데이터베이스 관리 도구
12.1 DataGrip 설치
bash
brew install --cask datagrip
12.2 PostgreSQL 설치 및 실행
bash
brew install postgresql
brew services start postgresql
13. API 및 데이터 분석 도구
13.1 Postman 설치
bash
brew install --cask postman
14. Telegram 및 Slack 설치
14.1 Telegram 설치
bash
brew install --cask telegram
14.2 Slack 설치
bash
brew install --cask slack
15. 기타 유용한 도구
15.1 VS Code 설치
bash
brew install --cask visual-studio-code
15.2 Wireshark 설치
bash
brew install --cask wireshark
15.3 Rectangle 설치
bash
brew install --cask rectangle
이제 맥북이 FastAPI 개발, Streamlit 프로젝트, Poetry 의존성 관리, Kubernetes 운영, Docker 컨테이너 관리, DevOps 도구 사용, Telegram 및 Slack 커뮤니케이션 등 다양한 작업을 수행할 준비가 완료되었습니다! 🚀

