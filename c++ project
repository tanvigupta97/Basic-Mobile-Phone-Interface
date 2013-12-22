#include<iostream.h>
#include<stdio.h>
#include<fstream.h>
#include<string.h>
#include<conio.h>
#include<iomanip.h>
#include<process.h>

void menu(void);
void box(void);
void organiser(void);
void createnotes(void);
void viewnotes(void);
void addmore(void);
void notes(void);
void phone(void);
void dial(void);
void numberpad(void);
void calllog(void);
void contacts(void);
void addcontc(void);
void searchcontc(void);
void viewcontc(void);
void deletecontc(void);
void modifycontc(void);
float calc(float x,float y,char a);

class contact
{
private:
char name[30];
long int phno;
public:
contact()
{
strcpy(name,"Unknown");
phno=0;
}
contact(long int a)
{
strcpy(name,"Unknown");
phno=a;
}
void enter()
{
cout<<"\n\n\t\t\tEnter contact name ";
gets(name);
cout<<"\n\n\t\t\tEnter contact's phone number ";
cin>>phno;
}
void display()
{
cout<<"\n\t\t\tContact name "<<name;
cout<<"\n\t\t\tPhone number "<<phno;
}
char *returnname()
{
return(name);
}
};

void menu()
{
clrscr();
cout<<"\n\n\n\n\t\t\t_______Main Menu_______";
cout<<"\n\n\t\t\t1. Phone";
cout<<"\n\n\t\t\t2. Contacts";
cout<<"\n\n\t\t\t3. Organiser";
cout<<"\n\n\t\t\t4. Switch Off";
int ch;
cout<<"\n\n\nEnter your choice ";
cin>>ch;
switch(ch)
{
case 1:
clrscr();
phone();
break;
case 2:
clrscr();
contacts();
break;
case 3:
clrscr();
organiser();
break;
case 4:
exit(1);
break;
}
}

void contacts()
{
clrscr();
cout<<"\n\n\n\n\t\t\t_______CONTACTS_______";
cout<<"\n\n\t\t1. Add Contact";
cout<<"\n\n\t\t2. Search contact";
cout<<"\n\n\t\t3. View contact";
cout<<"\n\n\t\t4. Delete contact";
cout<<"\n\n\t\t5. Modify contact";
cout<<"\n\n\t\t6. Back to Menu";
int ch;
cout<<"\n\n\nEnter your choice ";
cin>>ch;
switch(ch)
{ 
case 1:
clrscr();
addcontc();
break;
case 2:
clrscr();
searchcontc();
break;
case 3:
clrscr();
viewcontc();
break;
case 4:
clrscr();
deletecontc();
break;
case 5:
clrscr();
modifycontc();
break;
case 6:
clrscr();
menu();
break;
}
}

void addcontc()
{
contact c;
fstream fout;
fout.open("CONTACTS.DAT",ios::app|ios::binary);
c.enter();
fout.write((char*)&c,sizeof(c));
fout.close();
contacts();
}

void searchcontc()
{
contact c;
char ch='n';
char n[30];
cout<<"\n\n\nEnter the name to be searched";
gets(n);
fstream fin;
fin.open("CONTACTS.DAT",ios::in|ios::binary);
fin.read((char*)&c,sizeof(c));
while(fin)
{
if(strcmpi(c.returnname(),n)==0)
{
c.display();
ch='y';
break;
}
fin.read((char*)&c,sizeof(c));
}
if(ch=='n')
cout<<"\n\n\nContact Not Found";
cout<<"\n\t\tPress any key and Enter to return to contacts ";
cin>>ch;
fin.close();
contacts();
}

void viewcontc()
{
contact c;
fstream fin;
fin.open("CONTACTS.DAT",ios::in|ios::binary);
fin.read((char*)&c,sizeof(c));
int i=1;
while(fin)
{
cout<<i<<".\n";
c.display();
cout<<"\n";
fin.read((char*)&c,sizeof(c));
i++;
}
fin.close();
char ch='n';
cout<<"\nDo you want to modify any contacts(N or Y) ";
cin>>ch;
if(ch=='y'||ch=='Y')
modifycontc();
else
contacts();
}

