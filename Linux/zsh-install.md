우분투에 **Oh My Zsh**를 설치하는 방법은 다음과 같습니다. 이 과정은 Zsh를 설치하고, 이를 기본 쉘로 설정한 후, Oh My Zsh를 설치하는 단계로 나뉩니다.

## **1. Zsh 설치**

먼저, Zsh를 설치해야 합니다. 터미널을 열고 다음 명령어를 입력하세요:

```bash
sudo apt update
sudo apt install zsh
```

설치가 완료되면, Zsh가 제대로 설치되었는지 확인합니다:

```bash
zsh --version
```

## **2. 기본 쉘 변경**

Zsh를 기본 쉘로 설정하려면 다음 명령어를 입력합니다:

```bash
chsh -s $(which zsh)
```

변경 사항을 적용하기 위해 로그아웃 후 다시 로그인하거나, 터미널을 재시작합니다. 기본 쉘이 Zsh로 변경되었는지 확인하려면 다음 명령어를 사용합니다:

```bash
echo $SHELL
```

출력 결과가 `/bin/zsh`로 나타나면 성공적으로 변경된 것입니다.

## **3. Oh My Zsh 설치**

이제 Oh My Zsh를 설치할 차례입니다. 설치는 `curl` 또는 `wget`을 사용하여 진행할 수 있습니다. 아래 명령어 중 하나를 선택하여 실행하세요:

```bash
# curl을 사용하는 경우
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# wget을 사용하는 경우
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

설치가 완료되면, Oh My Zsh의 기본 설정 파일인 `~/.zshrc`가 생성됩니다. 이 파일을 통해 다양한 설정을 조정할 수 있습니다.

## **4. 추가 설정 (선택 사항)**

Oh My Zsh는 다양한 플러그인과 테마를 지원합니다. 예를 들어, `zsh-syntax-highlighting` 및 `zsh-autosuggestions` 플러그인을 추가하고 싶다면 다음 명령어를 사용하여 설치할 수 있습니다:

```bash
# zsh-syntax-highlighting 설치
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# zsh-autosuggestions 설치
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

이후 `~/.zshrc` 파일을 열어 플러그인을 활성화합니다:

```bash
nano ~/.zshrc
```

`plugins=(...)` 부분에 추가한 플러그인을 포함시킵니다:

```bash
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```

변경 사항을 저장하고, 다음 명령어로 적용합니다:

```bash
source ~/.zshrc
```

이제 Oh My Zsh와 함께 Zsh를 사용할 준비가 완료되었습니다!
[1] https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH
[2] https://ohmyz.sh/
[3] https://caniro.tistory.com/225
[4] https://davelogs.tistory.com/129
[5] https://www.tecmint.com/install-oh-my-zsh-in-ubuntu/
[6] https://log4cat.tistory.com/7
[7] https://askubuntu.com/questions/1032567/install-zsh-in-ubuntu-18-04
[8] https://phoenixnap.com/kb/install-zsh-ubuntu
[9] https://bluevps.com/blog/how-to-install-oh-my-zsh-on-ubuntu-2204
[10] https://velog.io/@yuja/Oh-my-zsh%EA%B3%BC-%ED%85%8C%EB%A7%88powerlevel10k-%EB%B0%8F-%EB%B6%80%EA%B0%80%EA%B8%B0%EB%8A%A5-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0
[11] https://velog.io/@cosmos42/Ubuntu%EC%97%90-zsh-oh-my-zsh-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0
[12] https://crm06217.tistory.com/57
[13] https://medium.com/@satriajanaka09/setup-zsh-oh-my-zsh-powerlevel10k-on-ubuntu-20-04-c4a4052508fd
[14] https://www.reddit.com/r/Ubuntu/comments/sbmsnl/i_messed_up_my_terminal_by_installing_oh_my_zsh/
[15] https://gist.github.com/tsabat/1498393
[16] https://askubuntu.com/questions/521469/oh-my-zsh-for-the-root-and-for-all-user
