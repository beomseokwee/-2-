

2일차 jesus

timedatectl
우분투에서 제공하는 ntp서버를 다운시켜야 시간 변경 가능

3.
history
history -d 는 지우는것
!! 바로 전에거 실행
매칭되는 문자열 실행
!da 이런식

4. 자동 완성기능 = tap


5.  메뉴얼 페이지 man
man man  , space는 다음장 b는 전장 (1,5,8번은 숙지 해놓기)
ls에 대한 도움말을 알고 싶으면 man ls 이런식으로
command -o [FILE]
-- < 명령을 주는 방법?
커멘드 서브커멘드 패턴
git switch (옵션)
git branch (옵션)

6. man FDISK << 슈퍼유저로 들어가서 사용해야한다
#은 관리자를 나타냄
man ls
어떤건 관리자로 봐야하는게 있고 아닌게 있다
7. man 1 passwd << 일반 유저 가능
   man 5 passwd << 5번 관련 파일 설정 관련이라서 슈퍼유저로 봐야함
   
   man -f ls << f옵션은 간단히 보는 옵션
   whatis 라는 명령어는 man -f명령어랑 똑같다
   
8. 리눅스는 멀티유저 시스템이라서 어떤유저가 로그인 했는지 기록 확인을 해줘야한다
로그인환경 확인 ### 무조건 외우기.
logname  < 최초에 접속했던 id
whoami   < 현재?
id
개인정보 확인법
logout 이나 exit로 터미널을 빠져 나올 수 있다.
id는 나의 현재 신원 정보를 알려준다

9.  접속자에 대한 시스템을 알아보는법
users
who  < user에 대한 정보를 좀더 자세히 볼수 있다

ctrl alt F4

ctrl alt F1 = 원래환경
ctrl alt F2
who -b 언제 부팅했는지

10. 
w 
jcpu 는 장치 터미널에서 cpu 사용시간, pcpu = 프로그램이 사용되는데 필요한 시간

11. 달력
cal
cal 2022 
cal 4 2022
cal -y 해당 년도 모두 보기
cal -j?
clear = ctrl + l키

12. 시스템 정보보기
uname
uname -a
hostname
hostnamectl set-hostname 
arch 아키텍쳐 정보
env = 환경변수,windows랑 같다

환경 변수 세팅은 expert TEST
echo = 화면에다가 출력해주는 명령어
echo -e ??  <<escape 문자 역슬레쉬 명령어가 먹게 하기 위해선 -e를 실행 해야한다
-n 은 프롬포트가 붙는다

13. 어떤 명령어에 대해 위치를 알고 싶을때
which

14. 사용자에대한 정보 보고싶을때 finger
mesg y userid1  메세지off를 키고 싶을때

15. sleep 30

16.source 설정파일을 바로 적용 하고싶을때 사용
logout 필요 없이

리눅스 3일차 파일 및 디렉토리

리눅스는 보통 서버설정할때 다루기 때문에 gui 환경 보다는 터미널환경에서 사용된다.
 
i-node의 구성 google링 해보기
파생으로 해서 데이터 크기를 늘려서 데이터를 저장하는 방법?

index의 방법은 4kb밖에 되지않으나 포인터로 다른 데이터를 다시 가리키게 해서
4TB까지 저장할수 있게 한다?>?

## 실제파일을 i-node를 가지고 관리를 하고 있다.
실제 파일은 /dev라는 폴더에서 관리되고 있다.

ls -l 파일에대한 정보가 모두 나온다 d는 디렉토리
-로 시작하는게 일반 파일.
pwd 디렉토리의 위치를 알려주는것
ls = 리스트의 약자 , 파일과 디렉토리 정보를 알려주는것

1. 절대 경로 : 최상위 root부터 시작
cd 다음에 /를 치면 모두 절대경로

자기의 홈디렉토리를 무조건 써서 경로를 찾아 가야한다
유저라는 디렉토리를 갈때는 절대경로로 해서 간다??
usr = root 바로 밑에 있는것
cd /var

ㅡㅁ
2. 상대경로 : 내가 현재 위치한 디렉토리부터 시작하는것
cd 다음에 /를 치면 모두 상대경로


리눅스는 windows랑 다르게 c드라이브 d드라이브가 없고
root를 기준으로 해서 디렉토리가 존재한다
리눅스를 드라이브 추가할때는 root를 기준으로 하위디렉토리 서브디렉토리가 존재하는것

상대경로로 가게되면 cd../../usr
이런식으로 홈으로 올라간 다음에 usr로 가야함

cd명령어는 홈디렉토리로 가는것.
cd 다음ls 나온것들은 모두 서브 디렉토리라고 하는것

##userid1에 대한 홈디렉토리를 가는법
  cd ~userid1


