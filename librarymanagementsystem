#include<windows.h>
#include<stdio.h>
#include<conio.h>
#include <stdlib.h>
#include<string.h>                  //contains strcmp(),strcpy(),strlen(),etc
#include<ctype.h>                   //contains toupper(), tolower(),etc
#include<dos.h>                     //contains _dos_getdate
#include<time.h>
//#include<bios.h>
#define RETURNTIME 15
void gotoxy(int x,int y){

}


char catagories[][15]={"Computer","Electronics","Electrical","Civil","Mechnnical"};
void returnfunc();
void mainmenu();
void addbooks();
void deletebooks();
void editbooks();
void searchbooks();
void issuebooks();
void viewbooks();
void closeapplication();
int  getdata();
int  checkid(int);
int t(v);
//void show_mouse(void);
void Password();
void issuerecord();
void loaderanim();

//list of global files that can be acceed form anywhere in program
FILE *fp,*ft,*fs;


int s;
char findbook;
char password[10]={"codewithc"};


struct meroDate
{
    int mm,dd,yy;
};


struct books
{
    int id;
    char stname[20];
    char name[20];
    int rno;
    char year[10];
    char Author[20];
    int quantity;
    float Price;
    int count;
    int rackno;
    char *cat;
    struct meroDate issued;
    struct meroDate duedate;
};


struct books a;



void mainmenu()
{
    int i;
    printf("MAIN MENU");
    printf("\n1. Add Books   ");
    printf("\n2. Delete books");
    printf("\n3. Search Books");
    printf("\n4. Issue Books");
    printf("\n5. View Book list");
    printf("\n6. Edit Book's Record");
    printf("\n7. Close Application");
    printf("\nEnter your choice:");
    switch(getch())
    {
        case '1':
        addbooks();
        break;
        case '2':
        deletebooks();
        break;
        case '3':
        searchbooks();
        break;
        case '4':
        issuebooks();
        break;
        case '5':
        viewbooks();
        break;
        case '6':
        editbooks();
        break;
        case '7':
        {
        exit(0);
    }
    default:
    {

    printf("\n\aWrong Entry!!Please re-entered correct option");
    if(getch())
    mainmenu();
    }

    }
}

void addbooks()    //funtion that add books
{
    system("cls");
    int i;
    printf("\nSELECT CATEGORIES");
    printf("\n1. Computer");
    printf("\n2. Electronics");
    printf("\n3. Electrical");
    printf("\n4. Civil");
    printf("\n5. Mechanical");
    //printf("\n6. Architecture");
    printf("\n6. Back to main menu");
    printf("\nEnter your choice:");
    scanf("%d",&s);
    if(s==6)

    mainmenu() ;
    system("cls");
    fp=fopen("Library.dat","ab+");
    if(getdata()==1)
    {
    a.cat=catagories[s-1];
    fseek(fp,0,SEEK_END);
    fwrite(&a,sizeof(a),1,fp);
    fclose(fp);

    printf("\nThe record is sucessfully saved");
    printf("\nSave any more?(Y / N):");
    if(getch()=='N')
    mainmenu();
    else
    system("cls");
    addbooks();
    }
}
void deletebooks()    //function that delete items from file fp
{
    system("cls");
    int d;
    char another='y';
    while(another=='y')  //infinite loop
    {
    system("cls");
    printf("\nEnter the Book ID to  delete:");
    scanf("%d",&d);
    fp=fopen("Library.dat","rb+");
    rewind(fp);
    while(fread(&a,sizeof(a),1,fp)==1)
    {
    if(a.id==d)
    {
    printf("\nThe book record is available");
    printf("\nBook name is %s",a.name);
    printf("\nRack No. is %d",a.rackno);
    findbook='t';
    }
}
if(findbook!='t')
{

    printf("\nNo record is found modify the search");
    if(getch())
    mainmenu();
}
if(findbook=='t' )
{
    printf("\nDo you want to delete it?(Y/N):");
    if(getch()=='y')
{
    ft=fopen("test.dat","wb+");  //temporary file for delete
    rewind(fp);
    while(fread(&a,sizeof(a),1,fp)==1)
{
if(a.id!=d)
{
    fseek(ft,0,SEEK_CUR);
    fwrite(&a,sizeof(a),1,ft); //write all in tempory file except that
}                              //we want to delete
}
    fclose(ft);
    fclose(fp);
    remove("Library.dat");
    rename("test.dat","Library.dat"); //copy all item from temporary file to fp except that
    fp=fopen("Library.dat","rb+");    //we want to delete
    if(findbook=='t')
    {
    printf("\nThe record is sucessfully deleted");
    printf("\nDelete another record?(Y/N)");
    }
}
else
mainmenu();
fflush(stdin);
another=getch();
}
}
mainmenu();
}




