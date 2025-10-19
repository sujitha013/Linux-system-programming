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
  GNU nano 7.2                                                                  thread_new.c *                                                                          #include<stdio.h>
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
##23.Write a C program to create a thread that generates a random array of integers? 
```c


