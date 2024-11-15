### C-Programming assignment 3

- Q1
    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <time.h>


    // 안의성 / 22200422 

    // 이 프로그램은 랜덤으로 행열 2개를 생성하여 그것을 연산한 값을 나타내는 프로그램입니다. 

    void Print_matrix(int A[4][5], int B[4][5]);         //배열 두개를 화면에 출력하는 함수 
    void Matrixoper(int A[4][5], int B[4][5], char Op);    //주어진 연산자도 배열두개를 계산 하여 프린트하는 함수

    int main(void) {
    srand(time(0));               //시간을 기준으로 랜덤된 수가 변하게 하는 함수
    
    char op;                      //연산자를 받을 변수
    int a[4][5]={0}, b[4][5]={0}; // 두개의 배열을 받을 열

    printf("input operator:");    //연산하고 싶은 연산자를 입력하라는 것을 표시 
    scanf("%c", &op);             //연산자를 입력받는다

    
    for(int i=0; i<4; i++){       //for문을 이용하여 
        for(int j=0; j<5; j++){
        a[i][j] = rand()%10+1;    //a열에 랜덤으로 수를 지정해준다.
        b[i][j] = rand()%10+21;   //b열에 랜덤으로 수를 지정해준다.
        }
    }  
    
    Print_matrix(a,b);            //a열과 b열을 파라매터로 입력받아 함수에 지정된 식을 수행
    Matrixoper(a,b,op);           //a열과 b열과 연산자를 파라매터로 입력받아 함수에 지정된 식을 수행
    
    return 0;
    }


    void Print_matrix(int A[4][5], int B[4][5]){    //a,b열을 수행하는 함수

    for(int i=0; i<4; i++){       //for문으로 세로 줄 수를 지정해준다.
        for(int j=0; j<5; j++){  //for문으로 5단위씩 
        printf("%-2d    ", A[i][j]);    //띄어쓰기를 하며 a를 출력
        }
        printf("          ");             //중간의 공백
        for(int j=0; j<5; j++){    //for문으로 5단위씩
        printf("%-2d    ", B[i][j]);      //띄워쓰기를 하며 b를 출력
        }
        printf("\n");                    //한 줄을 띄워준다.
    }
    printf("\n");                      //모든 for문이 끝나면 결과를 위해 한 줄을 더 띄워 준다.
    }



    void Matrixoper(int A[4][5], int B[4][5], char Op){    //a,b열을 연산자로 연산하는 함수

    int C[4][5]={0};        //연산된 새로운 수를 넣을 열

    if(Op == '+'){                  //만약 연산자가 +라면
        for(int i=0; i<4; i++){      //for문으로
        for(int j=0; j<5; j++){
            C[i][j] = A[i][j]+B[i][j];           //a+b한 값을 c에 지정해준다.
        }  
        }
        
    }else if(Op == '-'){                //만약 연산자가 -라면
        for(int i=0; i<4; i++){           //for문으로
        for(int j=0; j<5; j++){
            C[i][j] = A[i][j]-B[i][j];    //a+b한 값을 c에 지정해준다.
        } 
        }
    }

    printf("============RESULT============\n"); //결과를 알려줄 경계선을 출력해준다. 

    for(int i=0; i<4; i++){             //세로로 4줄을 출력할 for문
        for(int j=0; j<5; j++){     // 가로로 5줄을 출력할 for문
        printf("%-2d    ", C[i][j]);       //띄어쓰기를 하며 c를 출력
        }
        printf("\n");                     //한 줄을 띄워준다.
    }
    }
    ```

- Q2
    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <time.h>

    // 안의성 / 22200422
    // 이 프로그램은 항상 행의 크기가 크도록 행열을 변환해서 출력하는 프로그램입니다. 


    void transMatrix(int n[][5], int h);       //행과 열을 바꾸어 주는 함수


    int main(void) {

    srand(time(0));                     //랜덤으로 변수를 만들어주는 식

    int size;                           // 행의 크기를 입력받을 변수
    
    printf("행의 크기 입력:");             //행의 크기를 입력 받으라는 것을 출력
    scanf("%d", &size);                 //행의 크기를 입력 받음
    
    int a[size][5];                      //입력받은 size를 토대로 열을 만듬
    
    for(int i=0; i<size; i++){        //for문으로 
        for(int j=0; j<5; j++){
        a[i][j] = rand()%11;                 //a열에 랜덤한 0~10를 지정
        }
    }

    printf("배열 생성 결과 출력.\n");        //배열을 랜덤으로 생성한 것을 출력한다는 것을 출력

    for(int i=0; i<size; i++){          //for문으로 배열 세로 
        for(int j=0; j<5; j++){     //for문으로 배열 가로
        printf("%2d  ", a[i][j]);          //a열을 출력한다.
        }
        printf("\n");                     //한줄을 띄운다.
    }
    printf("\n============================\n");   // 결과를 나타내기 위한 경계선 

    if(size<5){                                  //만약 행의 크기가 가로보다 작다면 
        transMatrix(a,size);                        //함수를 불러온다.
    }else{                                        //아니라면
        printf("배열을 변환할 필요가 없습니다.\n");        //배열 변환 불필요를 출력.
    }

    return 0;                                     
    }

    void transMatrix(int n[][5], int h){            //행열을 바꾸는 함수

    for(int i=0; i<5; i++){                       //세로를 출력하는 for문
        for(int j=0; j<h; j++){                     //가로를 출력하는 for문
        printf("%2d   ", n[j][i]);                //n열을 출력한다.
        }
        printf("\n");                               //한줄을 띄운다.
    }
    }
    ```

