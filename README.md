# 윈도우 개발 환경 셋업

![setup-windows](setup-windows-512x256x2.png)

## 1. 윈도우 버전 확인

- Windows 10 버전 2004 이상(빌드 19041 이상)
- 이전 버전이라면 [수동 설치 페이지](https://learn.microsoft.com/ko-kr/windows/wsl/install-manual)참조

## 2. VSCode 설치

- 설치 링크: https://code.visualstudio.com/
- 익스텐션 설치(선택)
  - Ayu: 테마
  - Material Icon Theme: 아이콘 테마

## 3. git 설치

- 설치 링크: https://git-scm.com/downloads

## 4. Windows Terminal 설치

- 설치 링크: https://apps.microsoft.com/detail/9n0dx20hk701?hl=ko-kr&gl=KR

## 5. wsl 설치

- 설치 링크: https://learn.microsoft.com/ko-kr/windows/wsl/install

```shell
wsl --install
```

## 6. Ubuntu 설치

- 설치 링크: https://apps.microsoft.com/detail/9mttcl66cpxj?hl=ko-kr&gl=KR

- 설치 후 재시작
- 리눅스 유저 생성

- 설치 후 에러 발생 시
  - 윈도우즈 시작 메뉴 > 설정 > 앱 > 앱 및 기능 - 최하단까지 스크롤 > 프로그램 및 기능 > Windows 기능 켜기/끄기 > Linux용 Windows 하위 시스템 체크되어있는지 확인

## 7. Window Terminal 설정

- 시작
  - 기본 프로필: Ubuntu 20.04.06 LTS
  - 기본 터미널 응용 프로그램: Windows 터미널
- Ubuntu 20.04.06 LTS
  - 명령줄: C:\WINDOWS\system32\wsl.exe
  - 시작 디렉터리: C:\Users\${윈도우사용자이름}
- 왼쪽 하단 설정 아이콘 클릭
  - VSCode로 settings.json 열기
  - wsl 익스텐션 설치

## 8. zsh 설치

- 설치 링크: https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH#ubuntu-debian--derivatives-windows-10-wsl--native-linux-kernel-with-windows-10-build-1903

```shell
sudo apt install zsh
```

## 9. oh my zsh 설치

- 설치 링크: https://ohmyz.sh/#install

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 10. TerminalSplash에서 테마 선택

- 링크: https://terminalsplash.com/

- TerminalSplash에서 원하는 테마 코드 복사
- Windows Terminal `settings.json` 파일에 해당 코드

```json
{
  "profiles": {
    "defaults": {
      // 추가한 코드의 name 입력
      "colorScheme": "ayu"
    }
  },
  "schemes": [
    // TerminalSplash에서 복사한 코드 추가
    {
      "name": "ayu",
      "background": "#0F1419",
      "black": "#000000",
      "blue": "#36A3D9",
      "brightBlack": "#323232",
      "brightBlue": "#68D5FF",
      "brightCyan": "#C7FFFD",
      "brightGreen": "#EAFE84",
      "brightPurple": "#FFA3AA",
      "brightRed": "#FF6565",
      "brightWhite": "#FFFFFF",
      "brightYellow": "#FFF779",
      "cursorColor": "#FFFFFF",
      "cyan": "#95E6CB",
      "foreground": "#E6E1CF",
      "green": "#B8CC52",
      "purple": "#F07178",
      "red": "#FF3333",
      "selectionBackground": "#FFFFFF",
      "white": "#FFFFFF",
      "yellow": "#E7C547"
    }
  ]
}
```

## 11. NerdFont 설치

- 설치 링크: https://www.nerdfonts.com/font-downloads

- 어떤 폰트든 아래 4 종류는 설치 권장

  - regular
  - bold
  - italic
  - bold italic

- Windows Terminal에 폰트 적용
  - `settings.json` 파일 수정

```json
{
  "profiles": {
    "defaults": {
      // 설치한 폰트 추가
      "font": {
        "face": "JetBrainsMono Nerd Font Mono"
      }
    }
  }
}
```

- VSCode `settings.json` 코드 추가
  - VSCode에서 `ctrl + shift + p` 입력
  - `Preferences: Open User Settings (JSON)` 검색 후 엔터
  - `settings.json` 수정

```json
{
  "editor.fontFamily": "JetBrainsMono Nerd Font",
  "editor.fontLigatures": true,
  "terminal.integrated.fontFamily": "JetBrainsMono Nerd Font",
  "terminal.integrated.automationProfile.windows": "C:\\WINDOWS\\System32\\wsl.exe"
}
```

## 12. powerlevel10k 설치

- 설치 링크: https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#oh-my-zsh

```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

- `.zshrc` 파일 수정
  - VSCode로 `.zshrc` 파일 열기

```shell
code ~/.zshrc
```

- `ZSH_THEME` 수정

```shell
ZSH_THEME="powerlevel10k/powerlevel10k"
```

- 터미널 열어서 powerlevel10k 설정 마법사 실행
  - 안내문 따라서 진행하면 됨.

## 13. 디렉터리 이름의 배경색 지우기()

- `.zshrc` 파일 수정
  - `.zshrc` 파일 열기

```shell
code ~/.zshrc
```

- 아래 코드 추가

```shell
LS_COLORS="di=01;36;48" && export LS_COLORS

# di: 디렉터리
# 01: 글꼴 스타일(01: 굵은 글꼴)
# 36: 폰트 색상(36: 현재 테마의 cyan색깔)
# 48: 배경 색상(48: 현재 테마의 background 색깔)

# 값은 자신의 테마에 따라 달라질 수 있음.
# 직접 값을 바꿔보며 설정하는 것을 권장.
```

## 14. NodeJS 설치

- nvm 설치할 경우 설치 생략: nvm으로 설치하지 않은 node 버전은 nvm에서 사용할 수 없기 때문.

- 설치 링크: https://github.com/nodesource/distributions

- Node.js v20.x 설치

```shell
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```

## 15. nvm 설치

- 설치 링크: https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

- 설치 후 터미널 재시작하고 `nvm` 입력

- nvm 명령어

```shell
nvm ls-remote # 사용 가능한 node 버전 표시
nvm install ${version} # 특정 버전 설치: 버전 입력시 맨 앞에 v 붙여야 함.
nvm use ${version} # 특정 버전 사용
nvm ls # 설치한 모든 node 버전 표시

node -v # 현재 사용 중인 node 버전 표시
```

## 16. VSCode WSL:Ubuntu-20.04에 익스텐션 설치

- 아래 익스텐션 설치

  - Prettier
  - ESLint

- File > Preferences > settings > Editor:Format On Save 활성화

## 17. Git and Github CLI 설치

- 명령어로 Git 설치 (위에서 따로 설치했다면 생략)

```shell
git --version # git의 설치 여부를 모르겠다면 해당 명령어 입력
sudo apt-get install git # git 설치 명령어
```

- Github CLI 설치

- 설치 링크: https://github.com/cli/cli/blob/trunk/docs/install_linux.md#debian-ubuntu-linux-raspberry-pi-os-apt

```shell
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

```shell
gh # 입력하여 설치 확인
```

- Git 설정

```shell
git config --global user.name "이름"
git config --global user.email "이메일"
```
