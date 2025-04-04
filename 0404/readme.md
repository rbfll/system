- ## 0부터 255의 정수를 입력 받아 2진수로 출력하고, 1의 개수가 몇개인지 출력하며, 상위 8비트에서 왼쪽 4비트를 2진수로 출력하는 C프로그램
![image](https://github.com/user-attachments/assets/d8ca8b5a-5daa-4752-bc98-d5ecc8b1993c)


```
#include <stdio.h>

int main() {
    int num;
    int binary[8]; 
    int count = 0; 

    printf("0부터 255 사이의 정수를 입력하세요: ");
    scanf("%d", &num);

    if (num < 0 || num > 255) {
        printf("오류: 0부터 255 사이의 정수를 입력해야 합니다.\n");
        return 1;
    }

    printf("\n입력된 %d의 2진수 표현: ", num);
    for (int i = 7; i >= 0; i--) {
        binary[i] = num % 2;
        num /= 2;
        
        if (binary[i] == 1) {
            count++;
        }
    }

    for (int i = 0; i < 8; i++) {
        printf("%d", binary[i]);
    }
    printf("\n");

    printf("1의 개수: %d\n", count);

 
    printf("상위 4비트: ");
    for (int i = 0; i < 4; i++) {
        printf("%d", binary[i]);
    }
    printf("\n");

    return 0;
}
```