- Q3
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    //로켓 모터의 추진력 평균을 계산하는 프로그램


    float funcForce(float w, float v, float t);      //force를 구하는 함수
    float funcThrust(float f, float w);              //thrust를 구하는 함수

    int main(void) {

    float weight, velocity, time;     //weight, velocity, time를 받을 변수
    float force, thrust;              //force, thrust를 받을 변수

    printf("INPUT DATA(ex. weight velocity time):"); //필요한 정보를 입력하라고 출력 한다.
    scanf("%f %f %f", &weight, &velocity, &time);    //필요한 정보를 입력받는다
    printf("OUTPUT DATA:\n%.2f\n%.2f\n%.2f\n\n", weight, velocity , time);          //입력받은 정보를 출력한다.

    force = funcForce(weight, velocity ,time);   //force를 계산하는 함수를 이용해 값을 리턴받는다.
    thrust = funcThrust(force, weight);          //thrust를 계산하는 함수를 이용해 값을 리턴 받는다.
    
    printf("Force due to acceleration: %.2f\n", force);  //force를 출력한다.
    printf("Total thrust due to acceleration: %.2f\n", thrust); //thrust를 출력한다. 
    return 0;
    }


    float funcForce(float w, float v, float t){      //force를 구하는 함수
    float f;                    //force 변수 
    float g = 32.2;             //중력을 나타냄

    f = w*v/(t*g);              //force를 구하는 식

    return f;                   //f를 리턴한다.
    }


    float funcThrust(float f, float w){   //thrust를 구하는 함수
    float th;                    //thrust 변수

    th = w+f;                  //thrust를 구하는 식

    return th;                 //th를 리턴해준다.
    }
    ```
    
- Q4
    ```c
    #include <stdio.h>

    // 안의성 / 22200422
    // n번째에 있는 피보나치수열을 구하는 법

    int Fibo(int n);                    //피보나치 수열을 불러오는 함수

    int main(void) {

    int number;                           //숫자를 입력받을 변수          
    
    printf("fibonaci number: ");       //몇번째 숫자를 받을 것인지 출력한다.
    scanf("%d", &number);                 //숫자를 입력받아 number에 할당
    
    printf("%d번째 피보나치 수열의 값은 %d\n",number, Fibo(number));  //원하는 번째의 피보나치 수열을 받는다. 
    
    return 0;
    }

    int Fibo(int n){                  //피보나치 함수

    //f(n) = f(n-1)+f(n-2)
    //f(n)= Fibo(n)
    
    if(n<=0){                        //n이 0보다 작거나 같으면 
        return 0;                      //리턴을 0으로 한다.
    }else if (n==1){                 //n이 1이라면  
        return 1;                      //1을 리턴한다.
    }else{                          //그외에 모든 경우에
        return Fibo(n-1)+ Fibo(n-2);   //Fibo(n-1)+Fibo(n-2)라는 재귀함수를 사용한다. 
    }
    }
    ```

