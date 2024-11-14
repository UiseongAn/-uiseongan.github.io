### C-Programming assignment 1

- Q1
    ```c
    #include <stdio.h>

    // 안의성 / 2022/9/23
    // 내 이름과 학번을 출력하는 프로그램 
    // C프로그래밍 과제 1

    int main(void) {
    printf("\"안의성\"  \\22200422\\\n");    //내 이름과 학번이다. 
    return 0;
    }
    ```

- Q2
    ```c
    #include <stdio.h>
    // 안의성 / 2022 / 9 / 23
    // 5개의 숫자를 입력받고 합과 평균을 구하는 프로그램
    // C프로그래밍 과제

    int main(void) {

    int num = 0;                   //입력받을 숫자를 뜻하는 변수
    int total = 0;                 //전부 합한 것을 뜻하는 변수
    float average = 0;             //평균을 뜻하는 변수
    
    for (int i = 1; i<=5; i++){      //5개의 수를 입력받게 해줄 수 있는 for문
    printf("0%d번째 입력:",i);       //입력하라고 출력되는 문장
    scanf("%d", &num);             //입력된 숫자를 할당하는 num

    total +=num;                 //원래 있던 total에 num에 할당된 수를 더한다.
    
    }
    average = 1.0*total/5;       //total에 5를 나눠준다. 
    
    printf("입력이 완료되었습니다.\n입력받은 숫자의 합: %-5d, 평균: %.2f입니다.\n",total,average);         //값을 출력한다.
    
    return 0;
    }
    ```

- Q3
    ```c
    #include <stdio.h>

    // 안의성 / 2022 / 9 / 23
    //2개의 실수를 입력받고 몫과 나머질ㄹ 구하는 프로그램
    //C프로그래밍 과제 3

    int main(void) {

    float num1, num2;                  //두 실수의 변수
    float result;                      //두 실수를 나누었을때 몫
    int remain;                        //두 실수를 나누었을때 나머지
    
    printf("Input float1 float2: ");   //변수를 입력하는 것을 출력
    scanf("%f %f", &num1, &num2 );     //변수를 할당

    result = num1 / num2;              //나눗셈의 계산식
    remain = (int)num1 % (int)num2;    //나머지의 계산식
    
    printf("입력 받은 실수는 %.3f, %.3f\n",num1,num2);  //입력받은 실수 출력
    printf("몫:%.3f\n나머지:%d\n",result,remain);    //몫과 나머지 출력
    return 0;
    }
    ```
    
- Q4
    ```c
    #include <stdio.h>

    //안의성 / 2022 / 9 / 23
    //학번을 입력받고 입력 받은 학번을 이용하여 입학년도, 학과, 입학순서를 출력하는 프로그램
    //C프로그래밍 과제 4

    int main(void){

    int num;                           //학번의 변수
    int a, b, c, d, e, f, g, h;        //각 자릿수를 위한 변수들
    
    printf("Input student number: ");  //학번을 입력하라는 것을 출력
    scanf("%d",&num);                  //학번을 할당

    a = num/10000000;          //학번의 첫번째 자릿수를 구하기 위해 int로 나눠줌 
    num %= 10000000;           //나눠준 것의 나머지를 다시 num에 할당
    
    b = num/1000000;            //위와 같음
    num %= 1000000;
    
    c = num/100000;
    num %=100000;
    
    d = num/10000;
    num %=10000;
    
    e = num/1000;
    num %=1000;
    
    f = num/100;
    num %=100;
    
    g = num/10;
    
    h = num%10;

        if(a ==1 ){                    //첫자리가 1이면 19년도
        printf("1999년 이전 입학\n입학년도:19%d%d\n",b,c); //뒤에 b,c붙여서 년도 완성
        }else if(a ==2){              //첫자리가 2면 20년도
        printf("2000년 이후 입학\n입학년도:20%d%d\n",b,c); // 위와 같음
        }

        if( d ==5 && e==5){              //각 d자릿수와 e자릿수를 비교하여 전공을 출력
        printf("전공:새내기\n");
        }else if( d ==6 && e==6){
        printf("전공:인간문화\n");
        }else if( d ==7 && e==7){
        printf("전공:로봇제어\n");
        }else if( d ==8 && e==8){
        printf("전공:전산공학\n");
        }else if( d ==9 && e==9){
        printf("전공:인간생명\n");
        }else{
        printf("전공번호오류\n");          //다른 수를 입력 받았을 때
        }

    printf("입학순번:%d%d%d\n",f,g,h);    //입학한 순서를 나타내는 번호 출력
    return 0;
    }
    ```