void searchbooks()
{
    system("cls");
    int d;
    printf("*****************************Search Books*********************************");
    printf("\n 1. Search By ID");
    printf("\n 2. Search By Name");
    printf("Enter Your Choice");
    fp=fopen("Library.dat","rb+"); //open file for reading propose
    rewind(fp);   //move pointer at the begining of file
    switch(getch())
    {
    case '1':
    {
        system("cls");
        printf("****Search Books By Id****");
        printf("\nEnter the book id:");
        scanf("%d",&d);

    while(fread(&a,sizeof(a),1,fp)==1)
    {
        if(a.id==d)
        {
            Sleep(2);
            printf("\nThe Book is available");
            printf("\nID:%d",a.id);
            printf("\n Name:%s",a.name);
            printf("\n Author:%s ",a.Author);
            printf("\n Qantity:%d ",a.quantity);
            printf("\n Price:Rs.%.2f",a.Price);
            printf("\n Rack No:%d ",a.rackno);
            printf("\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2");
            findbook='t';
        }

    }
    if(findbook!='t')  //checks whether conditiion enters inside loop or not
    {
        printf("\nNo Record Found");
    }
    printf("Try another search?(Y/N)");
    if(getch()=='y')
    searchbooks();
    else
    mainmenu();
    break;
    }
    case '2':
    {
        char s[15];
        system("cls");
        printf("****Search Books By Name****");
        printf("\nEnter Book Name:");
        scanf("%s",s);
        int d=0;
        while(fread(&a,sizeof(a),1,fp)==1)
        {
            if(strcmp(a.name,(s))==0) //checks whether a.name is equal to s or not
            {
                printf("The Book is available");

                printf("\xB2 ID:%d",a.id);
                printf("\xB2");

                printf("\xB2 Name:%s",a.name);printf("\xB2");

                printf("\xB2 Author:%s",a.Author);
                printf("\xB2");
                printf("\xB2 Qantity:%d",a.quantity);
                //a.quantity--;
                printf("\xB2");
                gotoxy(20,13);
                printf("\xB2 Price:Rs.%.2f",a.Price);gotoxy(47,13);printf("\xB2");
                gotoxy(20,14);
                printf("\xB2 Rack No:%d ",a.rackno);gotoxy(47,14);printf("\xB2");
                gotoxy(20,15);
                printf("\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2");
                d++;
            }




        }
            if(d==0)
            {

            printf("\a\nNo Record Found");
            }
            printf("Try another search?(Y/N)");
            if(getch()=='y')
            searchbooks();
            else
            mainmenu();
            break;
            }
            default :
            getch();
            searchbooks();
            }
            fclose(fp);
}




