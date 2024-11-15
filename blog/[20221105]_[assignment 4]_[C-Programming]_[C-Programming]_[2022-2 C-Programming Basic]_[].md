### C-Programming assignment 4

- Q1
    ```c
    //안의성 / 22200422
    //숫자 3개를 입력하고 함수를 이용하여 가장 큰수와 작은 수를 알려주는 프로그램

    #include <stdio.h>

    int max(int N[]); //가장 큰수를 알려주는 함수
    int min(int N[]); //가장 작은수를 알려주는 함수

    int main(void) {
    int n[3] = {0};                   //입력한 수를 저장할 배열
    for (int i = 0; i < 3; i++) {     // 3번 반복할 for문
        printf("Input number(%d):", i); //숫자를 넣으세요
        scanf("%d", &n[i]);             //숫자를 n배열에 할당한다.
    }
    printf("max:%d min:%d\n", max(n), min(n)); //가장 큰수와 작은 수를 출력한다.

    return 0;
    }

    int max(int N[]) {              //가장 큰수를 알려주는 함수
    int M = N[0];                 //임의로 가장큰 수를 저장할 변수
    for (int i = 0; i < 3; i++) { // 3번 반복할 for문
        if (M < N[i]) {             //만약 N이 M보다 크다면
        M = N[i];                 // M에 N을 할당
        }
    }
    return M; // M을 리턴
    }

    int min(int N[]) {              //가장 작은수를 알려주는 함수
    int M = N[0];                 //임의로 가장작은 수를 저장할 변수
    for (int i = 0; i < 3; i++) { // 3번 반복할 for문
        if (M > N[i]) {             //만약 N이 M보다 작다면
        M = N[i];                 // M에 N을 할당
        }
    }
    return M; // M을 리턴
    }
    ```

- Q2
    ```c
    //안의성 / 22200422
    //포인터를 이용하여 입력한 값을 출력하는 프로그램

    #include <stdio.h>
    int main(void) {
    int *count=NULL;//주솟값을 0으로 설정한 포인터 변수
    int N;//값을 입력받을 변수
    
    printf("Input number: ");//수를 입력하시오라고 출력
    scanf("%d", &N);//N에 수를 할당
    count = &N;//count에 N의 주솟값을 할당
    printf("%d", *count);//N의 주솟값을 할당받은 count에 저장된 값을 출력
    
    return 0;//0을 리턴
    
    //이전 코드의 문제점:count는 포인터 변수이기에 수를 할당하기 보다 주솟값을 할당해야한다. 
    
    }
    ```

- Q3
    ```c
    //안의성 / 22200422
    //자동차 두대의 정보를 구초체를이용하여 받고 출력하는 프로그램

    #include <stdio.h>

    struct st_car{//자동차의 정보를 저장 할 구조체

    char model[20];
    int length;
    int width;
    int depth;
    float velocity;
    };

    int main(void) {
    struct st_car car[2];//구조체를 부를 배열을 정해준다. 
    char dummy;//쓰레기값을 받을 변수
    printf("Input car data for type01(medel length width depth velocity):");//필요한 값을 입력하라고 출력
    scanf("%s %d %d %d %f%c", car[0].model , &car[0].length, &car[0].width, &car[0].depth, &car[0].velocity, &dummy);//입력받은 값을 구조체에 할당
    
    printf("Input car data for type02(medel length width depth velocity):");//필요한 값을 입력하라고 출력
    scanf("%s %d %d %d %f", car[1].model , &car[1].length, &car[1].width, &car[1].depth, &car[1].velocity);//입력받은 값을 구조체에 할당

    printf("model %s data is: %d %d %d %.1f\n",car[0].model , car[0].length, car[0].width, car[0].depth, car[0].velocity);//받은 구조체의 값을 출력
    printf("model %s data is: %d %d %d %.1f\n",car[1].model , car[1].length, car[1].width, car[1].depth, car[1].velocity);//받은 구조체의 값을 출력
    
    return 0;
    }
    ```
    
