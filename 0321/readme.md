## 명령어의 경로 확인: `which`
- **사용법**  
  `$ which 명령어`  
  명령어의 절대경로를 보여준다.

- **예**  
  ```bash
  $ which ls  
  /bin/ls  
  $ which pwd  
  /bin/pwd  
  $ which passwd  
  /bin/passwd

## Wild Character
- `*` : all
- `?` : one

## 디렉터리 삭제: `rmdir` (remove directory)
- **사용법**  
  `$ rmdir 디렉터리+`  
  디렉터리(들)을 삭제한다.  
  **주의**: 빈 디렉터리만 삭제할 수 있다.

---

## 간단한 파일 만들기: `cat`
- **사용법**  
  `$ cat > 파일`  
  표준 입력 내용을 모두 파일에 저장한다. 파일이 없으면 새로 만든다.

- **예**  
  ```bash
  $ cat > cs1.txt  
  ...  
  ^D

## 간단한 파일 만들기: `touch`
- **사용법**  
  `$ touch 파일`  
  파일 크기가 0인 이름만 있는 빈 파일을 만들어준다.

- **예**  
  ```bash
  $ touch cs1.txt  
  $ ls -asl cs1.txt

## 파일 내용 출력
- **파일 내용 출력과 관련된 명령어들**
  - `cat`, `more`, `head`, `tail`, `wc` 등

- **사용법**
  ```bash
  $ 명령어 파일  
  $ 명령어 파일*

## 페이지 단위로 파일 내용 보기: `more`
- **사용법**
  ```bash
  $ more 파일+

## 파일 앞부분 보기: `head`
- **사용법**
  ```bash
  $ head [–n] 파일*

## 핵심 개념
- 리눅스의 디렉터리는 루트로부터 시작하여 계층 구조를 이룬다.
- 절대경로명은 루트 디렉터리부터 시작하고, 상대경로명은 현재 디렉터리부터 시작한다.

---

## 학번, 이름을 입력받아 화면에 출력하는 것을 c프로그램으로 구현
![스크린샷 2025-03-21 114203](https://github.com/user-attachments/assets/ca3555d2-2cd9-4939-b8d7-9da8654380a6)