void modifycontc()
{
contact c;
fstream f;
f.open("CONTACTS.DAT",ios::in|ios::out|ios::binary);
char n[30];
cout<<"\nEnter the name to be searched";
gets(n);
long int pos;
char ch='n';
pos=f.tellg();
f.read((char*)&c,sizeof(c));
while(f)
{
if(strcmpi(c.returnname(),n)==0)
{
cout<<"\nEnter new details";
c.enter();
f.seekp(pos,ios::beg);
f.write((char*)&c,sizeof(c));
ch='y';
}
pos=f.tellg();
f.read((char*)&c,sizeof(c));
}
f.close();
if(ch=='n')
cout<<"\nContact not found";
cout<<"\n\t\tPress any key and Enter to return to contacts ";
cin>>ch;
contacts();
}

void deletecontc()
{
contact c;
fstream fin,fout;
fin.open("CONTACTS.DAT",ios::in|ios::binary);
fout.open("TEMP.DAT",ios::out|ios::binary);
char n[30],ch='n';
cout<<"\nEnter the name to be deleted";
gets(n);
fin.read((char*)&c,sizeof(c));
while(fin)
{
if(strcmpi(c.returnname(),n)==0)
{
cout<<"\nDeleted!";
ch='y';
}
else
fout.write((char*)&c,sizeof(c));
fin.read((char*)&c,sizeof(c));
}
fin.close();
fout.close();
if(ch=='n')
cout<<"\nContact not found";
remove("CONTACTS.DAT");
rename("TEMP.DAT","CONTACTS.DAT");
cout<<"\n\t\tPress any key and Enter to return to contacts ";
cin>>ch;
contacts();
}

void numberpad()
{
clrscr();
cout<<"     *------------------------------------------*";
cout<<"\n     |                                          |";
cout<<"\n     |                                          |";
cout<<"\n     |                                          |";
cout<<"\n     *------------------------------------------*";
cout<<"\n\n\n\t";
for(int i=1;i<=7;i+=3)
{
cout<<"*---*\t\t*---*\t\t*---*";cout<<"\n\t";
cout<<"| "<<i<<" |\t\t| "<<(i+1)<<" |\t\t| "<<(i+2)<<" |";cout<<"\n\t";
cout<<"*---*\t\t*---*\t\t*---*";cout<<"\n\n\t";
}
cout<<"\t\t*---*\n";
cout<<"\t\t\t| 0 |\n";
cout<<"\t\t\t*---*";
}

void calllog()
{
fstream fin;
contact ob;
int i=1;
fin.open("LOG.DAT", ios::in|ios::binary);
cout<<
"\n\t\t\t_______CALL LOG_______\n\n";
fin.read( (char*)&ob, sizeof(ob));
while(fin)
{
cout<<"\n\t\t"<<i<<'.';
ob.display();
cout<<"\n";
fin.read( (char*)&ob, sizeof(ob));
++i;
}
fin.close();
cout<<"\n\t\tPress any key and Enter to return to phone ";
char ch;
cin>>ch;
phone();
}

void dial()
{ 
clrscr();
long int num;
clrscr();
numberpad();
cout<<"\n\n\n\t\t\tEnter number to call\n";
cin>>num;
contact c(num);
clrscr;
cout<<"\n\n";
cout<<setw(45)<<num;
cout<<"\n";
cout<<setw(45)<<"CALLING";
double a;
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<'.';
fstream f;
f.open("LOG.DAT", ios::out|ios::app|ios::binary);
f.write((char*)&c,sizeof(c));
f.close();
calllog();
}

void phone()
{
clrscr();
int c;
cout<<"\n\n\n\t\t\t________PHONE_______";
cout<<"\n\t\t1. Dial Pad";
cout<<"\n\t\t2. Call Log";
cout<<"\n\t\t3. Contacts";
cout<<"\n\t\t4. Back to menu";
cout<<"\n\nEnter your choice";
cin>>c;
switch(c)
{
 case 1:
clrscr();
dial();
break;
 case 2: 
clrscr();
calllog();
break;
 case 3: 
clrscr();
contacts();
break;
 	case 4: 
clrscr();
menu();
break;
}
}

void createnotes()
{
ofstream fout;
char ch='y';
fout.open("NOTE.dat",ios::out|ios::binary);
char line[225];
while(ch=='y'||ch=='Y')
{
cout<<"\nEnter your sentence";
gets(line);
fout<<line<<"\n";
cout<<"\nDo you want to add more?(N or Y) ";
cin>>ch;
}
fout.close();
clrscr();
notes();
}