- Q4
    ```c
    //안의성 / 22200422
    //포커 게임 판독 프로그램으로 5장의 카드를 입력하면 결과를 알려주는 프로그램

    #include <stdbool.h>
    #include <stdio.h>
    #include <stdlib.h>
    #define NUM_RANKS 13
    #define NUM_SUITS 4
    #define NUM_CARDS 5

    /*prototypes*/
    void read_cards(int n[], int m[]);//두개의 열을 받을 수 있는 파라매터를 추가해준다.
    void analyze_hand(int n[], int m[], bool* straight, bool* flush, bool* four, bool* three, int* pairs);//포인터를 이용해 지역변수라도 함수를 통해 값을 할당 받을 수 있게 해준다.
    void print_result(bool straight, bool flush, bool  four, bool three, int pairs);//출력을 할 수 있게 지역변수를 받을 수 있게 파라매터를 설정해준다.


    int main(){

    //지역변수로 설정해준다.
    int num_in_rank[NUM_RANKS];
    int num_in_suit[NUM_SUITS];
    bool straight, flush, four, three;
    int pairs; /* can be 0, 1, or 2*/
    
    for(;;){
        read_cards(num_in_rank, num_in_suit); 
        analyze_hand(num_in_rank, num_in_suit,&straight, &flush, &four, &three, &pairs);
        print_result(straight, flush, four, three, pairs);
    }
    return 0;
    }

    void read_cards(int n[],int m[]){
    bool card_exists[NUM_RANKS][NUM_SUITS];
    char ch, rank_ch, suit_ch;
    int rank, suit;
    bool bad_card;
    int cards_read=0;
    for(rank=0;rank < NUM_RANKS; rank++){
    n[rank]=0;
    for(suit =0; suit < NUM_SUITS; suit++)
        card_exists[rank][suit]= false;
    }
    for(suit =0;suit < NUM_SUITS;suit++)
    m[suit]=0;
    while(cards_read < NUM_CARDS){
    bad_card = false;
    printf("Enter a card: ");
    rank_ch =getchar();
    switch (rank_ch){
        case '0': exit(EXIT_SUCCESS);
        case '2': rank = 0; break;
        case '3': rank = 1; break;
        case '4': rank = 2; break;
        case '5': rank = 3; break;
        case '6': rank = 4; break;
        case '7': rank = 5; break;
        case '8': rank = 6; break;
        case '9': rank = 7; break;
        case 't': case 'T': rank = 8; break;
        case 'j': case 'J': rank = 9; break;
        case 'q': case 'Q': rank = 10; break;
        case 'k': case 'K': rank = 11; break;
        case 'a': case 'A': rank = 12; break;
        default : bad_card = true;
    }
    suit_ch = getchar();
        switch (suit_ch){
        case 'c': case 'C': suit =0; break;
        case 'd': case 'D': suit =1; break;
        case 'h': case 'H': suit =2; break;
        case 's': case 'S': suit =3; break;
        default : bad_card = true;
    }
    while ((ch = getchar ())!='\n')
        if (ch != ' ') bad_card = true;
        if(bad_card)
        printf("bad card: ignored. \n");
        else if(card_exists[rank][suit])
        printf("Duplicated card; ignored\n");
        else{
        n[rank]++;
        m[suit]++;
        card_exists[rank][suit]=true;
        cards_read++;
        }
    }
    }


    void analyze_hand(int n[], int m[], bool* straight, bool* flush, bool* four, bool* three, int* pairs){
    int num_consec=0;
    int rank, suit;
    *straight = false;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    *flush = false;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    *four = false;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    *three = false;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    *pairs = 0;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    // check for flush
    for(suit =0;suit<NUM_SUITS;suit++)
    if(m[suit] == NUM_CARDS)
        *flush = true;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    // check for straight
    rank =0;
    while (n[rank]==0)rank++;
    for(;rank <NUM_RANKS && n[rank]>0;rank++)
    num_consec++;
    if(num_consec == NUM_CARDS){
    *straight =true;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    return;
    }
    // check for 4 of a kind, 3 of a kind, and pairs
    for(rank=0;rank < NUM_RANKS;rank++){
    if(n[rank]==4) *four = true;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    if(n[rank]==3) *three = true;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    if(n[rank]==2) *pairs += 1;//포인터변수니 앞에 *을 붙여서 값을 변하게 만들어준다.
    }
    }

    void print_result(bool straight, bool flush,bool  four, bool three, int pairs){
    if(straight && flush) printf("Straight flush");
    else if(four) printf("Four of a kind");
    else if(three && pairs == 1) printf("Full house");
    else if(flush) printf("Flush");
    else if(straight) printf("Straight");
    else if(three) printf("Three of a kind");
    else if(pairs == 2) printf("Two pairs");
    else if(pairs == 1) printf("Pair");
    else printf("High card");
    printf("\n\n");
    }
    ```