cd ~를 쳐도 홈디렉토리로 간다.


cd - 이전에 작업하던 디렉토리로 가는것


3. ls -l   < 자세히 표시된다
etc는 root바로 밑에 있으니 절대경로로 들어가야한다
원래는 세로로 보여지지만 ls -x 가로로 보여진다
. 은 나의 디렉토리를 표시

ls -l -i 이런식으로 해도되나 ls-li도 가능
명령어에 나타난 애들은 i-node

stat test.txt 
ls -l test.txt 
실제적으로 i-node 테이블안에 들어가있다고 인식하기.

쉘이란?? 리눅스는 대쉬라는 쉘을 사용중이다


ls -i 는 아이노드를 알기위해 ,번호가 같으면 똑같은 파일을 의미한다?

필터링 해서 보고싶을때 와일드카드
? = 뒤에 어떤 한문자가 와있는것들이 온다
ls -id passwd* =안붙은 것들도 모두 표시 
범위 지정가능 ls -id net[p-w]*

ls -l net*
그밑에 하위디렉토리까지 모두 다 나타난다
ls -l -d net* d를 붙이면 하위까지 안나온다

ls-R 모든게 다 나타난다????
ls -lt = 시간순으로 나열 하고 싶을때
ls - ltr = 시간 역순으로 나열

stat = 아이노드 관련 자세히 보는법

--------
디렉토리 만드는 명령
mkdir  생성
rmdir   삭제
파일을 생성하는 명령어 = touch 
디렉토리 삭제시 디렉토리안에 파일이 존재하면 rmdir로 삭제가 바로 안된다
파일을 지는 명령어 = rm
디렉토리 안에 파일이 있어도 지우는법 =rmdir -r testdir
와일드카드로 rmdir testdir? 하면 뒤에 붙은것들 지워짐
rm -r testdir??
touch -t 옵션을 붙여서 시간 변경 까지 가능??
rm -rf ./ 이건 withall 같은 삭제 안되는 파일도 모드 지워지는것(현재 디렉토리 하위 디렉토리 다지워짐)
mkdir -p /work/space/zone 계층적 디렉토리 생성??


