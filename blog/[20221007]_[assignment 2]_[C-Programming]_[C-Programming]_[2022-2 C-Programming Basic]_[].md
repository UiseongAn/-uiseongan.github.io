### C-Programming assignment 2

- Q1
    ```c
    #include <stdio.h>

    //안의성 / 22200422
    // 10부터 시작해서 1씩 작아져서 1이되면 출력을 멈춘다.

    int main(void) {
    for(int i=0; i<10; i++){    //for문을 이용해 변수 i를 1씩 증가시켜준다. 그리고 i<10를 충족시키지 않으면 작동을 멈춘다.
        printf("%d ",10-i);       //i가 1씩 증가하면서 10에서 부터 수가 점점 작아지는 것을 출력한다.
    }
    return 0;
    }
    ```

- Q2-1
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    // 숫자를 입력받아 입력받은 숫자만큼 *을 출력한다.


    int main(void) {
    int num;                          //수를 입력받는 변수
    int i=1;                          //while문을 카운트해줄 변수
    
    printf("Input number:");          //숫자를 입력하라는 것을 출력
    scanf("%d", &num);                //입력받은 숫자를 num에 할당

    while(1){                         //무한루프구문 
        printf("*");                    //*을 출력한다.
        if(i==num){                     //i가 num이랑 같아지면
        break;                        //while문을 벗어난다.
        }
        i++;                            //i가 1씩 증가한다.
    }
    printf("\n");                     //한줄 띄워준다.
    return 0;
    }
    ```
- Q2-2
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    // 수를 입력받고 입력받은 수만큼 *을 출력한다.

    int main(void) {  
    int num;                        //수를 할당받을 변수
    printf("Input number:");        //수를 입력하라고 출력
    scanf("%d",&num);               //입력받은 수를 num에 할당

    for(int i=0; i<num; i++){       //for문을 통해 0부터 num-1의 횟수만큼 for문을 실행
        printf("*");                  //*을 출력한다
    }
    printf("\n");                   //한줄을 띄워준다
    return 0;
    }
    ```

- Q3
    ```c
    #include <stdio.h>

    //안의성 / 22200422
    //수를 입력받아 그 개수만큼 홀수면 * 짝수면 +를 출력하는 프로그램

    int main(void) {
    int num;                                //수를 할당받을 변수
    printf("input number:");                //수를 입력하라는 것을 출력
    scanf("%d", &num);                      //입력받은 수를 num에 할당

    if(num%2==1){                           //만약 num을 2로 나누었을때 나머지가 1이라면 즉 홀수라면 
        for(int i=0; i<num; i++){             //for문을 이용해 num의 개수만큼
        printf("*");                        //*을 출력
        }
    }else if(num%2==0){                     //만약 num을 2로 나누었을때 나머지가 0이라면 즉 짝수라면 
        for(int i=0; i<num; i++){             //for문을 이용해 num의 개수만큼
        printf("+");                        //+를 출력
        }
    }
    printf("\n");                           //한줄 띄워준다.
    return 0;
    }
    ```
    
- Q4
    ```c
    #include <stdio.h>

    //안의성 / 22200422
    //수를 입력하면 그 크기만큼 X자를 출력하는 프로그램

    int main(void) {
    int num;                      //크기를 입력받을 변수
    printf("input number:");      //숫자를 입력하라는 것을 출력
    scanf("%d", &num);            //입력받은 수를 num에 할당

    if(num%2==0){                 //만약 num을 2로 나누었을때 즉 짝수라면 
        num++;                      //num에 1을 더해준다

        for(int i=0; i<(num-1)/2; i++){       //X의 윗부분을 출력할 for문
        
        for(int j=0; j<i; j++){             //처음의 공백을 출력할 for문
            printf(" ");                      //j만큼 공백을 출력한다.
        }
        printf("+");                        //+을 하나 출력한다.
        for(int j=0; j<num-2*(i+1); j++){   //+과+사이 공백을 출력할 for문
            printf(" ");                      //공백을 출력한다.
        }
        printf("+\n");                      //끝 +을 출력하고 한줄을 띄어준다.
        }
        
        for(int j=0; j<(num-1)/2; j++){       //중간 + 앞의 공백을 출력할 for문
            printf(" ");                      //공백을 출력한다.
        }
        printf("+\n");                      //+를 출력하고 한줄 띄워준다.
        
        for(int i=0; i<(num-1)/2; i++){       //X의 아래부분을 출력할 for문
        
        for(int j=0; j<(num-1)/2-(i+1); j++){   //처음의 공백을 출력할 for문
            printf(" ");                          //공백을 출력한다.
        }
        printf("+");                            //첫번째 +을 하나 출력한다.
        for(int j=0; j<2*i+1; j++){             //+과+ 사이 공백을 출력할 for문
            printf(" ");                          //공백을 출력한다.
        }
        printf("+\n");                          //마지막+을 출력하고 한줄을 띄워준다.
        }
    }else{

        for(int i=0; i<(num-1)/2; i++){       //X의 윗부분을 출력할 for문
        
        for(int j=0; j<i; j++){             //처음의 공백을 출력할 for문
            printf(" ");                      //j만큼 공백을 출력한다.
        }
        printf("*");                        //*을 하나 출력한다.
        for(int j=0; j<num-2*(i+1); j++){   //*과*사이 공백을 출력할 for문
            printf(" ");                      //공백을 출력한다.
        }
        printf("*\n");                      //끝 *을 출력하고 한줄을 띄어준다.
        }
        
        for(int j=0; j<(num-1)/2; j++){       //중간 * 앞의 공백을 출력할 for문
            printf(" ");                      //공백을 출력한다.
        }
        printf("*\n");                      //*를 출력하고 한줄 띄워준다.
        
        for(int i=0; i<(num-1)/2; i++){       //X의 아래부분을 출력할 for문
        
        for(int j=0; j<(num-1)/2-(i+1); j++){   //처음의 공백을 출력할 for문
            printf(" ");                          //공백을 출력한다.
        }
        printf("*");                            //첫번째 *을 하나 출력한다.
        for(int j=0; j<2*i+1; j++){             //*과* 사이 공백을 출력할 for문
            printf(" ");                          //공백을 출력한다.
        }
        printf("*\n");                          //마지막*을 출력하고 한줄을 띄워준다.
        }
        
    }
    return 0;
    }
    ```