void viewnotes()
{
int ch;
ifstream fin;
fin.open("NOTE.dat",ios::binary|ios::in);
char line[225];
fin.getline(line,225);
while(fin)
{
cout<<line<<" ";
fin.getline(line,225);
}
fin.close();
cout<<"\n1.Do you wish to add more to this note ";
cout<<"\n2.Back to notes";
cout<<"\nEnter your choice ";
cin>>ch;
switch(ch)
{
case 1:
clrscr();
addmore();
break;
case 2:
clrscr();
notes();
break;
}
}

void addmore()
{ 
ofstream fout;
fout.open("NOTE.dat",ios::app|ios::binary);
char ch='y';
char line[225];
while(ch=='y'||ch=='Y')
{
cout<<"\nEnter your sentence";
gets(line);
fout<<line<<"\n";
cout<<"\nDo you want to add more?(N or Y) ";
cin>>ch;
}
fout.close();
clrscr();
notes();
}

void notes()
{
int ch;
cout<<"\n\n\t\t\t________NOTES_______";
cout<<"\n\t\t1. Create a new note";
cout<<"\n\t\t2. View existing note";
cout<<"\n\t\t3. Back to organiser";
cout<<"\n\nEnter your choice ";
cin>>ch;
switch(ch)
{
case 1:
clrscr();
createnotes();
break;
case 2:
clrscr();
viewnotes();
break;
	case 3:
clrscr();
organiser();
break;
}
}

void box()
{
char ch='y';
do
{
cout<<"\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\t\t\t| c |\t|+/-|\t| / |\t| * |\t\n";
cout<<" \t\t\t--- \t --- \t --- \t --- \t\n ";
cout<<"\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\t\t\t| 7 |\t| 8 |\t| 9 |\t| - |\t\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\t\t\t| 4 |\t| 5 |\t| 6 |\t| + |\t\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\t\t\t| 1 |\t| 2 |\t| 3 |\t|   |\t\n";
cout<<"\t\t\t --- \t --- \t --- \t|   | \t\n ";
cout<<"\t\t\t     \t     \t     \t|   | \t\n ";
cout<<"\t\t\t --- \t --- \t --- \t|   | \t\n ";
cout<<"\t\t\t| 0 |\t|   |\t| . |\t| = |\t\n";
cout<<"\t\t\t --- \t --- \t --- \t --- \t\n ";
cout<<"\n Enter First number ";
float a,b,ans;
char fun;
cin>>a;
cout<<"\nEnter second number";
cin>>b;
cout<<"\nEnter the function(*,/,+/-)";
cin>>fun;
ans=calc(a,b,fun);
cout.setf(ios::showpos);
cout<<a<<" "<<fun<<b<<" = "<<setprecision(7)<<ans;
cout<<"\nDo you want to continue?(N or Y)";
cin>>ch;
clrscr();
}
while(ch=='y'||ch=='Y');
if(ch=='n')
clrscr();
organiser();

}
float calc(float x,float y,char a)
{
float sol;
switch(a)
{
case '+':
 sol=x+y;
 return(sol);
 break;
  	case '-':
sol=x-y;
return(sol);
break;
case '*':
sol=x*y;
return(sol);
break;
case '/':
sol=x/y;
return(sol);
break;
}
}

void organiser()
{
clrscr();
int ch;
cout<<"\n\n\n\t\t\t________ORGANISER________";
cout<<"\n\t\t1.Notes";
cout<<"\n\t\t2.Calculator";
cout<<"\n\t\t3.Back to menu";
cout<<"\n\nEnter your choice ";
cin>>ch;
switch(ch)
{
case 1:
clrscr();
notes();
break;
case 2:
clrscr();
box();
break;
case 3:
clrscr();
menu();
break;
}
}


void main()
{
double a;
cout<<"\n\n\n\n\n\n\t\t I N I T I A L I S I N G.";
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++); 
cout<<'.';
for(a=0;a<10239467;a++);
clrscr();
cout<<"\n\n\n\n\n\n\t\t\t\tWELCOME TO “;
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<"\n\t\t\t\tAMIGA T2A";
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
cout<<"\n\n\n\t\t\tREDEFINING MOBILE EXPERIENCE ";
for(a=0;a<10239417;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
for(a=0;a<10239467;a++);
clrscr();
fstream fout1,fout2;
fout1.open("CONTACTS.DAT",ios::out|ios::binary);
fout1.close();
fout2.open("LOG.DAT",ios::out|ios::binary);
fout2.close();
menu();
}
