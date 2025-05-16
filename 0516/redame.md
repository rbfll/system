

# 🔧 기본적인 리눅스 명령어와 옵션 예시

## 1. ls (디렉토리 목록 보기)

- `ls -l`   : 상세 정보 포함 (long format)  
- `ls -a`   : 숨김 파일까지 모두 표시  
- `ls -lh`  : 파일 크기를 사람이 읽기 쉬운 단위로 표시 (human-readable)  

## 2. cp (파일 복사)

- `cp -r`   : 디렉토리를 재귀적으로 복사  
- `cp -i`   : 덮어쓸 경우 확인 메시지 표시  
- `cp -u`   : 대상보다 새 파일만 복사

## 3. mv (파일 이동/이름 변경)

- `mv -i` : 덮어쓸 경우 확인  
- `mv -u` : 최신 파일만 이동

## 4. rm (파일/디렉토리 삭제)

- `rm -r`   : 디렉토리 및 하위 항목 삭제  
- `rm -f`   : 강제로 삭제 (확인 생략)  
- `rm -rf`  : 경고 없이 재귀적으로 삭제 (주의!)

## 5. find (파일 검색)

- `find . -name "*.txt"`    : 현재 디렉토리 이하에서 .txt 파일 찾기  
- `find /home -type d`      : 디렉토리만 찾기  
- `find . -mtime -1`        : 1일 이내 수정된 파일  

## 6. grep (문자열 검색)

- `grep "hello" file.txt`       : 파일 내 hello 찾기  
- `grep -i "hello" file.txt`    : 대소문자 구분 없이 검색  
- `grep -r "hello" .`           : 현재 디렉토리 이하에서 재귀적으로 검색  

## 7. chmod (권한 변경)

- `chmod 755 file.sh`  : 실행 권한 포함 설정 (rwxr-xr-x)  
- `chmod +x file.sh`   : 실행 권한 추가  

## 8. tar (압축 및 압축 해제)

- `tar -cvf archive.tar dir/`       : 디렉토리를 tar로 압축  
- `tar -xvf archive.tar`            : tar 파일 압축 해제  
- `tar -czvf archive.tar.gz dir/`   : gzip 압축

## 9. ps / top / kill (프로세스 관리)

- `ps aux`       : 전체 프로세스 보기  
- `top`          : 실시간 프로세스 상태  
- `kill -9 PID`  : 강제 종료  

## 10. df / du (디스크 용량 확인)

- `df -h`        : 마운트된 디스크 용량 보기 (사람이 읽기 쉬운 단위)  
- `du -sh *`     : 현재 디렉토리 내 각 항목의 용량  

---

# 리눅스 명령 구현 옵션 만드는 함수

## ✅ 예제: my_ls.py - ls 명령어처럼 옵션 처리

```python
import os
import argparse

def list_files(path='.', all_files=False, long_format=False):
    try:
        files = os.listdir(path)
        if not all_files:
            files = [f for f in files if not f.startswith('.')]  # 숨김 파일 제외
        
        if long_format:
            for f in files:
                full_path = os.path.join(path, f)
                stat = os.stat(full_path)
                print(f"{stat.st_size:>10} bytes\t{f}")
        else:
            for f in files:
                print(f)
    except Exception as e:
        print(f"오류 발생: {e}")

def main():
    parser = argparse.ArgumentParser(description="ls 명령어 구현")
    parser.add_argument('path', nargs='?', default='.', help="대상 디렉토리")
    parser.add_argument('-a', '--all', action='store_true', help="숨김 파일 포함")
    parser.add_argument('-l', '--long', action='store_true', help="상세 정보 출력")
    
    args = parser.parse_args()
    list_files(args.path, args.all, args.long)

if __name__ == "__main__":
    main()
```

## 🔍 사용법 (터미널에서 실행)

- python my_ls.py                : 현재 폴더의 파일 목록
- python my_ls.py -a             : 숨김 파일 포함
- python my_ls.py -l             : 상세 정보 출력
- python my_ls.py -al /tmp       : /tmp 디렉토리의 모든 파일 상세 목록


## 🎯 핵심 포인트

- `argparse`를 사용해 `-a`, `-l` 등 옵션을 간단하게 정의할 수 있습니다.
- 실제 리눅스 명령처럼 옵션 이름(`-a`, `--all`) 등을 지원할 수 있어 편리합니다.

---

# ✅ 리눅스 명령어 구현에 자주 사용하는 C 함수들

## 📁 1. 디렉토리 및 파일 관련

| 함수                   | 설명                              |
|------------------------|----------------------------------|
| `opendir()`            | 디렉토리 열기                    |
| `readdir()`            | 디렉토리 내 파일 하나씩 읽기     |
| `closedir()`           | 디렉토리 닫기                   |
| `stat()` / `lstat()`   | 파일의 상세 정보 조회 (권한, 크기, 수정시간 등) |
| `mkdir()` / `rmdir()`  | 디렉토리 생성 / 삭제             |
| `remove()`             | 파일 삭제                       |
| `rename()`             | 파일 이름 변경 또는 이동         |
| `open()` / `read()` / `write()` / `close()` | 저수준 파일 입출력             |

## 🔍 2. 문자열 및 입출력

| 함수                      | 설명                          |
|---------------------------|-------------------------------|
| `printf()` / `scanf()`    | 표준 입출력                   |
| `perror()`                | 에러 메시지 출력              |
| `strcpy()`, `strcat()`, `strcmp()` | 문자열 처리                |
| `strtok()`                | 문자열 분리 (옵션 파싱에 유용) |