- Q5
    ```c
    #include <stdio.h>

    //안의성 / 2022 / 9 / 23
    //사용자에게 정수 2개와 연산자를 순차적으로 입력 받은 후 연산 결과를 출력하는 프로그램
    //연산자 종류  +, -, *, /, %
    int main() {

    char o;                        //계산 기호 변수
    int a,b;                       //계산할 수 변수
    int r ;                        //결과 변수

    printf("Input first integers: ");    //처음 입력받을 계산할 변수를 입력하라는 것을 출력
        scanf("%d",&a);                    //입력받은 수를 할당
    printf("Input second integers: ");   //두번쨰로 입력받을 계산할 변수를 입력 하라는 것을 출력
        scanf("%d",&b);                    //입력받은 수를 할당
    printf("Input operater:");           //계산기호를 입력하라는 것을 출력
        scanf("%c", &o);                   //버퍼찌꺼기를 제거해줄 구문
        scanf("%c", &o);                   //계산기호를 할당

    // if(o == '+'){                     //if문으로 했을 때
    //   r = a+b;
    // }else if(o == '-'){
    //   r = a-b;
    // }else if(o == '*'){
    //   r = a*b;
    // }else if(o == '/'){
    //   r = a/b;
    // }else if(o == '%'){
    //   r = a%b;
    // }

    switch(o){                       //스위치 문으로 했을 때
        case '+':                      //케이스 + 덧셈
                r = a+b;               //더한 수를 결과에 할당
                break;                 //스위치문 빠져나오기
        case '-':                      //케이스 - 뺄셈
                r = a-b;               //뺀 수를 결과에 할당
                break;                 //스위치문 빠져나오기
        case '*':                      //케이스 * 곱셈
                r = a*b;               //곱한 수를 결과에 할당
                break;                 //스위치문 빠져나오기
        case '/':                      //케이스 / 나눗셈
                r = a/b;               //나눈 수를 결과에 할당
                break;                 //스위치문 빠져나오기
        case '%':                      //케이스 % 나머지
                r = a%b;               //나머지를 결과에 할당
                break;                 //스위치문 빠져나오기
    }
    
    printf("result:%d\n",r);         //결과를 출력
    
    return 0;
    }
    ````

- Q6
    ```c
    #include <stdio.h>

    //안의성 / 2022 / 09 / 25
    //두자리 숫자를 입력 받아 그것을 영어로 출력되는 프로그램
    //C프로그래밍 과제 6

    int main(void) {
    
    int number;                                 //입력 받을 숫자의 변수

    printf("Enter number(1~99): ");           //1부터99사이의 수를 입력하라는 것을 출력
    scanf("%d", &number);                     //수를 입력받음
    
    if (number<1 || number>99 ) {            //지정된 숫자가 아니면 다시 하라는 메시지를 출력
        printf("Enter numbers between 1 and 99");
        printf("Try again"); 
        }
    
    if (number>=10 && number<=19){           //10~19는 영어가 규칙적이지 않기때문에 따로 분리해준다. 
        
        switch(number){                        //스위치문을 이용하여 알맞는 영어 단어를 출력한다.
        case 10: printf("ten\n");            //입력받은수가 알맞는 케이스면 지정된 문자를 출력한다. 
            break;                             //스위치문을 빠져나온다.
        case 11: 
            printf("eleven\n");                //위와 같다
            break;
        case 12: 
            printf("twelve\n");    
            break;
        case 13: 
            printf("thirteen\n");  
            break;
        case 14: 
            printf("fourteen\n");  
            break;
        case 15: 
            printf("fifteen\n");   
            break;
        case 16: 
            printf("sixteen\n");   
            break;
        case 17: 
            printf("seventeen\n"); 
            break;
        case 18: 
            printf("eighteen\n");  
            break;
        case 19: 
            printf("nineteen\n");  
            break;
        default:  break;  
        }
    }else{ 
        
        switch( number / 10 ) {                    //10의 자리수를 출력하는 스위치 문
        case 2: printf("twenty ");               //10으로 나누었을때 정수부분이 2가 나오면 지정된 문자를 출력한다.
            break;                                 //스위치문을 빠져나온다.
        case 3: printf("thirty ");               //위와 같다.
            break;
        case 4: printf("forty ");     
            break;
        case 5: printf("fifty ");     
            break;
        case 6: printf("sixty ");     
            break;
        case 7: printf("seventy ");   
            break;
        case 8: printf("eighty ");    
            break;
        case 9: printf("ninety ");    
            break; 
        default: printf(" ");                   //1이 나올 경우는 위에서 먼저 실행해줬으니, 0일 경우 공백을 출력 해준다.
            break; 
        } 
        
        switch( number % 10 ){                   //1의 자리 숫자를 출력하는 스위치문
        case 0: printf("\n");                  //1의자리 숫자가 0일 때 \n을 출력해준다
            break;                               //스위치문을 빠져나온다.
        case 1: printf("one\n");               //위와 같다.
            break;
        case 2: printf("two\n");    
            break;
        case 3: printf("three\n");  
            break;
        case 4: printf("four\n");   
            break;
        case 5: printf("five\n");   
            break;
        case 6: printf("six\n");     
            break;
        case 7: printf("seven\n");   
            break;
        case 8: printf("eight\n");  
            break;
        case 9: printf("nine\n");   
            break;
        default:                                    //그외 다른경우에는 스위치문을 빠져나온다.
            break; 
        }
    }
    
    return 0;
    }
    ```