- Q5
    ```c
    //안의성 / 22200422
    //원하는 수를 입력하면 그만큼 랜덤하 문자를 출력해주는 프로그램

    #include <stdio.h>
    #include <time.h>
    #include <stdlib.h>
    
    void print_array(int n);//결과를 출력해줄 함수

    int main(void) {
    int num;//출력할 수를 위한 변수
    printf("Input number of characters:");//원하는 수를 입력하라고 출력
    scanf("%d", &num);//입력받은 수를 num에 할당
    print_array(num);//함수를 불러온다.
    return 0;
    }

    void print_array(int n){
    int count=0;//줄띄우기를 위한 변수
    int* S;//포인터 함수
    S = (int*)malloc(sizeof(int)*n);//원하는 만큼 공간을 확보한다.
    srand(time(0));//랜덤한 수를 지정해줄 식
    for(int i=0; i<n; i++){//n만큼 반복할 for문
        S[i] = rand()%126;//S에 아스키코드의 개수사이의 수를 랜덤으로 할당
        if(S[i] <= ' '){//만약 할당된 값이 ' '보다 작으면
        i--;//i를 하나 빼준다.
        }
    }
    for(int i=0; i<n; i++){//n만큼 반복한 for문
        count++;//count를 1씩 더해준다.
        printf("%c ", S[i]);//할당된 문자를 프린트한다.
        if(count%10==0){//만약 count를 10으로 나누었을때 나머지가 0이면
        printf("\n");//한줄을 띄워준다.
        }
    }
    free(S);//사용했던 메모리를 반환해준다.
    }
    ```

- Q6
    ```c
    //안의성 / 22200422
    //입력된 세수의 중간을 찾아서 출력하는 프로그램

    #include <stdio.h>
    int* findmedian(int *a,int *b, int *c);//중간 수를 찾아내줄 함수
    int main(void) {
    int num[3];//입력한 수를 입력받을 변수
    printf("Input numbers(1 2 3):");//수를 입력하라고 출력
    scanf("%d %d %d", &num[0], &num[1], &num[2]);//입력한 수를 할당
    printf("Median number is %d", *findmedian(&num[0], &num[1], &num[2]));//중간수를 출력한다.
    return 0;
    }

    int* findmedian(int *a,int *b, int *c){//중간수를 가려낼 함수
    if(*c<=*a && *a<=*b || *b<=*a && *a<=*c){//a가 중간수이면
        return a;//a를 리턴한다.
    }
    if(*a<=*b && *b<=*c || *c<=*b && *b<=*a){//b가 중간수이면
        return b;//b를 리턴한다.
    }
    if(*b<=*c&&*c<=*a || *a<=*c&&*c<=*b){//c가 중간수이면
        return c;//c를 리턴한다.
    }
    return 0;
    }
    ```

- Q7
    ```c
    //안의성 / 22200422
    //입력한 알파벳이 소문자면 대문자로 바꾸어주는 프로그램

    #include <stdio.h>
    #include <string.h>

    void chString(char *S);//알파벳이 소문자면 대문자로 바꾸어주는 함수

    int main(void) {
    char str[80];//입력할 문장을 저장할 변수

    printf("Input String:");//입력을 하라고 출력
    scanf("%s", str);//입력한 문장을 str에 할당
    chString(str);//알파벳이 소문자면 대문자로 바꾸어주는 함수
    printf("UpperCase: %s", str);//str을 출력
    
    return 0;
    }

    void chString(char *S){

    char s[80];//문장을 편하게 편집할수있게 새로 저장할 변수

    strcpy(s, S);//s에 S의 문장을 붙여넣기
    for(char i=0; i<strlen(S); i++){//for문으로 S문장 길이 만큼 반복
        if('a'<= s[i] && s[i] <= 'z'){//소문자이면
        s[i] -= 'a'-'A';//대문자로변할만큼의 아스키코드를 빼준다.
        }
    }
    strcpy(S, s);//S에 s문장을 붙여넣기
    }
    ```
