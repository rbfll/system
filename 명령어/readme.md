

## I. 파일 및 디렉토리 관리 명령어

이 명령어들은 파일 시스템을 조작하고 관리하는 데 기본적으로 사용됩니다.

### `ls`
**기능**: 디렉토리의 내용(파일 및 하위 디렉토리)을 나열합니다.
```bash
ls                  # 현재 디렉토리 내용 표시
ls -la              # 자세한 정보와 숨김 파일 포함하여 표시
ls -lh              # 파일 크기를 읽기 쉬운 형태로 표시
```

### `cd`
**기능**: 현재 작업 디렉토리를 변경합니다.
```bash
cd /path/to/directory    # 절대 경로로 이동
cd ..                    # 상위 디렉토리로 이동
cd ~                     # 홈 디렉토리로 이동
cd -                     # 이전 디렉토리로 이동
```

### `pwd`
**기능**: 현재 작업 디렉토리의 전체 경로를 출력합니다.
```bash
pwd                      # 현재 위치의 절대 경로 출력
```

### `mkdir`
**기능**: 새로운 디렉토리를 생성합니다.
```bash
mkdir new_directory      # 단일 디렉토리 생성
mkdir -p path/to/nested  # 중첩된 디렉토리 생성
```

### `rmdir`
**기능**: 비어 있는 디렉토리를 삭제합니다.
```bash
rmdir empty_directory    # 빈 디렉토리 삭제
```

### `cp`
**기능**: 파일이나 디렉토리를 복사합니다.
```bash
cp file1 file2           # 파일 복사
cp -r dir1 dir2          # 디렉토리 재귀적 복사
cp *.txt backup/         # 특정 패턴 파일들 복사
```

### `mv`
**기능**: 파일이나 디렉토리의 이름을 변경하거나 이동합니다.
```bash
mv oldname newname       # 파일/디렉토리 이름 변경
mv file.txt /path/to/    # 파일 이동
```

### `rm`
**기능**: 파일이나 디렉토리를 삭제합니다.
```bash
rm file.txt              # 파일 삭제
rm -r directory          # 디렉토리 재귀적 삭제
rm -f file.txt           # 강제 삭제
```

### `cat`
**기능**: 파일의 내용을 터미널에 출력하거나 여러 파일을 연결(concatenate)합니다.
```bash
cat file.txt             # 파일 내용 출력
cat file1 file2 > merged # 여러 파일을 합쳐서 새 파일 생성
```

### `less` / `more`
**기능**: 파일 내용을 페이지 단위로 보여주어 긴 파일을 편리하게 볼 수 있게 합니다.
```bash
less largefile.txt       # 파일을 페이지 단위로 조회
more largefile.txt       # 파일을 페이지 단위로 조회 (기본적)
```

### `head`
**기능**: 파일의 시작 부분(기본 10줄)을 출력합니다.
```bash
head file.txt            # 첫 10줄 출력
head -n 20 file.txt      # 첫 20줄 출력
```

### `tail`
**기능**: 파일의 끝 부분(기본 10줄)을 출력합니다. (로그 파일 모니터링에 유용)
```bash
tail file.txt            # 마지막 10줄 출력
tail -f logfile.log      # 실시간으로 파일 끝 부분 모니터링
```

### `find`
**기능**: 특정 기준에 따라 파일이나 디렉토리를 검색합니다.
```bash
find /path -name "*.txt" # 특정 패턴의 파일 검색
find . -type d           # 디렉토리만 검색
find . -size +1M         # 1MB 이상 파일 검색
```

### `grep`
**기능**: 파일 내용에서 특정 패턴(문자열)을 검색합니다.
```bash
grep "pattern" file.txt  # 파일에서 패턴 검색
grep -r "pattern" ./     # 디렉토리 내 재귀적 검색
grep -i "pattern" file   # 대소문자 무시하고 검색
```

### `wc`
**기능**: 파일의 줄 수, 단어 수, 문자 수를 계산하여 출력합니다.
```bash
wc file.txt              # 줄 수, 단어 수, 문자 수 출력
wc -l file.txt           # 줄 수만 출력
wc -w file.txt           # 단어 수만 출력
```