void issuebooks(void)  //function that issue books from library
{
    int t;

    system("cls");
    printf("********************************ISSUE SECTION**************************");
    printf("\n 1. Issue a Book");
    printf("\n 2. View Issued Book");
    printf("\n 3. Search Issued Book");
    printf("\n 4. Remove Issued Book");
    printf("Enter a Choice:");
    switch(getch())
    {
        case '1':  //issue book
        {
            system("cls");
            int c=0;
            char another='y';
            while(another=='y')
            {
            system("cls");
            printf("\n***Issue Book section***");
            printf("\nEnter the Book Id:");
            scanf("%d",&t);
            fp=fopen("Library.dat","rb");
            fs=fopen("Issue.dat","ab+");
            if(checkid(t)==0) //issues those which are present in library
            {
            printf("\nThe book record is available");
            printf("\nThere are %d unissued books in library ",a.quantity);
            printf("\nThe name of book is %s",a.name);
            printf("\nEnter student name:");
            scanf("%s",a.stname);
            printf("\nEnter the class of student:");
            scanf("%s",a.year);
            printf("\nEnter student Roll no:");
            scanf("%d",&a.rno);

            //struct dosdate_t d; //for current date
            //_dos_getdate(&d);
            //a.issued.dd=d.day;
            //a.issued.mm=d.month;
            //a.issued.yy=d.year;
            printf("\nIssued date=%d-%d-%d",a.issued.dd,a.issued.mm,a.issued.yy);
            printf("\nThe BOOK of ID %d is issued",a.id);
            a.duedate.dd=a.issued.dd+RETURNTIME;   //for return date
            a.duedate.mm=a.issued.mm;
            a.duedate.yy=a.issued.yy;
            if(a.duedate.dd>30)
            {
            a.duedate.mm+=a.duedate.dd/30;
            a.duedate.dd-=30;

            }
            if(a.duedate.mm>12)
            {
            a.duedate.yy+=a.duedate.mm/12;
            a.duedate.mm-=12;

            }
            printf("\nTo be return:%d-%d-%d",a.duedate.dd,a.duedate.mm,a.duedate.yy);
            fseek(fs,sizeof(a),SEEK_END);
            fwrite(&a,sizeof(a),1,fs);
            fclose(fs);
            c=1;
            }
            if(c==0)
            {

            printf("\nNo record found");
            }
            printf("\nIssue any more(Y/N):");
            fflush(stdin);
            another=getche();
            fclose(fp);
            }

            break;
    }
    case '2':  //show issued book list
    {
        system("cls");
        int j=4;
        printf("*******************************Issued book list*******************************\n");
        printf("STUDENT NAME    CATEGORY    ID    BOOK NAME    ISSUED DATE    RETURN DATE");
        fs=fopen("Issue.dat","rb");
        while(fread(&a,sizeof(a),1,fs)==1)
        {

        printf("\n%s",a.stname);
        printf("\n%s",a.cat);
        printf("\n%d",a.id);
        printf("\n%s",a.name);
        printf("\n%d-%d-%d",a.issued.dd,a.issued.mm,a.issued.yy );
        printf("\n%d-%d-%d",a.duedate.dd,a.duedate.mm,a.duedate.yy);
        /*struct d;
        _dos_getdate(&d);

                    printf("Current date=%d-%d-%d",d.day,d.month,d.year);
        j++;*/

        }
        fclose(fs);
        returnfunc();
        break;
        case '3':   //search issued books by id
        {
        system("cls");
        gotoxy(10,6);
        printf("Enter Book ID:");
        int p,c=0;
        char another='y';
        while(another=='y')
        {

            scanf("%d",&p);
            fs=fopen("Issue.dat","rb");
            while(fread(&a,sizeof(a),1,fs)==1)
            {
            if(a.id==p)
            {
            issuerecord();
            printf("Press any key.......");
            getch();
            issuerecord();
            c=1;
            }

            }
            fflush(stdin);
            fclose(fs);
            if(c==0)
            {

            printf("\nNo Record Found");
            }
            printf("\nTry Another Search?(Y/N)");
            another=getch();
        }
        }
        break;
    case '4':  //remove issued books from list
    {
        system("cls");
        int b;
        FILE *fg;  //declaration of temporary file for delete
        char another='y';
        while(another=='y')
        {

        printf("Enter book id to remove:");
        scanf("%d",&b);
        fs=fopen("Issue.dat","rb+");
        while(fread(&a,sizeof(a),1,fs)==1)
        {
        if(a.id==b)
        {
        issuerecord();
        findbook='t';
        }
        if(findbook=='t')
        {

        printf("Do You Want to Remove it?(Y/N)");
        if(getch()=='y')
        {
        fg=fopen("record.dat","wb+");
        rewind(fs);
        while(fread(&a,sizeof(a),1,fs)==1)
        {
        if(a.id!=b)
        {
        fseek(fs,0,SEEK_CUR);
        fwrite(&a,sizeof(a),1,fg);
        }
        }
        fclose(fs);
        fclose(fg);
        remove("Issue.dat");
        rename("record.dat","Issue.dat");
        printf("The issued book is removed from list");

        }

        }
        if(findbook!='t')
        {

        printf("\nNo Record Found");
        }
        }

        printf("\ndelete any more?(Y/N)");
        another=getch();
        }
        }
    default:

    printf("\n\aWrong Entry!!");
    getch();
    issuebooks();
    break;
    }
returnfunc();
}
}



