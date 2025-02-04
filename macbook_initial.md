1. 시스템 기본 설정


macOS 업데이트: 최신 macOS로 업데이트하여 보안 및 성능을 최적화하세요. (2025년 현재, macOS Ventura 또는 그 이후 버전이 최신일 수 있습니다.)


Xcode Command Line Tools: 개발 필수 도구를 설치합니다.
xcode-select --install



2. 패키지 관리자 - Homebrew 설치


Homebrew는 macOS에서 필수적인 패키지 관리 도구입니다.
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"



Homebrew 환경 설정:
echo `eval "$(/opt/homebrew/bin/brew shellenv)"` >> /Users/사용자이름/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
export PATH="/opt/homebrew/bin:$PATH"



3. 기본 개발 도구 설치


필수 개발 도구 설치:
brew install git zsh curl wget
brew install tmux tree htop



iTerm2 설치:
brew install --cask iterm2



Zsh 자동 완성 활성화:
echo 'source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh' >> ~/.zshrc



Oh My Zsh 설치 및 플러그인 설정:
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
brew install zsh-autosuggestions zsh-syntax-highlighting



4. Python 개발 환경 세팅


Python 버전 관리 도구 (pyenv) 설치:
brew install pyenv



Python 3.12.4 설치 및 설정:
pyenv install 3.12.4
pyenv global 3.12.4



가상 환경 관리 도구 (virtualenv) 설치:
alias pip='pip3'
pip install virtualenv



5. Poetry 설치 (Python 프로젝트 관리 도구)


Poetry 설치:
brew install poetry



Poetry 환경변수 설정:
export PATH="/opt/homebrew/bin:$PATH"



Poetry 프로젝트 생성 예시:
poetry new my-fastapi-project
cd my-fastapi-project
poetry add fastapi uvicorn requests sqlalchemy



6. PyCharm 설치

PyCharm (Community/Professional) 설치:
brew install --cask pycharm



7. Streamlit 설치

Poetry를 사용해 Streamlit 설치:
poetry add streamlit streamlit-elements streamlit-folium streamlit-lottie



8. Docker 설치


Docker Desktop 설치:
brew install --cask docker



Docker 명령어 테스트:
docker --version
docker run hello-world



9. Kubernetes 관련 도구


kubectl 설치:
brew install kubectl



Minikube 설치 (로컬 Kubernetes 클러스터):
brew install minikube
minikube start
minikube status



Helm 설치 (Kubernetes 패키지 관리자):
brew install helm
helm repo add stable https://charts.helm.sh/stable
helm repo update



k9s 설치 (Kubernetes CLI 관리 도구):
brew install k9s



Lens 설치 (Kubernetes IDE):
brew install --cask lens



kubectx & kubens 설치:
brew install kubectx



Kind (Kubernetes in Docker) 설치:
brew install kind
kind create cluster



10. DevOps 도구 설치


Docker Registry 설치: Docker 이미지를 저장하고 관리하기 위한 레지스트리 설치.
brew install registry



Argo CD 설치: Kubernetes에서 GitOps를 위한 지속적 배포 도구.
brew install argocd



11. 버전 관리 및 협업 도구


Sourcetree 설치:
brew install --cask sourcetree



Git 설정:
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"



12. 데이터베이스 관리 도구


DataGrip 설치:
brew install --cask datagrip



PostgreSQL 설치:
brew install postgresql
brew services start postgresql



13. API 및 데이터 분석 도구

Postman 설치:
brew install --cask postman



14. Telegram 및 Slack 설치


Telegram 설치:
brew install --cask telegram



Slack 설치:
brew install --cask slack



15. 기타 유용한 도구


VS Code 설치:
brew install --cask visual-studio-code



Wireshark 설치:
brew install --cask wireshark



Rectangle 설치:
brew install --cask rectangle



이제 맥북이 FastAPI 개발, Streamlit 프로젝트, Poetry 의존성 관리, Kubernetes 운영, Docker 컨테이너 관리, DevOps 도구 사용, Telegram 및 Slack 커뮤니케이션 등 다양한 작업을 수행할 준비가 완료되었습니다! 🚀
