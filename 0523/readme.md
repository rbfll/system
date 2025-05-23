# 🖥️ 프로세스 제어 요약

## 🔄 프로세스 생성 - fork()

### ⚡ 핵심 개념
- **fork()**: 부모 프로세스를 복제하여 자식 프로세스 생성
- **리턴값**: 자식에게 `0`, 부모에게 `자식 PID`
- **특징**: 한 번 호출, 두 번 리턴

```c
#include <unistd.h>
pid_t fork(void);
```

### 📝 기본 사용법
```c
pid = fork();
if (pid == 0) {
    // 자식 프로세스 코드
} else {
    // 부모 프로세스 코드
}
```

### 💡 실습 예제

#### 기본 fork 예제
```c
int main() {
    int pid = fork();
    if (pid == 0) {
        printf("자식 프로세스: PID=%d\n", getpid());
    } else {
        printf("부모 프로세스: 자식PID=%d\n", pid);
    }
}
```

#### 두 개의 자식 프로세스 생성
```c
int main() {
    if (fork() == 0) {
        printf("첫 번째 자식\n");
        exit(0);
    }
    if (fork() == 0) {
        printf("두 번째 자식\n");
        exit(0);
    }
    printf("부모 프로세스\n");
}
```

## ⏳ 자식 프로세스 기다리기 - wait()

### ⚡ 핵심 개념
- **wait()**: 자식 프로세스가 끝날 때까지 대기
- **waitpid()**: 특정 자식 프로세스 대기

```c
#include <sys/wait.h>
pid_t wait(int *status);
pid_t waitpid(pid_t pid, int *status, int options);
```

### 📝 기본 사용법
```c
int main() {
    int pid = fork();
    if (pid == 0) {
        printf("자식 프로세스 실행\n");
        exit(1);
    } else {
        int status;
        wait(&status);  // 자식이 끝날 때까지 대기
        printf("자식 프로세스 종료됨\n");
    }
}
```

## 🚀 9.2 프로그램 실행 - exec()

### ⚡ 핵심 개념
- **exec()**: 현재 프로세스를 새로운 프로그램으로 교체
- **특징**: 성공하면 **절대 리턴하지 않음**
- **실패시**: -1 리턴

```c
#include <unistd.h>
int execl(char* path, char* arg0, ...);
int execvp(char* file, char* argv[]);
```

### 🔗 fork/exec 패턴 (가장 중요!)
```c
if (fork() == 0) {
    execl("/bin/ls", "ls", "-l", NULL);  // 새 프로그램 실행
    exit(1);  // exec 실패시에만 실행됨
}
// 부모는 계속 실행
```

### 💡 실습 예제

#### 명령어 실행
```c
int main() {
    printf("부모 프로세스 시작\n");
    if (fork() == 0) {
        execl("/bin/echo", "echo", "Hello World", NULL);
        exit(1);  // exec 실패시
    }
    printf("부모 프로세스 끝\n");
}
```

#### 여러 명령어 실행
```c
int main() {
    // echo 명령 실행
    if (fork() == 0) {
        execl("/bin/echo", "echo", "hello", NULL);
        exit(1);
    }
    
    // date 명령 실행  
    if (fork() == 0) {
        execl("/bin/date", "date", NULL);
        exit(2);
    }
    
    // ls 명령 실행
    if (fork() == 0) {
        execl("/bin/ls", "ls", "-l", NULL);
        exit(3);
    }
}
```

#### 명령줄 인수로 명령어 실행
```c
int main(int argc, char *argv[]) {
    int pid = fork();
    if (pid == 0) {
        execvp(argv[1], &argv[1]);  // 첫 번째 인수를 명령어로 실행
        fprintf(stderr, "실행 실패\n");
        exit(1);
    } else {
        wait(NULL);  // 자식 종료 대기
        printf("명령어 실행 완료\n");
    }
}
```

**사용법:** `./program ls -l`

## 🎯 핵심 포인트 정리

| 🔧 함수 | 📋 기능 | 🔄 리턴값 |
|---------|---------|----------|
| `fork()` | 프로세스 복제 | 자식: 0, 부모: 자식PID |
| `exec()` | 프로그램 교체 | 성공시 리턴안함, 실패시 -1 |
| `wait()` | 자식 종료 대기 | 종료된 자식 PID |

### 🧠 기억해야 할 핵심
1. **fork()**: 똑같은 프로세스 2개 만들기
2. **exec()**: 현재 프로세스를 다른 프로그램으로 바꾸기  
3. **fork + exec**: 새 프로세스에서 다른 프로그램 실행하기
4. **wait()**: 자식이 끝날 때까지 기다리기

### 🔄 일반적인 프로세스 생성 패턴
```c
pid = fork();
if (pid == 0) {
    // 자식: 새 프로그램 실행
    exec(...);
    exit(1);
} else {
    // 부모: 자식 기다리기
    wait(&status);
}
```