## ⚙️ 3. 시스템 명령 및 프로세스

| 함수           | 설명                        |
|----------------|-----------------------------|
| `fork()`       | 프로세스 생성               |
| `exec()` 계열  | 새로운 명령 실행 (예: `execl`, `execvp`) |
| `wait()` / `waitpid()` | 자식 프로세스 대기      |
| `system()`     | 쉘 명령 실행 (간단한 테스트용) |

---

# 💡리눅스 `ls` 명령어 C 구현

리눅스의 `ls` 명령어를 C 언어로 간단히 구현한 코드입니다.  
주요 기능으로 `-a` (숨김 파일 포함)와 `-l` (상세 정보 출력) 옵션을 지원합니다.

---

## ✅주요 기능

- 기본: 현재 디렉토리 파일 목록 출력  
- `-a` 또는 `--all`: 숨김 파일(`.`으로 시작하는 파일) 포함 출력  
- `-l` 또는 `--long`: 파일 상세 정보 출력  
  - 파일 권한  
  - 링크 수  
  - 소유자 이름  
  - 그룹 이름  
  - 파일 크기  
  - 마지막 수정 시간  
  - 파일 이름

---

## 🔍사용한 주요 시스템 함수 및 라이브러리

| 함수/라이브러리           | 설명                      |
|---------------------------|---------------------------|
| `opendir()`, `readdir()`   | 디렉토리 열기 및 파일 읽기  |
| `lstat()`                  | 파일 상태 및 속성 정보 조회 |
| `getopt_long()`            | 명령줄 옵션 파싱           |
| `getpwuid()`, `getgrgid()` | 소유자 및 그룹 이름 얻기    |
| `strftime()`               | 시간 형식 포맷팅           |

---

## 📄코드

```c
#include <stdio.h>
#include <stdlib.h>
#include <dirent.h>
#include <sys/stat.h>
#include <unistd.h>
#include <pwd.h>
#include <grp.h>
#include <time.h>
#include <string.h>
#include <getopt.h>
#include <errno.h>

void print_permissions(mode_t mode) {
    char perms[11] = "----------";

    if (S_ISDIR(mode)) perms[0] = 'd';
    else if (S_ISLNK(mode)) perms[0] = 'l';
    else if (S_ISCHR(mode)) perms[0] = 'c';
    else if (S_ISBLK(mode)) perms[0] = 'b';
    else if (S_ISFIFO(mode)) perms[0] = 'p';
    else if (S_ISSOCK(mode)) perms[0] = 's';

    if (mode & S_IRUSR) perms[1] = 'r';
    if (mode & S_IWUSR) perms[2] = 'w';
    if (mode & S_IXUSR) perms[3] = 'x';

    if (mode & S_IRGRP) perms[4] = 'r';
    if (mode & S_IWGRP) perms[5] = 'w';
    if (mode & S_IXGRP) perms[6] = 'x';

    if (mode & S_IROTH) perms[7] = 'r';
    if (mode & S_IWOTH) perms[8] = 'w';
    if (mode & S_IXOTH) perms[9] = 'x';

    printf("%s ", perms);
}

void print_long_format(const char *path, const struct dirent *entry) {
    struct stat st;
    char fullpath[PATH_MAX];
    snprintf(fullpath, sizeof(fullpath), "%s/%s", path, entry->d_name);

    if (lstat(fullpath, &st) == -1) {
        perror("lstat");
        return;
    }

    print_permissions(st.st_mode);
    printf("%2ld ", (long)st.st_nlink);

    struct passwd *pwd = getpwuid(st.st_uid);
    struct group *grp = getgrgid(st.st_gid);
    printf("%-8s %-8s ", pwd ? pwd->pw_name : "unknown", grp ? grp->gr_name : "unknown");

    printf("%8ld ", (long)st.st_size);

    char timebuf[64];
    struct tm *tm_info = localtime(&st.st_mtime);
    strftime(timebuf, sizeof(timebuf), "%b %d %H:%M", tm_info);
    printf("%s ", timebuf);

    printf("%s\n", entry->d_name);
}

int main(int argc, char *argv[]) {
    int opt;
    int show_all = 0;
    int long_format = 0;

    static struct option long_options[] = {
        {"all", no_argument, 0, 'a'},
        {"long", no_argument, 0, 'l'},
        {0, 0, 0, 0}
    };

    while ((opt = getopt_long(argc, argv, "al", long_options, NULL)) != -1) {
        switch (opt) {
            case 'a':
                show_all = 1;
                break;
            case 'l':
                long_format = 1;
                break;
            default:
                fprintf(stderr, "Usage: %s [-a] [-l] [directory]\n", argv[0]);
                exit(EXIT_FAILURE);
        }
    }

    const char *dirpath = ".";
    if (optind < argc) {
        dirpath = argv[optind];
    }

    DIR *dir = opendir(dirpath);
    if (!dir) {
        fprintf(stderr, "Cannot open directory '%s': %s\n", dirpath, strerror(errno));
        return EXIT_FAILURE;
    }

    struct dirent *entry;
    while ((entry = readdir(dir)) != NULL) {
        if (!show_all && entry->d_name[0] == '.') continue;

        if (long_format) {
            print_long_format(dirpath, entry);
        } else {
            printf("%s\n", entry->d_name);
        }
    }

    closedir(dir);
    return 0;
}
```