- Q5
    ```c
    #include <stdio.h>

    //안의성 / 22200422
    // 3,6,9단을 출력하는 프로그램

    int main(void) {
    for(int i=1; i<=9; i++){                     //구구단을 반복하는 for문
        for(int j=1; j<=3; j++){                   //3,6,9단만 반복하는 for문
        if(j==1 && i>3){                         //만약 3단에서 단 개수가 3을 초과하면
            printf("        ");                    //공백을 출력해라
        }else if (j == 2 && i>6){                //만약 6단에서 단 개수가 6을 초과하면 
            printf("        ");                    //공백을 출력해라
        }else{                                   //둘 다 해당이 안되면
        printf("%d*%d=%02d  ", 3*j,i,3*j*i);     //구구단을 출력해라
        }
        }
        printf("\n");                              //한 줄을 띄워준다.
    }
    return 0;
    }
    ```

- Q6
    ```c
    #include <stdio.h>

    //안의성 / 22200422
    //XY+YX=99를 만족하는 모든 경우의 수와 총 반복 횟수를 출력하는 프로그램

    int main(void) {
    int a, b;                            //XY와 YX를 할당해줄 변수
    int count =0;                        //전체 실행횟수를 세아려줄 변수
    int realcount=0;                     //원하는 수를 찾기까지의 실행횟수를 세아려줄 변수
    for(int i=0; i<=9; i++){             //X를 0에서 9까지 반복해줄 for문
        for(int j=0; j<=9; j++){           //Y를 0에서 9까지 반복해줄 for문
        a= i*10+j;                       //a는 10*X + Y 해서 XY를 만들어 준다.
        b= j*10+i;                       //b는 10*Y + X 해서 YX를 만들어 준다.
        if(a+b==99){                     //a+b가 99일 때
            printf("%02d+%02d=99\n",a,b);  //이때 a,b가 무엇인지 식을 출력한다.
            realcount=count;               //원하는 식을 찾을때까지의 실행횟수를 출력하기 위해 식을 출력할 때만 realcount에 횟수를 저장해준다.
        }
        count++;                         //총 실행 횟수를 세어주는 식
        }
    }
    printf("count:%d\n",realcount);      //원하는 식을 모두 찾을때까지의 실행횟수를 출력한다.
                                        //한줄 띄운다.
    return 0;
    }
    ```

- Q7
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    // 입력한 숫자가 소수인지 판단하는 프로그램 

    int main(void) {

    int num;                              //입력받을 변수
    int a=0;                              //플래그 변수
    
    printf("Input number:");              //수를 입력하라는 것을 출력
    scanf("%d", &num);                    //입력받은 수를 num에 할당

    for(int i = 2; i<num; i++){           //for문을 통하여 2부터 num-1수까지 i를 1씩 증가시킨다. 
        if(num%i == 0){                     //만약 num을 i로 나누었을때 나머지가 0이라면  
        a=1;                              // a에 1을 할당한다.
        }
    }


    if(a==0){                                      //만약 a가 그대로 0이라면 
        printf("%d is a prime number\n", num);       //num은 소수이다를 출력한다.
    }else if(a==1){                                //만약 a가 1이라면
        printf("%d is a not prime number\n", num);   //num은 소수가 아니다를 출력한다.
    }
    
    return 0;
    }
    ```

- Q8
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    // 세로와 가로의 크기를 입력받고 (5*2 => 세로길이 5, 가로길이 2) 결과를 출력하는 프로그램 작성 but 3의 배수는 *로 출력함.

    int main(void) {

    int a,b;                          //세로와 가로의 변수
    int count=1;                      //전체의 수를 세줄 카운트
    
    printf("Input m*n:");             //세로와 가로를 입력하라고 출력
    scanf("%d*%d", &a, &b);           //입력받은 세로와 가로를 a,b에 할당
    printf("\n=========output=========\n"); //output창을 나타내줌

    for(int i=0; i<a; i++){              //세로를 담당하는 for문
        for(int j=0; j<b; j++){            //가로를 담당하는 for문
        if(count%3==0){                  //만약 count에 3을 나누었을때 나머지가 0이라면 
            printf(" *");                  //*을 출력해준다.
        }else{                           //그렇지 않다면
            printf("%2d", count);          //count를 열에 맞춰서 출력해준다.
        }
        count++;                         //count를 하나씩 증가시킨다.
        }
        printf("\n");                      //가로입력이 끝나면 줄을 한줄 띄운다.
    }
    return 0;
    }
    ```