### `touch`
**기능**: 파일의 접근 시간, 수정 시간을 변경하거나 새로운 빈 파일을 생성합니다.
```bash
touch newfile.txt        # 빈 파일 생성
touch -t 202401011200 file # 특정 시간으로 타임스탬프 변경
```

### `chmod`
**기능**: 파일 또는 디렉토리의 접근 권한(읽기, 쓰기, 실행)을 변경합니다.
```bash
chmod 755 file.txt       # 숫자 방식으로 권한 설정
chmod +x script.sh       # 실행 권한 추가
chmod -w file.txt        # 쓰기 권한 제거
```

### `chown`
**기능**: 파일 또는 디렉토리의 소유자를 변경합니다.
```bash
chown user:group file    # 소유자와 그룹 변경
chown user file          # 소유자만 변경
chown -R user:group dir/ # 디렉토리 재귀적 소유자 변경
```

### `ln`
**기능**: 파일에 대한 하드 링크 또는 심볼릭 링크(바로가기)를 생성합니다.
```bash
ln file hardlink         # 하드 링크 생성
ln -s file symlink       # 심볼릭 링크 생성
```

---

## II. 프로세스 관리 명령어

이 명령어들은 시스템에서 실행 중인 프로세스를 확인하고 제어하는 데 사용됩니다.

### `ps`
**기능**: 현재 실행 중인 프로세스들의 스냅샷을 보여줍니다.
```bash
ps                       # 현재 터미널의 프로세스 표시
ps aux                   # 모든 프로세스를 자세히 표시
ps -ef                   # 모든 프로세스를 전체 형식으로 표시
```

### `top`
**기능**: 시스템의 프로세스 상태, CPU 및 메모리 사용량 등을 실시간으로 모니터링합니다.
```bash
top                      # 실시간 프로세스 모니터링
top -u username          # 특정 사용자의 프로세스만 표시
```

### `htop`
**기능**: top 명령어보다 사용자 친화적인 인터페이스를 제공하는 대화형 프로세스 뷰어입니다.
```bash
htop                     # 향상된 프로세스 모니터링
```

### `kill`
**기능**: 특정 프로세스에 시그널을 보내어 종료하거나 제어합니다.
```bash
kill 1234                # PID 1234 프로세스 종료
kill -9 1234             # 강제 종료
kill -STOP 1234          # 프로세스 일시 중단
```

### `killall`
**기능**: 특정 이름을 가진 모든 프로세스에 시그널을 보냅니다.
```bash
killall firefox          # firefox 이름의 모든 프로세스 종료
killall -9 chrome        # chrome 프로세스 강제 종료
```

### `pstree`
**기능**: 프로세스들을 부모-자식 관계의 트리 형태로 보여줍니다.
```bash
pstree                   # 프로세스 트리 표시
pstree -p                # PID와 함께 표시
```

### `nice` / `renice`
**기능**: 프로세스의 스케줄링 우선순위를 설정하거나 변경합니다.
```bash
nice -n 10 command       # 낮은 우선순위로 명령 실행
renice 5 -p 1234         # 실행 중인 프로세스 우선순위 변경
```

### `bg`
**기능**: 중단된 작업을 백그라운드로 보냅니다.
```bash
bg                       # 가장 최근에 중단된 작업을 백그라운드로
bg %1                    # 작업 번호 1을 백그라운드로
```

### `fg`
**기능**: 백그라운드 작업을 포그라운드로 가져옵니다.
```bash
fg                       # 가장 최근 백그라운드 작업을 포그라운드로
fg %1                    # 작업 번호 1을 포그라운드로
```

### `jobs`
**기능**: 현재 쉘 세션의 백그라운드 작업 목록을 표시합니다.
```bash
jobs                     # 현재 작업 목록 표시
jobs -l                  # PID와 함께 작업 목록 표시
```

---

## III. 시스템 정보 및 네트워크 명령어

시스템의 상태를 확인하고 네트워크 연결을 관리하는 데 사용되는 명령어들입니다.

### `df`
**기능**: 디스크 파티션별 사용 가능한 공간 및 사용량을 보고합니다.
```bash
df                       # 모든 파일시스템의 디스크 사용량 표시
df -h                    # 읽기 쉬운 형태로 표시
df /                     # 루트 파티션의 사용량만 표시
```

