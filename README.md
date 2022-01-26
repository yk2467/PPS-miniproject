# PPS-miniproject
Library Management
#include"stdio.h" 
#include"stdlib.h" 
#include"string.h" 
#include"conio.h" 
#define Pquantity 3 
#define MAX 1000 
#define N 5 
int k=0; 
 /* Structural type */ 
typedef struct 
{ int num;/* Serial number */ 
 char name[20];/* Title: */ 
 char author[20];/* The author */ 
 char press[20];/* Press. */ 
 float price;/* The price */ 
 int quantity;/* The number of */ 
 
 
}STUDENTS; 
 
int read_file(STUDENTS stu[]) 
{ FILE *fp; 
 int i=0; 
 if((fp=fopen("stu.txt","rt"))==NULL) 
 {printf("\n\n Stock file does not exist! Please create a "); 
 return 0; 
 } 
 while(feof(fp)!=1) 
 { 
 fread(&stu[i],sizeof(STUDENTS),1,fp); 
 if(stu[i].num==0) 
 break; 
 else 
 i++; 
 } 
 fclose(fp); 
 return i; 
} 
void save_file(STUDENTS stu[],int sum) 
{FILE*fp; 
 int i; 
 if((fp=fopen("stu.txt","wb"))==NULL) 
 {printf(" File writing error !\n"); 
 return; 
 } 
 for(i=0;i<sum;i++) 
 if(fwrite(&stu[i],sizeof(STUDENTS),1,fp)!=1) 
 printf(" File writing error !\n"); 
 fclose(fp); 
} 
 
 
/* Creating book information */ 
int input(STUDENTS stu[]) 
{ int i,x; 
 for(i=0;i<1000;i++) 
 { 
 system("cls"); 
 printf("\n\n    Input book information  ( most %d this )\n",MAX); 
 printf("  ----------------------------\n"); 
 
 printf("\n    The first %d This book ",k+1); 
 printf("\n  Please enter the book number :"); 
 scanf("%d",&stu[k].num); 
 printf("\n  Please enter the title of the book :"); 
 scanf("%s",stu[k].name); 
 printf("\n  Please enter the author of the book :"); 
 scanf("%s",stu[k].author); 
 printf("\n  Please enter the publisher of the book :"); 
 scanf("%s",stu[k].press); 
 printf("\n  Please enter the price of the book :"); 
 scanf("%f",&stu[k++].price); 
 printf("\n  Please enter the number of books :"); 
 scanf("%d",&stu[i].quantity); 
 printf("\n  Please click 1 Key to return to menu or press 0 Key continues to create "); 
 scanf("%d",&x); 
 if(x) 
 break; 
 } 
 
 return k; 
} 
 
 
/* Delete book information */ 
void deletel(STUDENTS stu[]) 
 { system("cls"); 
 char Stuname2[20]; 
 int i,j; 
 printf(" Please enter the title of the book: "); 
 scanf("%s",Stuname2); 
 printf("\n"); 
 for(i=0;i<k;i++) 
 if(strcmp(stu[i].name,Stuname2)==0) 
 for(j=0;j<20;j++) 
 stu[i].name[j]=stu[i+1].name[j]; 
 k--; 
 
 
 printf(" Delete the success \n"); 
 printf(" Press any key to return to the main menu !"); 
 scanf("%d",&i); 
 getchar(); 
} 
 
/* Print book information */                                
void output(STUDENTS stu[]) 
{ system("cls"); 
 int i; 
 for(i=0;i<k;i++) 
 printf(" No. : %d, Title: %s, The author: %s, Press: %s, The price : %.2f, Quantity: %d\n",stu[i].num,stu[i].name, 
 stu[i].author,stu[i].press,stu[i].price,stu[i].quantity); 
 printf(" Press any key to return to the main menu !"); 
 scanf("%d",&i); 
 getchar(); 
} 
 
/* Search for book information */ 
void inquire(STUDENTS stu[]) 
 { int i; 
 char name[20]; 
 system("cls"); 
 printf(" \n\n Please enter the title of the book you are looking for: "); 
 scanf("%s",&name); 
 for(i=0;i<k;i++) 
 if(strcmp(name,stu[i].name)==0) 
  printf("\n\n\n No. : %d, Title: %s, The author: %s, Press: %s, The price : %.2f, Quantity: %d\n",stu[i].num,stu[i].name, 
 stu[i].author,stu[i].press,stu[i].price,stu[i].quantity); 
 printf(" Press any key to return to the main menu !"); 
 scanf("%d",&i); 
 getchar(); 
 } 
 
 
