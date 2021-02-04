<center>리눅스</center>

1991년에 Linus Torvalds 가 만듦.
유닉스는 워크스테이션 좀 무거움
가벼운 버전으로 만든 것

### linux Distro

\*\* Distro: 배포자 혹은 배포된 버전, 컴퓨터 소프트웨어의 패키지

- Debian: Debian, Ubuntu, KNOPPIX(CD Linux -> CD rom)
- RedHat: Fedora, RedHat Enterprise, CentOS, Vine Linux(Jp)
- Slackware: openSUSE(Novell), SUSE Enterprise

큰 회사들은 RedHat 계열 많이 사용.

### Kernel

하드웨어 위에 존재. infra와 가장 가까이 있음.
메모리, 파일 시스템, CPU, Device 등을 모두 관리함

### Linux shell

리눅스 커널을 컨트롤

- linux shell types
  - sh(Bourne shell): by unix shell, super shell
  - bash(Bourne-again shell): super shell in linux
  - csh(C shell): C like syntax
  - tcsh(Enhanced-C shell)
  - ksh(korn shell): powerful script language
  - zch(Z shell): unix/GNU shel script, powerful script language

### Linux File System Directories

- **/bin**: 기본 명령어
- /boot: for booting
- /dev: device file, cd-rom
- **/etc**: config, passwd, rc.d
- /home: user home dir
- **/lib**: shared library
- /media: ssd
- /opt: application software package
- **/proc**: process info
- /root: root home dir
- **/sbin**: 관리자용, ifconfig
- /srv: system data
- **/tmp**: temporary dir
- **/usr**: source or programs
- /usr/local
- **/var**: logs, ftp, spool, mail // 양이 많아지는 것들
- **/lost+found** // 사용이 안되는 파일들을 모아놓는 것. 휴지통 같은 개념
- +)**inode** // 트리 형태로 메모리에 올려 놓음

### Linux ports

- 20 **FTP (data)**
- 21 **FTP (control)**
- 22 **ssh**
- 23 **telnet**
- 25 **smtp**
- 465 smtps
- 43 whois
- 53 **dns**
- 80 **http**
- 443 **https**
- 110 **pop3**
- 995 pop3s
- 123 ntp // 네트워크 타임 프로토콜. 위성으로 시간을 다 맞춤. 항상 서버의 시간을 똑같이 맞춰줌.
- 143 imap2/4
- 993 imaps
- 514 SysLog

### Command Line Tips
- tab 키 사용
- Arrow up & down
- !% -> history 에서 %로 시작하는 가장 최근에 실행한 명령어 실행
- !! -> 가장 최근에 실행한 명령어 실행
- Ctrl + A : 커서를 맨 앞으로
- Ctrl + E : 커서를 맨 뒤로
- history : 최근에 실행한 명령 이력
- man <명령> : 명령에 대한 manual

root command
- adduser: 유저 추가
- passwd <account-name> : 비밀번호 변경
- deluser <account-name> : 유저 삭제

vi /etc/passwd에서 유저 목록 확인 가능

ps: 현재 프로세스 목록을 보여주는 명령어
ps -ef?

rmdir시 디렉터리가 비어있지 않아 삭제가 안된다면 

> rm -rf <directory_name>

su - <account_name>: 계정 전환

echo $HOME : HOME 환경변수를 print

**.bashrc 에 기본적으로 내가 써야 할 기능들, 여러 가지 등을 설정해 놓은 파일**

touch: 빈 파일 생성하기

apt-get install vim

apt라는 것이 서버에 있음 이 서버에 있는 vim 이라는 것을 install 하겠다.
apt-get update는 이 apt-get을 최신 버전으로 업데이트 시켜주는 명령어

**vi 에디터**

### 기본 명령어
- ls / touch / cat
- head / tail : 위쪽 10줄만 출력 / 아래 10줄만 출력
- pwd / which / clear / echo 
- cd 
- mkdir / rmdir
- cp / mv / rm
- find

> >는 새로 쓰기 
> >>는 append

$PATH 환경변수 안에 있는 경로들은 어디에서도 명령어를 실행할 수 있음

~: root 디렉토리
mv의 경우 inode가 내부적으로는 위치를 바꿈
find . <file_name>: 현재 디렉터리 아래에 있는 모든 폴더를 다 찾아봐라~
정석) find . -name <file_name>

cd -> - 옵션: 이전의 working directory로 이동

cp -af // file 복사 시 덮어쓰기

### 한글 적용 (캐릭터 인코딩)
- apt-get install locales

> locale
> locale -a
> cat /usr/share/i18n/SUPPORTED | grep k *ko로 시작하는 것이 한국어
> locale 치면 LANGUAGE에 적용된 언어셋이 나와있음
LC_ALL이 모든 것에 대한 언어를 나타냄
locale -a 
> localedef -f UTF-8 -i ko_KR ko_KR.UTF-8

### 기본 명령어 2
* df [m] // 옵션은 바이트 수 지정 가능
* du // disk used
* du -sk /home // sum 디스크 사용량 볼 수 있음
* free // 메모리 사용량 보여줌. 그 중 free는 남아있는 메모리 바이트 수
** swap: 메모리가 부족할 때 디스크를 사용하게 해줌. 메모리와 디스크 번갈아 가면서 사용 가능 
* top // CPU 사용량을 보여줌
* vmstat // 현재 상태 한 번에 보여줌 ex. vmstat 1하면 1초마다 상태 볼 수 있음. 모니터링할 때 유용
* ps // 
* ps -ef | grep bash ** grep은 필터 기능 bash의 ps만 볼 수 있음

가끔 '' 말고 "" 는 명령어로 인식될 수가 있음 ex. bash에서

echo '#!/bin/sh' >> tt.sh <- 외우기!
cat tt.sh // 화면에 파일 내용 출력
echo 'echo 123' >> tt.sh
cat tt.sh -> echo 123
sh tt.sh -> 123 // 최상위 쉘에서 파일명을 쉘로 실행시킨다.

* chmod // 실행 권한 변경
* chown // owner 변경 +) 디렉터리 변경 시 -r 옵션 사용

tt.sh를 ttt 폴더로 옮기고, 파일명을 aa.sh로 변경
> mv tt.sh ttt/aa.sh 

> mv tt.sh ttt/
> cd ttt
> mv tt.sh aa.sh

* ln // 윈도우의 바로가기 기능. symbolic link 걸기
ln -s 목적지(존재하는) 링크명

sudo // root가 실행하라는 뜻

### grep 명령어
* grep <찾을 단어> <file-name> [-io]
정규식과 비슷
^ 시작
$ 끝
[] 괄호 안에 들어가는 단어 들어가면 검색
-i ignore case