### `du`
**기능**: 파일이나 디렉토리가 차지하는 디스크 공간을 요약하여 보여줍니다.
```bash
du -h directory          # 디렉토리 크기를 읽기 쉬운 형태로 표시
du -s *                  # 현재 디렉토리의 각 항목 크기 요약
du -sh ~/.cache          # 특정 디렉토리의 총 크기
```

### `free`
**기능**: 시스템의 물리적 메모리와 스왑 메모리 사용량을 보여줍니다.
```bash
free                     # 메모리 사용량 표시
free -h                  # 읽기 쉬운 형태로 표시
free -m                  # MB 단위로 표시
```

### `uname`
**기능**: 시스템 커널 이름, 호스트 이름, 커널 버전 등 시스템 정보를 출력합니다.
```bash
uname -a                 # 모든 시스템 정보 표시
uname -r                 # 커널 버전 표시
uname -m                 # 머신 아키텍처 표시
```

### `hostname`
**기능**: 시스템의 호스트 이름을 표시하거나 설정합니다.
```bash
hostname                 # 현재 호스트 이름 표시
hostname newname         # 호스트 이름 변경 (임시)
```

### `ifconfig` / `ip`
**기능**: 네트워크 인터페이스의 설정 및 상태 정보를 확인하거나 변경합니다. (ip는 ifconfig의 현대적인 대체 명령어)
```bash
ifconfig                 # 모든 네트워크 인터페이스 정보 표시
ifconfig eth0            # 특정 인터페이스 정보 표시
ip addr show             # 네트워크 인터페이스 정보 표시 (현대적)
ip route                 # 라우팅 테이블 표시
```

### `ping`
**기능**: 네트워크 호스트와의 연결성을 테스트하고 응답 시간을 측정합니다.
```bash
ping google.com          # 호스트 연결성 테스트
ping -c 4 8.8.8.8        # 4번만 ping 전송
ping -i 2 localhost      # 2초 간격으로 ping
```

### `netstat`
**기능**: 활성 네트워크 연결, 라우팅 테이블, 인터페이스 통계 등을 표시합니다.
```bash
netstat -tuln            # TCP/UDP 포트 사용 현황 표시
netstat -r               # 라우팅 테이블 표시
netstat -i               # 네트워크 인터페이스 통계
```

### `ss`
**기능**: 소켓 관련 통계를 표시합니다 (netstat의 더 빠르고 현대적인 버전).
```bash
ss -tuln                 # TCP/UDP 소켓 정보 표시
ss -p                    # 프로세스 정보와 함께 표시
ss -s                    # 소켓 통계 요약
```

### `route`
**기능**: IP 라우팅 테이블을 표시하거나 조작합니다.
```bash
route -n                 # 라우팅 테이블을 숫자 형태로 표시
route add default gw gateway # 기본 게이트웨이 추가
```

### `who` / `w`
**기능**: 현재 시스템에 로그인한 사용자 정보를 보여줍니다.
```bash
who                      # 로그인한 사용자 목록
w                        # 사용자 활동 정보와 함께 표시
whoami                   # 현재 사용자명 표시
```

### `last`
**기능**: 시스템의 최근 로그인 기록을 보여줍니다.
```bash
last                     # 최근 로그인 기록 표시
last username            # 특정 사용자의 로그인 기록
last -n 10               # 최근 10개 기록만 표시
```

---

## IV. 개발 및 유틸리티 명령어

이 범주에는 프로그램을 개발하거나 시스템을 관리하는 데 유용한 도구와, C/C++ 프로그램에서 핵심적인 기능을 수행하는 라이브러리 함수가 포함됩니다.

### `man`
**기능**: 명령어의 매뉴얼 페이지를 열어 자세한 사용법과 옵션을 제공합니다.
```bash
man ls                   # ls 명령어의 매뉴얼 페이지 열기
man -k keyword           # 키워드로 매뉴얼 페이지 검색
man 3 printf             # 특정 섹션의 매뉴얼 페이지 열기
```