ls -l workspace
whatis  (su =  유저를 변경하는것

su - userid1 << pwd했을때 userid1 디렉토리로 간다
cp /etc/service . 서비스 파일 카피
cd -v /는 정보를 보여준다
파일 앞에 l이 붙으면 심볼링??
cp -b /etc/services .


##file 

cat 명령어
cat -n service
head는 10줄만 표시
head -숫자 파일
tail은 뒤쪽부터

## more
    less
    less -n 파일이름?
   
which랑 whereis랑 비슷하지만 whereis가 상세하게?
mv는 파일 이동

-r은 디렉토리를 카피하는 옵션 , 디렉토리를 카피할때는 -r을 붙여줘야한다
wc(wordcount 약자)
ls -a 숨겨져있는것 까지 모두다 
ls -R 하위디렉토리만 표현
ls -l 자세히 표현하는것

##find
find /etc -name<<찾고자 하는 파일 이름 = 기본적인 find의 틀
sudo find /etc -name < 슈퍼유저로 찾을때
find /etc -name -ls <<-l 옵션을 붙여준거와 같은 효과
find /-uid 1001 -print << userid1이 1001번으로 설정 되있거여서 모두 userid 있는걸 모두 찾아냄
find / -size +300000 <<30mb이상되는거만 찾겠다
find / -size +300000 -ls 옵션 가능
리눅스는 파일마다 permission이 모두 지정되어 있다.
 permission 옵션으로 찾을 수도 있다
find / -perm -4000 (-print로 기본설정 되어 있다.) -ls 옵션 가능

man find << 너무 많으니 따로 공부 해야함
-exec << 실행시키라는것 file은 어떤 형식인지 나타냄?  
wc는 카운트 해주는 것
find /etc -name services -exec file {}\; 여기서{}는 {}여기에 넣어 준다??
find /etc -name services find의 기본 패턴
리눅스 에서 ; 를 치면 한줄에서 두가지 명령 실행 하는것
find에서 ;는 exe가 끝난다는 뜻 , 두가지 명령이 아니다?
find에서는 기본형식 이후 ; 하나하나씩 분배 해준다
## grep
grep PATTERNS {FILE..} << 기본형식 {} << 디렉토리의 범위를 설정해주는것
grep -h beomseok /etc/passwd /etc/group << h로 인해 파일명은 출력을 안해준다
-n??
grep은 정규 표현식이 가능하다 따로 공부하기
grep은 무조건 이름이 있어야한다.


tail -f /var/log/syslog << 우리가 터미널을 사용할때 로그기록이 계속 갱신 되는데 그걸 확인하는것?


#@@!#!@#
ls -l 했을때
- <<일반파일 << 가 처음으로 붙는 것들
d <<디렉토리 파일
l
b 블로피 바이스 << 하드디스크나 
c 캐릭터 디바이스 입력을 바로바로 처리해주는것 ,, ex 키보드
s 심볼리 링크 디바이스
p 

install tree 다음 놓침

tty는 터미널 디바이스

내디렉토리에 심볼리링크를 걸어서 마치 카피 한것처럼
버전을 다른걸 실행 시키고 싶을 때 ln
ln -s를 붙이면 심볼릭??
ln 

파일이름이 inode를 가리키는데
하드링크는 파일이름이 다른데 같은 inode를 가리키게 할 수 있다.

아이노드가 같다는건 같은 파일이라는 뜻
카피는 독립적으로 존재
디렉토리에는 하드링크를 걸 수 없다
다른 드라이브끼리는 하드링크가 존재 하지않는다

디렉토리에서 나온 숫자는 하위에 있는 숫자를 표시

A > File

(date && errorcommand) > redirection 를 하면 date가 파일에 들어가고

A n> File
(date && errorcommand) 2> redirection 를 하면 명령을 찾을수 없습니다가 들어감
A &> File
(date && errorcommand) &> redirection 하면 표준 출력도 안되고 둘다 들어감

A >> File


pipe  페이지 단위로 more해서 넘어가도록 볼수 있다


ls -l /etc | more 는 뒤로 못돌아가지만 less는 돌아갈수 잇다(space는 넘어가기 , b는 뒤로)

-N은 번호 붙어서 나옴

ls -l /etc | grep magic??, conf

mkfifo myfifo << myfifo 생성한것
파이프로 통신할수있다
echo "HELLO TEST" > myfifo
 다른 터미널에서 cat myfifo 이런식으로 << 생성된 파일을 불러 올수 있다'
run 디렉토리에서 소켓을 생성해서 서로 통신을 할 수 있게 해준다.
s << 소켓 파일?
find /run -type s (-ls | less)
이런식으로 찾아줌 
-  파일의 종류 -는일반 d는 디렉토리 (하드링크의수) (파일 소유자의 로그인 id) (파일 소유자의 그룹이름) (파일크기 byte단위)
r = read권한
w = 쓰기권한
x = 실행

소유자권한 (), 그룹 사용자 권한 ,기타 사용자 권한

리눅스는 확장자명이 없고 권한으로 나뉘어진다
.py 이런건 접근권한과 상관 없고 보기 좋게 하기 위해서 바뀐것

접근권한을 확인하기 위한 명령어
## chmod
접근권한 변경
u-w 하면 소유자에서 w를 뺏는것ㅈ
a+x =모든 사용자
u+w,g-w 이런식으로 가능 콤마에 모두 붙여쓰기
chmod a=rwx hello.txt << 이건 모든사용자에게 모든 권한을 다주는것.
권한을 숫자모드로 줄떄는 8진수의 방법으로 준다
파일이랑
디렉토리는 디폴트로 세팅된게 다르다
디렉토리는(775로 세팅되어있다)
파일은 기본으로 디렉토리에서 실행권한을 다 빼줘있다 (664)
##umask
umask -S 
umask를 022로 바꾸면 디렉토리가 775에서 755로 변경?
0022 << 에서 맨앞에0은 특수 접근 권한을 나타낸다

umask 0111로 하면 
0을 맨앞으로 줌으로서 set uid권한을 줄 수있다
실행시킬때 set uid 권한?
ls -l /usr/bin/passwd
소유자는 슈퍼유저로 접근한다는 뜻으로 set uid
4 = set uid
실행하는 순간에만 슈퍼 접근 권한을 얻게된다?
set gid 실행하는 동안에 그룹 사용자에 슈퍼 접근권한을 주는것??
set 스티퀘이비트??

특수 접근권한??
chmod 1777 work

chown 소유자에대한 소유권 변경?
chgrp 그룹에 대한


chown "userid" : 소유권 변경
chgrp "userid" : 그룹 소유권 변경
chown "userid:userid" : 소유자, 그룹 소유권 동시 변경

상위만 아니고 
하위까지 모두 변강? -R

chown(changeown)을 동시에 바꿀땐 userid1:userid1 이런식으로 콜론을 붙힌다
ls -l 보다 더 자세히 볼때 stat hello.txt 이런식으로 확인??(시간 부분)

시간이 볼때 하나로만 저장이 되있는것처럼 보이지만
stat으로 이름수정이나 변경 시간 모두 저장이 되어 있다
inode에는 access랑 modify 시간이 모두 기록 되어 있다.
