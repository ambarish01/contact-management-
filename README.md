
#include<stdio.h>
#include<conio.h>
#include<string.h>
#define tab printf("\t\t\t")
struct list{
char name[20];
char phone[20];
char email[30];
char address[20];
}li,check;
void createcontact(){
FILE *fp;
fp = fopen("contact.txt","a+");
system("cls");
tab; printf("========================\n");
tab; printf(" NEW CONTACT \n");
tab; printf("========================\n");
tab; printf("Input name : "); fflush(stdin); gets(li.name);
tab;printf("Input phone : "); fflush(stdin); gets(li.phone);
tab; printf("Input address : "); fflush(stdin); gets(li.address);
tab; printf("Input Email : "); fflush(stdin); gets(li.email);
fprintf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email);
fclose(fp);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
}
void editcontact(){
int ch,f=0;
FILE *fp,*newrec;
fp = fopen("contact.txt","r");
newrec = fopen("temp.txt","w");
system("cls");
tab; printf("========================\n");
tab; printf(" EDIT CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmp(check.name,li.name) == 0){
f=1;
do{
system("cls");
tab; printf("========================\n");
tab; printf(" EDIT CONTACT \n");
tab; printf("========================\n");
tab; printf("What you want to edit\n");
tab; printf("1.Name\n");
tab; printf("2.Phone\n");
tab; printf("3.Address\n");
tab; printf("4.Email\n");
tab; printf("0.Back\n");
tab; printf("========================\n");
tab; printf(" Enter option : "); scanf("%d",&ch);
switch(ch){
case 1:
tab; printf("Enter new name : "); fflush(stdin);
gets(li.name);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 2:
tab;printf("Enter new phone : "); fflush(stdin);
gets(li.phone);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 3:
tab; printf("Enter new address : "); fflush(stdin);
gets(li.address);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 4:
tab; printf("Enter new Email : "); fflush(stdin);
gets(li.email);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 0:
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
break;
}
}while(ch != 0);
}
else{
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
}
}
fclose(fp);
fclose(newrec);
remove("contact.txt");
rename("temp.txt","contact.txt");
if(f == 0){
printf("Cannot found the name\n\n");
system("pause");
}
}
void searchcontact(){
int f=0;
FILE *fp;
fp = fopen("contact.txt","r");
system("cls");
tab; printf("========================\n");
tab; printf(" SEARCH CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmpi(check.name,li.name)==0){
f=1;
tab; printf("Name : %s\n",li.name);
tab; printf("Phone : %s\n",li.phone);
tab; printf("Address : %s\n",li.address);
tab; printf("Email : %s\n",li.email);
system("pause");
break;
}
}
fclose(fp);
if(f == 0){
printf("Cannot found the name\n\n");
system("pause");
}
}
void listcontact(){
int f=0;
FILE *fp;
fp = fopen("contact.txt","r");
system("cls");
tab; printf("========================\n");
tab; printf(" LIST CONTACT \n");
tab; printf("========================\n\n\n");
tab;
printf("%-10s%-10s%-10s%-10s\n","NAME","PHONE","ADDRESS","EMAIL");
tab; printf("===================================================\n");
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
f=1;
tab;
printf("%-10s%-10s%-10s%-10s\n",li.name,li.phone,li.address,li.email);
}
fclose(fp);
if(f == 0){
printf("No Record Contact\n\n");
system("pause");
}
system("pause");
}
void deletecontact(){
int ch,f=0;
FILE *fp,*newrec;
fp = fopen("contact.txt","r");
newrec = fopen("temp.txt","w");
system("cls");
tab; printf("========================\n");
tab; printf(" DELETE CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmpi(check.name,li.name) == 0){
f=1;
}
else{
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
}
}
fclose(fp);
fclose(newrec);
remove("contact.txt");
rename("temp.txt","contact.txt");
if(f == 0){
tab; printf("Cannot found the name\n\n");
system("pause");
}
else{
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
}
}
void main(){
int ch;
do{
system("cls");
tab; printf("========================\n");
tab; printf(" MAIN MENU\n");
tab; printf("========================\n");
tab; printf("1.Create new contact\n");
tab; printf("2.Edit contact\n");
tab; printf("3.Search contact\n");
tab;printf("4.List contact\n");
tab; printf("5.Delete contact\n");
tab; printf("0.Exit\n");
tab; printf("========================\n");
tab; printf(" Enter option : "); scanf("%d",&ch);
switch(ch){
case 1: createcontact(); break;
case 2: editcontact(); break;
case 3: searchcontact(); break;
case 4: listcontact(); break;
case 5: deletecontact(); break;
}
}while( ch !=0);
}
#include<stdio.h>
#include<conio.h>
#include<string.h>
#define tab printf("\t\t\t")
struct list{
char name[20];
char phone[20];
char email[30];
char address[20];
}li,check;
void createcontact(){
FILE *fp;
fp = fopen("contact.txt","a+");
system("cls");
tab; printf("========================\n");
tab; printf(" NEW CONTACT \n");
tab; printf("========================\n");
tab; printf("Input name : "); fflush(stdin); gets(li.name);
tab;printf("Input phone : "); fflush(stdin); gets(li.phone);
tab; printf("Input address : "); fflush(stdin); gets(li.address);
tab; printf("Input Email : "); fflush(stdin); gets(li.email);
fprintf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email);
fclose(fp);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
}
void editcontact(){
int ch,f=0;
FILE *fp,*newrec;
fp = fopen("contact.txt","r");
newrec = fopen("temp.txt","w");
system("cls");
tab; printf("========================\n");
tab; printf(" EDIT CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmp(check.name,li.name) == 0){
f=1;
do{
system("cls");
tab; printf("========================\n");
tab; printf(" EDIT CONTACT \n");
tab; printf("========================\n");
tab; printf("What you want to edit\n");
tab; printf("1.Name\n");
tab; printf("2.Phone\n");
tab; printf("3.Address\n");
tab; printf("4.Email\n");
tab; printf("0.Back\n");
tab; printf("========================\n");
tab; printf(" Enter option : "); scanf("%d",&ch);
switch(ch){
case 1:
tab; printf("Enter new name : "); fflush(stdin);
gets(li.name);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 2:
tab;printf("Enter new phone : "); fflush(stdin);
gets(li.phone);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 3:
tab; printf("Enter new address : "); fflush(stdin);
gets(li.address);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 4:
tab; printf("Enter new Email : "); fflush(stdin);
gets(li.email);
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
break;
case 0:
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
break;
}
}while(ch != 0);
}
else{
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
}
}
fclose(fp);
fclose(newrec);
remove("contact.txt");
rename("temp.txt","contact.txt");
if(f == 0){
printf("Cannot found the name\n\n");
system("pause");
}
}
void searchcontact(){
int f=0;
FILE *fp;
fp = fopen("contact.txt","r");
system("cls");
tab; printf("========================\n");
tab; printf(" SEARCH CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmpi(check.name,li.name)==0){
f=1;
tab; printf("Name : %s\n",li.name);
tab; printf("Phone : %s\n",li.phone);
tab; printf("Address : %s\n",li.address);
tab; printf("Email : %s\n",li.email);
system("pause");
break;
}
}
fclose(fp);
if(f == 0){
printf("Cannot found the name\n\n");
system("pause");
}
}
void listcontact(){
int f=0;
FILE *fp;
fp = fopen("contact.txt","r");
system("cls");
tab; printf("========================\n");
tab; printf(" LIST CONTACT \n");
tab; printf("========================\n\n\n");
tab;
printf("%-10s%-10s%-10s%-10s\n","NAME","PHONE","ADDRESS","EMAIL");
tab; printf("===================================================\n");
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
f=1;
tab;
printf("%-10s%-10s%-10s%-10s\n",li.name,li.phone,li.address,li.email);
}
fclose(fp);
if(f == 0){
printf("No Record Contact\n\n");
system("pause");
}
system("pause");
}
void deletecontact(){
int ch,f=0;
FILE *fp,*newrec;
fp = fopen("contact.txt","r");
newrec = fopen("temp.txt","w");
system("cls");
tab; printf("========================\n");
tab; printf(" DELETE CONTACT \n");
tab; printf("========================\n");
tab; printf("Enter name : "); fflush(stdin); gets(check.name);
while(fscanf(fp,"%s %s %s %s\n",li.name,li.phone,li.address,li.email)
!= EOF)
{
if(strcmpi(check.name,li.name) == 0){
f=1;
}
else{
fprintf(newrec,"%s %s %s
%s\n",li.name,li.phone,li.address,li.email);
}
}
fclose(fp);
fclose(newrec);
remove("contact.txt");
rename("temp.txt","contact.txt");
if(f == 0){
tab; printf("Cannot found the name\n\n");
system("pause");
}
else{
tab; printf("=====SUCCESSFUL=====\n\n");
system("pause");
}
}
void main(){
int ch;
do{
system("cls");
tab; printf("========================\n");
tab; printf(" MAIN MENU\n");
tab; printf("========================\n");
tab; printf("1.Create new contact\n");
tab; printf("2.Edit contact\n");
tab; printf("3.Search contact\n");
tab;printf("4.List contact\n");
tab; printf("5.Delete contact\n");
tab; printf("0.Exit\n");
tab; printf("========================\n");
tab; printf(" Enter option : "); scanf("%d",&ch);
switch(ch){
case 1: createcontact(); break;
case 2: editcontact(); break;
case 3: searchcontact(); break;
case 4: listcontact(); break;
case 5: deletecontact(); break;
}
}while( ch !=0);
}