### `which`
**기능**: 특정 명령어의 실행 파일이 위치한 경로를 찾아줍니다.
```bash
which python             # python 실행 파일 경로 찾기
which -a gcc             # 모든 해당 실행 파일 경로 표시
```

### `whereis`
**기능**: 명령어의 바이너리, 소스 코드, 매뉴얼 페이지 파일의 위치를 찾아줍니다.
```bash
whereis ls               # ls 관련 파일들의 위치 찾기
whereis -b gcc           # 바이너리 파일만 찾기
whereis -m python        # 매뉴얼 페이지만 찾기
```

### `alias`
**기능**: 기존 명령어에 대한 짧은 별칭(별명)을 생성합니다.
```bash
alias ll='ls -la'        # ll을 ls -la의 별명으로 설정
alias ..='cd ..'         # ..을 상위 디렉토리 이동의 별명으로
alias                    # 현재 설정된 별명 목록 표시
```

### `history`
**기능**: 이전에 쉘에서 입력했던 명령어 목록을 보여줍니다.
```bash
history                  # 명령어 히스토리 표시
history | grep keyword   # 특정 키워드가 포함된 명령어 검색
!100                     # 히스토리의 100번째 명령어 실행
```

### `echo`
**기능**: 터미널에 문자열을 출력합니다. (쉘 스크립트에서 변수 값 확인 등에 사용)
```bash
echo "Hello World"       # 문자열 출력
echo $PATH               # 환경 변수 값 출력
echo -n "No newline"     # 줄바꿈 없이 출력
```

### `tar`
**기능**: 여러 파일을 하나의 아카이브 파일로 묶거나 해제하는 데 사용됩니다. (압축 기능 포함 가능)
```bash
tar -czf archive.tar.gz files/  # 디렉토리를 gzip 압축하여 아카이브
tar -xzf archive.tar.gz         # gzip 아카이브 해제
tar -tf archive.tar             # 아카이브 내용 목록 보기
```

### `getopt` (C/C++ 표준 라이브러리 함수)
**기능**: C/C++ 프로그램에서 **짧은 명령줄 옵션** (예: -a, -v)을 파싱하는 표준 함수입니다. 사용자 친화적인 프로그램 인터페이스 구현에 필수적입니다.

```c
#include <unistd.h>

int getopt(int argc, char * const argv[], const char *optstring);

// 사용 예시
int main(int argc, char *argv[]) {
    int opt;
    while ((opt = getopt(argc, argv, "abc:")) != -1) {
        switch (opt) {
            case 'a':
                // -a 옵션 처리
                break;
            case 'b':
                // -b 옵션 처리
                break;
            case 'c':
                // -c 옵션 처리 (인자 필요)
                printf("Option c: %s\n", optarg);
                break;
        }
    }
}
```

### `getopt_long` (C/C++ 표준 라이브러리 함수)
**기능**: C/C++ 프로그램에서 **긴 명령줄 옵션** (예: --help, --verbose)을 파싱하는 함수입니다. GNU 시스템에서 널리 사용되며 getopt의 확장 버전입니다.

```c
#include <getopt.h>

int getopt_long(int argc, char * const argv[],
                const char *optstring,
                const struct option *longopts,
                int *longindex);

// 사용 예시
static struct option long_options[] = {
    {"help",    no_argument,       0, 'h'},
    {"verbose", no_argument,       0, 'v'},
    {"output",  required_argument, 0, 'o'},
    {0, 0, 0, 0}
};

int main(int argc, char *argv[]) {
    int c;
    int option_index = 0;
    
    while ((c = getopt_long(argc, argv, "hvo:",
                           long_options, &option_index)) != -1) {
        switch (c) {
            case 'h':
                // --help 또는 -h 처리
                break;
            case 'v':
                // --verbose 또는 -v 처리
                break;
            case 'o':
                // --output 또는 -o 처리
                printf("Output file: %s\n", optarg);
                break;
        }
    }
}
```

---

- ln 명령을 통해 하나의 파일이 여러 이름을 가질 수 있고, 특히 '하드 링크'는 원본 파일이 삭제되어도 데이터가 유지되는 독특한 특성을 가진다는 점이 신기했습니다. 