/* Modify book information */ 
void change(STUDENTS stu[]) 
 { int num,i,choice; 
 system("cls"); 
 printf("\n\n\n  Please enter the number of the book you want to modify "); 
 scanf("%d",&num); 
 for(i=0;i<k;i++) 
 { if(num==stu[i].num) 
  printf("\n No. : %d, Title: %s, The author: %s, Press: %s, The price : %.2f, Quantity: %d\n",stu[i].num,stu[i].name, 
 stu[i].author,stu[i].press,stu[i].price,stu[i].quantity); 
 
 printf("\n\n\n ******** Please enter the data you want to modify ********\n\n"); 
 printf("  1.  Serial number \n\n"); 
 printf("  2.  Title: \n\n"); 
 printf("  3.  The author \n\n"); 
 printf("  4.  Press. \n\n"); 
 printf("  5.  The price \n\n"); 
 printf("  6.  The number of \n\n"); 
 printf("    Please select ( 1-6 ) :"); 
 scanf("%d",&choice); 
 switch(choice) 
 {case 1:{ 
  printf("\n  Please enter the new number you changed "); 
  scanf("%d",&stu[i].num); 
  break; 
  } 
 case 2:{ 
  printf("\n  Please enter your new title "); 
  scanf("%s",stu[i].name); 
  break; 
 } 
 case 3:{ 
  printf("\n  Please enter your new author "); 
  scanf("%s",stu[i].author); 
  break; 
 } 
 case 4:{ 
  printf("\n  Please enter your new publisher "); 
  scanf("%s",stu[i].press); 
  break; 
 } 
 case 5:{ 
  printf("\n  Please enter your revised price "); 
  scanf("%f",&stu[i].price); 
  break; 
 case 6:{ 
  printf("\n  Please enter the new quantity you modified "); 
  scanf("%d",&stu[i].quantity); 
  break; 
 } 
 } 
 } 
 
 printf(" No. : %d, Title: %s, The author: %s, Press: %s, The price : %.2f, Quantity: %d\n",stu[i].num,stu[i].name, 
 stu[i].author,stu[i].press,stu[i].price,stu[i].quantity); 
 printf(" Press any key to return to the main menu !"); 
 scanf("%d",&i); 
 break; 
 } 
} 
 
 
/* Book price information ranking */ 
void sort(STUDENTS stu[]) 
 { int i,j,n=1,x; 
 system("cls"); 
 int t; 
 for(i=0;i<k-1;i++) 
 for(j=i+1;j<k;j++) 
 if(stu[i].price<stu[j].price) 
 { t=stu[i].price; 
 stu[i].price=stu[j].price; 
 stu[j].price=t; 
  t=stu[i].num; 
 stu[i].num=stu[j].num; 
 stu[j].num=t; 
 
 } 
 for(i=0;i<k;i++) 
 printf(" ranking   Serial number   The price \n %d %d %.2f\n",n++,stu[i].num,stu[i].price); 
 printf(" Press any key to return to the main menu !"); 
 scanf("%d",&x); 
 getchar(); 
 } 
 
void pquantitydis() 
{ 
 printf(" \n\n\n   **********************************\n"); 
 printf("   *    *\n"); 
 printf("   *    *\n"); 
 printf("   *    *\n"); 
 printf("   *  Welcome to the book information management system  *\n"); 
 printf("   *    *\n"); 
 printf("   *    *\n"); 
 printf("   *    *\n"); 
 printf("   **********************************\n"); 
 
} 
void check() 
{ 
 char userName[5];/* The user name */ 
 char userPWD[5];/* password */ 
 int i,sum; 
 system("color 0B"); 
 for(i = 1; i < 4; i++) 
 { 
 /* The username and password are both abcde;*/ 
 printf("    ( The username and password are both 1)\n\n"); 
 printf("\n  Please enter your user name :"); 
 gets(userName); 
  
 printf("\n  Please enter your password :"); 
 gets(userPWD); 
  
 if ((strcmp(userName,"1")==0) && (strcmp(userPWD,"1")==0))/* Verify the username and password */ 
 { 
  printf("\n   * The user name and password are correct, and the main menu is displayed *"); 
  return; 
 } 
 else 
 { 
  if (i < 3) 
  { 
  printf(" User name or password error, prompt user to enter again "); 
  printf(" The user name or password is wrong. Please enter it again !"); 
  } 
  else 
  { 
  printf(" continuous 3 Enter the wrong user name or password the second time and exit the system. "); 
  printf(" You have been 3 If the user name or password is incorrectly entered this time, the system will exit !"); 
  exit(1); 
  } 
 } 
 } 
} 
void menu() 
{ 
 STUDENTS stu[20]; 
 int choice,k,sum; 
 sum=read_file(stu); 
 if(sum==0) 
 { printf(" First input basic inventory information! Press enter to enter -- \n"); 
 getch(); 
 sum=input(stu); 
 } 
 
 do 
 { system("cls"); 
 printf("\n\n\n  ******** Book information management system ********\n\n"); 
 printf("   1.  Creating book information \n\n"); 
 printf("   2.  Print book information \n\n"); 
 printf("   3.  Search for book information \n\n"); 
 printf("   4.  Modify book information \n\n"); 
 printf("   5.  Delete book information \n\n"); 
 printf("   6.  Book price information ranking \n\n"); 
 printf("   0.  Log out \n\n"); 
 printf("    Please select ( 0-6 ) :"); 
 scanf("%d",&choice); 
 switch(choice) 
 { 
 case 1: k=input(stu); break;/* Creating book information */ 
 case 2: output( stu) ; break;/* Print book information */ 
 case 3: inquire(stu); break;/* Search for book information */ 
 case 4: change(stu); break;/* Modify book information */ 
 case 5: deletel(stu); break;/* Delete book information */ 
 case 6: sort(stu); break;/* Book price information ranking */ 
 case 0: break; 
 } 
 }while(choice!=0); 
 save_file(stu,sum); 
} 
int main() 
{ 
 int i,sum; 
 pquantitydis(); 
 check(); 
 menu(); 
} 
