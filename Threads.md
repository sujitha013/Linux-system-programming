##1.Write a C program to create a thread that prints "Hello, World!"? 
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
printf("Hello World!\n");
return NULL;
}
int main()
{
pthread_t th;
pthread_create(&th,NULL,&threadfun,NULL);
pthread_join(th,NULL);
return 0;
}
```
2.Modify the above program to create multiple threads, each printing its own message? 
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun1(void*arg)
{
printf("Hello World from thread 1\n");
return NULL;
}
void*threadfun2(void*arg)
{
printf("Hello World from thread 2\n");
return NULL;
}
void*threadfun3(void*arg)
{
printf("Hello World from thread 3\n");
return NULL;
}
void*threadfun4(void*arg)
{
printf("Hello World from thread 4\n");
return NULL;
}
int main()
{
pthread_t th1,th2,th3,th4;
pthread_create(&th1,NULL,threadfun1,NULL);
pthread_create(&th2,NULL,threadfun2,NULL);
pthread_create(&th3,NULL,threadfun3,NULL);
pthread_create(&th4,NULL,threadfun4,NULL);
pthread_join(th1,NULL);
pthread_join(th2,NULL);
pthread_join(th3,NULL);
pthread_join(th4,NULL);
printf("All threads execution is completed.\n");
return 0;
}
```
##3.Develop a C program to create two threads that print numbers from 1 to 10 concurrently?
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
int i;
for(i=1;i<=10;i++)
{
printf("Thread 2:%d\n",i);
sleep(1);
}
return NULL;
}
int main()
{
int i;
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
for(i=1;i<=10;i++)
{
printf("Thread 1:%d\n",i);
sleep(1);
}
pthread_join(th1,NULL);
return 0;
}
```
##4.Implement a C program to create a thread that calculates the factorial of a given number?
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
int i,n;
long long pod=1;
printf("Enter a number:");
scanf("%d",&n);
for(i=1;i<=n;i++)
{
pod=pod*i;
}
printf("Factorial of %d is :%lld\n",n,pod);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("The thread execution is completed.\n");
return 0;
}
```
##5.Write a C program to create two threads that print their thread IDs?
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun1(void*arg)
{
printf("Thread 1 ID:%lu\n",pthread_self());
return NULL;
}
void*threadfun2(void*arg)
{
printf("Thread 2 ID:%lu\n",pthread_self());
return NULL;
}
int main()
{
pthread_t th1,th2;
pthread_create(&th1,NULL,threadfun1,NULL);
pthread_create(&th2,NULL,threadfun2,NULL);
pthread_join(th1,NULL);
pthread_join(th2,NULL);
return 0;
}
```
##6.Develop a C program to create a thread that prints the sum of two numbers? 
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
int a,b,c;
printf("Enter a value for a:");
scanf("%d",&a);
printf("Enter a value for b:");
scanf("%d",&b);
c=a+b;
printf("sum of two numbers %d and %d is:%d",a,b,c);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
return 0;
}
```
##7.Implement a C program to create a thread that calculates the square of a number?
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
int n,sq;
printf("Enter a number:");
scanf("%d",&n);
sq=n*n;
printf("Squre of %d is:%d\nx",n,sq);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##8.Write a C program to create a thread that prints the current date and time? 
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
#include<time.h>
void*threadfun(void*arg)
{
time_t  t;
struct tm *tm_info;
time(&t);
tm_info=localtime(&t);
printf("Current date and time:%s",asctime(tm_info));
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##9.Develop a C program to create a thread that checks if a number is prime?
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
void*threadfun(void*arg)
{
int i,n,count=0;
printf("Enter a number:");
scanf("%d",&n);
if(n==1)
{
printf("Not a prime number.\n");
}
else
{
for(i=2;i<n;i++)
{
if(n%i==0)
{
count++;
}
}
if(count==0)
{
printf("%d is a prime number.\n",n);
}
else
{
printf("%d is not a prime number.\n",n);
}
}
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##10.Implement a C program to create a thread that checks if a given string is a palindrome? 
```c
#include<stdio.h>
#include<unistd.h>
#include<pthread.h>
#include<string.h>
#include<ctype.h>
void*threadfun(void*arg)
{
char str[1000];
printf("Enter string:");
fgets(str,sizeof(str),stdin);
str[strcspn(str,"\n")]='\0';
int start=0,end=strlen(str)-1;
while(start<=end)
{
while(start<=end&&!isalpha(str[start]))
{
start++;
}
while(start<=end&&!isalpha(str[end]))
{
end--;
}
if(tolower(str[start])!=tolower(str[end]))
{
printf("String \"%s\" not a palindrome.\n",str);
return NULL;
}
start++;
end--;
}
printf("String \"%s\" is a palindrome.\n",str);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##11.Write a C program to create a thread that prints "Hello, World!" with thread synchronization? 
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*threadfun(void*arg)
{
pthread_mutex_lock(&mtx);
printf("Hello World!\n");
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
pthread_mutex_destroy(&mtx);
printf("Thread execution completed.\n");
return 0;
}
```
##12.Develop a C program to create two threads that print their thread IDs and synchronize their output? 
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*threadfun1(void*arg)
{
pthread_mutex_lock(&mtx);
printf("Thread 1 ID:%lu\n",pthread_self());
pthread_mutex_unlock(&mtx);
return NULL;
}
void*threadfun2(void*arg)
{
pthread_mutex_lock(&mtx);
printf("Thread 2 ID:%lu\n",pthread_self());
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1,th2;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,threadfun1,NULL);
pthread_create(&th2,NULL,threadfun2,NULL);
pthread_join(th1,NULL);
pthread_join(th2,NULL);
pthread_mutex_destroy(&mtx);
printf("Thread execution completed.\n");
return 0;
}
```
##13.Implement a C program to create a thread that generates random numbers and synchronizes access to a shared buffer? 
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<time.h>
#include<pthread.h>
#define SIZE 10
int index=0;
int buffer[SIZE];
pthread_mutex_t mtx;
void*randomnum(void*arg)
{
for(int i=0;i<SIZE;i++)
{
int num=rand()%100;
pthread_mutex_lock(&mtx);
buffer[index++]=num;
printf("Thread generated:%d\n",num);
pthread_mutex_unlock(&mtx);
sleep(1);
}
return NULL;
}
int main()
{
pthread_t th1;
srand(time(NULL));
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,randomnum,NULL);
pthread_join(th1,NULL);
printf("Final buffer contents:");
for(int i=0;i<SIZE;i++)
{
printf("%d ",buffer[i]);
}
printf("\n");
pthread_mutex_destroy(&mtx);
return 0;
}
```
##14.Write a C program to create a thread that performs addition of two numbers with mutex locks? 
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*threadfun(void*arg)
{
pthread_mutex_lock(&mtx);
int a,b,c;
printf("Enter values of a and b:");
scanf("%d%d",&a,&b);
c=a+b;
printf("addition of two numbers:%d\n",c);
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,threadfun,NULL);
pthread_join(th1,NULL);
printf("thread execution is completed.\n");
pthread_mutex_destroy(&mtx);
return 0;
}
```
##15.Implement a C program to create two threads that increment and decrement a shared 
variable, respectively, using mutex locks?
```c
#include<stdio.h>
#include<pthread.h>
int share_var;
pthread_mutex_t mtx;
void*threadinc(void*arg)
{
for(int i=0;i<5;i++)
{
pthread_mutex_lock(&mtx);
share_var++;
printf("Threadinc increment value:%d\n",share_var);
pthread_mutex_unlock(&mtx);
}
return NULL;
}
void*threaddec(void*arg)
{
for(int i=0;i<5;i++)
{
pthread_mutex_lock(&mtx);
share_var--;
printf("Threaddec decrement value:%d\n",share_var);
pthread_mutex_unlock(&mtx);
}
return NULL;
}
int main()
{
pthread_t th1,th2;
printf("Enter share_var:");
scanf("%d",&share_var);
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,threadinc,NULL);
pthread_create(&th2,NULL,threaddec,NULL);
pthread_join(th1,NULL);
pthread_join(th2,NULL);
printf("Final  shared variable value:%d",share_var);
pthread_mutex_destroy(&mtx);
return 0;
}
```
##16.Implement a C program to create a thread that prints prime numbers up to a given limit 
with mutex locks? 
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int num,i,j,count;
printf("Enter a number:");
scanf("%d",&num);
for(i=1;i<=num;i++)
{
count=0;
if(i==1)
{
continue;
}
for(j=2;j<=i/2;j++)
{
if(i%j==0)
{
count++;
break;
}
}
if(count==0)
{
printf("%d ",i);
}
}
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("\nThread execution completed.\n");
pthread_mutex_destroy(&mtx);
return 0;
}
```
##17.Implement a C program to create a thread that calculates the sum of Fibonacci numbers up 
to a given limit using dynamic programming with mutex locks?
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int num,i,n1=0,n2=1;
int next=n1+n2,sum=n1+n2;
printf("Enter a number:");
scanf("%d",&num);
printf("%d %d ",n1,n2);
for(i=3;i<=num;i++)
{
printf("%d ",next);
sum+=next;
n1=n2;
n2=next;
next=n1+n2;
}
printf("\nSum of fabinacci series of number:%d",sum);
pthread_mutex_unlock(&mtx);
return  NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_mutex_destroy(&mtx);
return 0;
}
```
##18.Write a C program to create a thread that checks if a given year is a leap year using 
dynamic programming with mutex locks? 
```c
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int *ptr=(int*)malloc(sizeof(int));
printf("Enter a year:");
scanf("%d",ptr);
if((*ptr%4==0&&(*ptr%100!=0))||(*ptr%400==0))
{
printf("The year %d is a leap year.\n",*ptr);
}
else
{
printf("The year %d is not a leap year.\n",*ptr);
}
free(ptr);
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_mutex_destroy(&mtx);
return 0;
}
```
##19.Write a C program to create a thread that checks if a given string is a palindrome using 
dynamic programming with mutex locks?
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<pthread.h>
#include<stdlib.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
char *str=(char*)malloc(100*sizeof(char));
printf("Enter string:");
fgets(str,100,stdin);
str[strcspn(str,"\n")]='\0';
int start=0,end=strlen(str)-1,ispal=1;
while(start<=end)
{
while(start<=end&&!isalpha(str[start]))
{
start++;
}
while(start<=end&&!isalpha(str[end]))
{
end--;
}
if(tolower(str[start])!=tolower(str[end]))
{
ispal=0;
break;
}
start++;
end--;
}
if(ispal)
{
printf("The string \"%s\" is a palindrome.\n",str);
}
else
{
printf("The string \"%s\" is not  a palindrome.\n",str);
}
free(str);
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
pthread_mutex_destroy(&mtx);
return 0;
}
```
##20.Implement a C program to create a thread that performs selection sort on an array of 
integers? 
```c
#include<stdio.h>
#include<pthread.h>
#define SIZE 100
int a[SIZE];
int size;
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int  i;
printf("Enter Array elements from Thread1:");
for(i=0;i<size;i++)
{
scanf("%d",&a[i]);
}
pthread_mutex_unlock(&mtx);
return NULL;
}
void*thread2(void*arg)
{
pthread_mutex_lock(&mtx);
int i,j,temp;
printf("Sorted array from Thread2:");
for(i=0;i<size;i++)
{
for(j=i+1;j<size;j++)
{
if(a[j]<a[i])
{
temp=a[i];
a[i]=a[j];
a[j]=temp;
}
}
}
for(i=0;i<size;i++)
{
printf("%d ",a[i]);
}
pthread_mutex_unlock(&mtx);
return NULL;
}

int main()
{
pthread_t th1,th2;
printf("Enter size:");
scanf("%d",&size);
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_create(&th2,NULL,thread2,NULL);
pthread_join(th2,NULL);
pthread_mutex_destroy(&mtx);
printf("\nThread execution completed.\n");
return 0;
}
```
##21.Develop a C program to create a thread that calculates the area of a triangle? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread(void*arg)
{
int b,h;
printf("Enter Base:");
scanf("%d",&b);
printf("Enter Height:");
scanf("%d",&h);
int result=(b*h)/2;
printf("Area of Triangle=%d\n",result);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
```
##22.Write a C program to create a thread that calculates the sum of squares of numbers from 1 
to 100? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread(void*arg)
{
int i,sq,sum_sq=0;
for(i=1;i<=100;i++)
{
sq=i*i;
sum_sq=sum_sq+sq;
}
printf("Sum of squares from 1 to 100:%d\n",sum_sq);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##23.Develop a C program to create a thread that calculates the greatest common divisor (GCD) 
of two numbers? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread(void*)
{
int a,b,i,gcd=0;
printf("Enter a and b:");
scanf("%d%d",&a,&b);
int res=a>b?a:b;
for(i=1;i<=res;i++)
{
if(a%i==0&&b%i==0)
{
gcd=i;
}
}
printf("\nGreatest common divisior=%d\n",gcd);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##24.Implement a C program to create a thread that calculates the sum of even numbers from 1 
to 100?
```c
#include<stdio.h>
#include<pthread.h>
void*thread(void*)
{
int i,sum=0;
for(i=1;i<=100;i++)
{
if(i%2==0)
{
sum=sum+i;
}
}
printf("Sum of Even numbers=%d\n",sum);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##25.Implement a C program to create a thread that performs multiplication of two matrices?
```c
#include<stdio.h>
#include<pthread.h>
#define ROWS 100
#define COLS 100
int a[ROWS][COLS],b[ROWS][COLS],c[ROWS][COLS];
int rows,cols;
void*thread1(void*arg)
{
int i,j;
printf("Enter elements for matrix a:");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
scanf("%d",&a[i][j]);
}
}
printf("Enter elements for matrix b:");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
scanf("%d",&b[i][j]);
}
}

return NULL;
}
void*thread2(void*arg)
{
int i,j,k;
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
c[i][j]=0;
c[i][j]=0;
for(k=0;k<cols;k++)
{
c[i][j]+=a[i][k]*b[k][j];
}
}
}
printf("\nResult matrix:\n");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
printf("%d ",c[i][j]);
}
printf("\n");
}
return NULL;
}
int main()
{
pthread_t th1,th2;
printf("Enter rows and cols:");
scanf("%d%d",&rows,&cols);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_create(&th2,NULL,thread2,NULL);
pthread_join(th2,NULL);
printf("Thread execution complete.\n");
return 0;
}
```
##26..Develop a C program to create a thread that calculates the average of numbers from 1 to 
100? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int i,sum=0;
float avg;
for(i=1;i<=100;i++)
{
sum=sum+i;
}
avg=sum/100.00;
printf("Average of numbers from 1 to 100:%.2f\n",avg);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##27.Implement a C program to create a thread that generates a random string?
```c
#include<pthread.h>
#include<time.h>
#include<stdlib.h>
void*thread1(void*arg)
{
char str[11];
int i;
srand(time(NULL));
for(i=0;i<10;i++)
{
int isupper=rand()%2;
if(isupper)
{
str[i]='A'+rand()%26;
}
else
{
str[i]='a'+rand()%26;
}
}
str[10]='\0';
printf("Generated random string:%s\n",str);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##28.Write a C program to create a thread that checks if a given number is a perfect square? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int i,n,flag=0;
printf("Enter a number:");
scanf("%d",&n);
for(i=1;i*i<=n;i++)
{
if(i*i==n)
{
flag=1;
break;
}
}
if(flag)
{
printf("%d is a prfect square.\n",n);
}
else
{
printf("%d is not a perfect square.\n",n);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
```
##29.Write a C program to create a thread that calculates the sum of digits of a given number?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int num,rem,sum=0;
printf("Enter a number:");
scanf("%d",&num);
int temp=num;
while(temp>0)
{
rem=temp%10;
sum=sum+rem;
temp=temp/10;
}
printf("Sum of digits of a number %d:%d\n",num,sum);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##30.Develop a C program to create a thread that finds the maximum element in an array? 
```c
#include<stdio.h>
#include<pthread.h>
int a[100];
int size;
void*thread1(void*arg)
{
int i;
printf("Enter elements:");
for(i=0;i<size;i++)
{
scanf("%d",&a[i]);
}
return NULL;
}
void*thread2(void*arg)
{
int i,max=a[0];
for(i=1;i<size;i++)
{
if(a[i]>max)
{
max=a[i];
}
}
printf("Maximum element in the array:%d\n",max);
return NULL;
}
int main()
{
pthread_t th1,th2;
printf("Enter size:");
scanf("%d",&size);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_create(&th2,NULL,thread2,NULL);
pthread_join(th2,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##31.Write a C program to create a thread that sorts an array of strings?
```c
#include<stdio.h>
#include<pthread.h>
#include<string.h>
char str[100][100];
int n;
void*thread1(void*arg)
{
int i,j;
printf("Enter strings:");
for(i=0;i<n;i++)
{
scanf("%s",str[i]);
}
for(i=0;i<n;i++)
{
for(j=i+1;j<n;j++)
{
if(strcmp(str[i],str[j])>0)
{
char temp[100];
strcpy(temp,str[i]);
strcpy(str[i],str[j]);
strcpy(str[j],temp);
}
}
}
printf("Sorted strings:\n");
for(i=0;i<n;i++)
{
printf("%s\n",str[i]);
}
return NULL;
}
int main()
{
pthread_t th1;
printf("Enter the number of strings:");
scanf("%d",&n);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##32.Implement a C program to create a thread that calculates the square root of a number? 
```c
#include<stdio.h>
#include<pthread.h>
#include<math.h>
void*thread1(void*arg)
{
int num;
printf("Enter a number:");
scanf("%d",&num);
float result=sqrt(num);
printf("Square root =%.6f\n",result);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##33.Develop a C program to create a thread that calculates the average of numbers in an array? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int a[100],i,sum=0,size;
float avg;
printf("Enter size:");
scanf("%d",&size);
printf("Enter elements:");
for(i=0;i<size;i++)
{
scanf("%d",&a[i]);
sum=sum+a[i];
}
avg=(float)sum/size;
printf("Average of the array elements:%.2f\n",avg);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##34..Write a C program to create a thread that generates a random password? 
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <pthread.h>

void* generate_password(void* arg) {
    int len = *(int*)arg;
    char charset[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*";
    char password[len + 1]; // +1 for null terminator

    for(int i = 0; i < len; i++) {
        int idx = rand() % strlen(charset);
        password[i] = charset[idx];
    }
    password[len] = '\0'; // null-terminate the string

    printf("Generated password: %s\n", password);
    return NULL;
}

int main() {
    pthread_t th1;
    int length;

    printf("Enter desired password length: ");
    scanf("%d", &length);

    srand(time(NULL)); // seed random number generator

    pthread_create(&th1, NULL, generate_password, &length);
    pthread_join(th1, NULL);

    printf("Thread execution completed.\n");
    return 0;
}
```
##35.Implement a C program to create a thread that checks if a number is even or odd? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int num;
printf("Enter number:");
scanf("%d",&num);
if(num%2==0)
{
printf("%d is an even number.\n",num);
}
else
{
printf("%d is an odd number.\n",num);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##36.Develop a C program to create a thread that calculates the sum of elements in an array? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int a[100],i,sum=0,size;
printf("Enter size:");
scanf("%d",&size);
printf("Enter elements:");
for(i=0;i<size;i++)
{
scanf("%d",&a[i]);
sum=sum+a[i];
}
printf("Sum of the array elements:%d\n",sum);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##37.Write a C program to create a thread that calculates the factorial of numbers from 1 to 10? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int  i,j;
long long pod;
for(i=1;i<=10;i++)
{
pod=1;
for(j=1;j<=i;j++)
{
pod=pod*j;
}
printf("Factorial of  %d:%lld\n",i,pod);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##38.Implement a C program to create a thread that calculates the area of a rectangle? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int h,b;
printf("Enter height:");
scanf("%d",&h);
printf("Enter breadth:");
scanf("%d",&b);
int rect_area=h*b;
printf("Area of Rectangular:%d\n",rect_area);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##39.Write a C program to create a thread that searches for a given number in an array?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int a[100],i,size,search,store=-1;
printf("Enter size:");
scanf("%d",&size);
printf("Enter elements:");
for(i=0;i<size;i++)
{
scanf("%d",&a[i]);
}
printf("Enter element to search:");
scanf("%d",&search);
for(i=0;i<size;i++)
{
if(a[i]==search)
{
store=i;
break;
}
}
if(store!=-1)
{
printf("%d found at %d position.\n",search,store);
}
else
{
printf("%d is not found.\n",search);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##40.Write a C program to create a thread that performs addition of two matrices? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int  rows,cols;
printf("Enter rows and cols:");
scanf("%d%d",&rows,&cols);
int a[rows][cols],b[rows][cols],c[rows][cols],i,j;
printf("Enter elements to first matrix:\n");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
scanf("%d",&a[i][j]);
}
}
printf("Enter elements to second matrix:\n");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
scanf("%d",&b[i][j]);
}
}
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
c[i][j]=a[i][j]+b[i][j];
}
}
printf("Resultant matrix:\n");
for(i=0;i<rows;i++)
{
for(j=0;j<cols;j++)
{
printf("%d ",c[i][j]);
}
printf("\n");
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##41.Develop a C program to create a thread that calculates the length of a given string?
```c
#include<stdio.h>
#include<pthread.h>
#include<string.h>
void*thread1(void*arg)
{
char str[100];
int i,len=0;
printf("Enter string:");
fgets(str,sizeof(str),stdin);
str[strcspn(str,"\n")]='\0';
for(i=0;str[i]!='\0';i++)
{
len++;
}
printf("lenght of the string \"%s\" is :%d\n",str,len);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##42.Write a C program to create a thread that prints the even numbers between 1 and 20?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int i;
printf("Even numbers between 1 to 20:\n");
for(i=1;i<=20;i++)
{
if(i%2==0)
{
printf("%d ",i);
}
}
printf("\n");
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##43.Develop a C program to create two threads that print odd and even numbers alternately? 
```c
#include<unistd.h>
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int i;
for(i=1;i<=20;i++)
{
if(i%2==0)
{
printf("Even:%d\n",i);
sleep(1);
}
}
return NULL;
}
void*thread2(void*arg)
{
int i;
for(i=1;i<=20;i++)
{
if(i%2!=0)
{
printf("Odd:%d\n",i);
sleep(1);
}
}
return NULL;
}
int main()
{
pthread_t th1,th2;
pthread_create(&th1,NULL,thread1,NULL);
pthread_create(&th2,NULL,thread2,NULL);
pthread_join(th1,NULL);
pthread_join(th2,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##44.Implement a C program to create a thread that calculates the sum of squares of numbers 
from 1 to 10?
```c
#include<stdio.h>
#include<pthread.h>
#include<math.h>
void*thread1(void*arg)
{
int i,pod=1,sum=0;
for(i=1;i<=10;i++)
{
pod=pow(i,2);
sum=sum+pod;
}
printf("Sum of squares from 1 to 10:%d\n",sum);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##45.Write a C program to create a thread that calculates the product of numbers from 1 to 5? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int i,pod=1;
for(i=1;i<=5;i++)
{
pod=pod*i;
}
printf("Product of 1 to 5 is:%d\n",pod);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##46.Implement a C program to create a thread that prints the ASCII values of characters in a 
given string? 
```c
#include<string.h>
#include<stdio.h>
#include<pthread.h>
#include<ctype.h>
void*thread1(void*arg)
{
char str[100];
int i;
printf("Enter string:");
fgets(str,sizeof(str),stdin);
str[strcspn(str,"\n")]='\0';
printf("ASCII values of characters:\n");
for(i=0;str[i]!='\0';i++)
{
if(isupper(str[i]))
{
printf("%c->%d\n",str[i],str[i]);
}
else
{
printf("%c->%d\n",str[i],str[i]);
}
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##47.Develop a C program to create a thread that calculates the sum of all prime numbers up to 
a given limit? 
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int num,i,j,count,sum=0;
printf("Enter a number:");
scanf("%d",&num);
for(i=1;i<=num;i++)
{
count=0;
if(i==1)
{
continue;
}
for(j=2;j<=i/2;j++)
{
if(i%j==0)
{
count++;
break;
}
}
if(count==0)
{
sum=sum+i;
}
}
printf("Sum of all prime numbers from 1 to %d is:%d\n",num,sum);
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("\nThread execution completed.\n");
pthread_mutex_destroy(&mtx);
return 0;
}
```
##48.Write a C program to create a thread that calculates the area of a circle using a given 
radius?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
float r,pie=3.14159;
printf("Enter  radius:");
scanf("%f",&r);
float area=pie*r*r;
printf("Area of circul:%.2f\n",area);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##50.Develop a C program to create a thread that calculates the average of a given array of 
floating-point numbers?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int n;
float a[100],sum=0.00,avg;
printf("Enter  n:");
scanf("%d",&n);
printf("Enter elements:");
for(int i=0;i<n;i++)
{
scanf("%f",&a[i]);
sum=sum+a[i];
}
avg=sum/n;
printf("Average of array elements:%.2f\n",avg);
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##51.Implement a C program to create a thread that prints the factors of a given number? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int num,i;
printf("Enter a number:");
scanf("%d",&num);
printf("Factors of %d are:",num);
for(i=1;i<=num;i++)
{
if(num%i==0)
{
printf("%d ",i);
}
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("\nThread execution completed.\n");
return 0;
}
```
##52.Develop a C program to create a thread that prints the English alphabet in uppercase? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
printf("Tread execution strated.\n");
int i;
for(i=65;i<=90;i++)
{
printf("%c ",i);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("\nThread execution completed.\n");
return 0;
}                                                                                                                                    
```
##53.4.Implement a C program to create a thread that checks if a given number is divisible by 
another given number? 
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int num1,num2;
printf("Enter first number:");
scanf("%d",&num1);
printf("Enter second number:");
scanf("%d",&num2);
if(num1%num2==0)
{
printf("%d is divisiable by %d.\n",num1,num2);
}
else
{
printf("%d is not divisiable by %d.\n",num1,num2);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##54.Develop a C program to create a thread that prints the multiplication table of a given 
number up to a given limit?
```c
#include<stdio.h>
#include<pthread.h>
void*thread1(void*arg)
{
int n,limit,i;
printf("Enter a number:");
scanf("%d",&n);
printf("Enter a limit:");
scanf("%d",&limit);
printf("Multiplication of a table :%d\n",n);
for(i=1;i<=limit;i++)
{
printf("%dX%d=%d\n",n,i,n*i);
}
return NULL;
}
int main()
{
pthread_t th1;
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
printf("Thread execution completed.\n");
return 0;
}
```
##55.Develop a C program to create a thread that prints numbers from 10 to 1 in descending order 
using mutex locks?
```c
#include<stdio.h>
#include<pthread.h>
pthread_mutex_t mtx;
void*thread1(void*arg)
{
pthread_mutex_lock(&mtx);
int i;
printf("Thread strarting to print numbers  in desending order.\n");
for(i=10;i>=1;i--)
{
printf("%d\n",i);
}
pthread_mutex_unlock(&mtx);
return NULL;
}
int main()
{
pthread_t th1;
pthread_mutex_init(&mtx,NULL);
pthread_create(&th1,NULL,thread1,NULL);
pthread_join(th1,NULL);
pthread_mutex_destroy(&mtx);
printf("Thread execution completed.\n");
return 0;
}
```











