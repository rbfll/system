# 유닉스 역사 및 표준

## AT&T 벨 연구소(Bell Lab)에서 개발됨
- **Ken Thompson**이 어셈블리어로 개발
- **D. Ritchie**가 C 언어로 다시 작성  
  - C 언어는 Unix를 작성하기 위한 언어로 밀접하게 관련됨
  - 이론적으로 C 컴파일러만 있으면 이식 가능
- 소스코드를 대학에 개방함

## 유닉스의 큰 흐름
- **System V (시스템 V)**
- **BSD (Berkeley Standard Distribution) 유닉스**
- **리눅스 (Linux)**

# 리눅스 (Linux)

## PC를 위한 효율적인 유닉스 시스템
- 1991년 헬싱키 대학의 **Linus Torvalds**에 의해 개발됨

## 소스코드 공개
- 인터넷상에서 자원자들에 의해 기능 추가 및 확장됨
- 공용 도메인상의 무료 OS

## 다양한 하드웨어 플랫폼에 포팅 가능
- PC, 워크스테이션, 서버, 메인프레임 등
- 놀라운 성능 및 안정성 제공

# 슈퍼유저 (Superuser)

## 슈퍼유저란?
- 시스템을 관리할 수 있는 사용자
- 슈퍼유저가 사용하는 계정이 **root** 

# sudo 명령어 사용

## `sudo` 명령어
```bash
$ sudo <명령어>
$ sudo apt install gcc   # gcc 컴파일러 설치
$ sudo passwd root       # root 패스워드 설정