void viewbooks(void)  //show the list of book persists in library
{
    int i=0,j;
    system("cls");
    printf("*********************************Book List*****************************");

    printf("\n CATEGORY     \tID    \tBOOK NAME     AUTHOR           QTY     PRICE     RackNo ");
    j=4;
    fp=fopen("Library.dat","rb");
    while(fread(&a,sizeof(a),1,fp)==1)
    {
    printf("\n%s",a.cat);
    printf("\t%d",a.id);

    printf("\t%s",a.name);
    printf("\t\t%s",a.Author);
    printf("\t\t%d",a.quantity);
    printf("\t%.2f",a.Price);
    printf("\t  %d",a.rackno);
    printf("\t");
    j++;
    i=i+a.quantity;
    }
    printf("\nTotal Books =%d",i);
    fclose(fp);

    returnfunc();
}



void editbooks(void)  //edit information about book
{
    system("cls");
    int c=0;
    int d,e;
    printf("****Edit Books Section****");
    char another='Y';
    while(another=='Y')
    {
        system("cls");

    printf("Enter Book Id to be edited:");
    scanf("%d",&d);
    fp=fopen("Library.dat","rb+");
    while(fread(&a,sizeof(a),1,fp)==1)
    {
    if(checkid(d)==0)
    {

        printf("\nThe book is availble");
        printf("\nThe Book ID:%d",a.id);
        printf("\nEnter new name:");scanf("%s",a.name);
        printf("\nEnter new Author:");scanf("%s",a.Author);
        printf("\nEnter new quantity:");scanf("%d",&a.quantity);
        printf("\nEnter new price:");scanf("%f",&a.Price);
        printf("\nEnter new rackno:");scanf("%d",&a.rackno);
        printf("\nThe record is modified");
        fseek(fp,ftell(fp)-sizeof(a),0);
        fwrite(&a,sizeof(a),1,fp);
        fclose(fp);
        c=1;
    }
    if(c==0)
    {

    printf("No record found");
    }
    }
    printf("Modify another Record?(Y/N)");
    fflush(stdin);
    another=getch();
    }
    returnfunc();
}

void returnfunc()
{
    {
    printf(" Press ENTER to return to main menu");
    }
    a:
    if(getch()==13) //allow only use of enter
    mainmenu();
    else
    goto a;
}


int getdata()
{
    int t;
    printf("\nEnter the Information Below");

    printf("\nCategory:");

    printf("%s",catagories[s-1]);

    printf("\nBook ID:\t");

    scanf("%d",&t);
    if(checkid(t) == 0)
    {

        printf("\aSorry, the book ID already exists.Please renter another one:\a");
        getch();
        mainmenu();
    return 0;
    }
    a.id=t;
    printf("Book Name:");
    scanf("%s",a.name);
    printf("Author:");
    scanf("%s",a.Author);
    printf("Quantity:");
    scanf("%d",&a.quantity);
    printf("Price:");
    scanf("%f",&a.Price);
    printf("Rack No:");
    scanf("%d",&a.rackno);
    return 1;
    }


    int checkid(int t)  //check whether the book is exist in library or not
    {
    rewind(fp);
    while(fread(&a,sizeof(a),1,fp)==1)
    if(a.id==t)
    return 0;  //returns 0 if book exits
    return 1; //return 1 if it not
}

void issuerecord()  //display issued book's information
{
    printf("\nThe Book has taken by Mr. %s",a.stname);
    printf("\nIssued Date:%d-%d-%d",a.issued.dd,a.issued.mm,a.issued.yy);
    printf("\nReturning Date:%d-%d-%d",a.duedate.dd,a.duedate.mm,a.duedate.yy);
}

void main()
{
    //Password();
    mainmenu();
    //getch();
    return;
}

