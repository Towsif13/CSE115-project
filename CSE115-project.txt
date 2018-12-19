#include<stdio.h>
#include<conio.h>
#include <stdlib.h>
#include<string.h>

void mainmenu(void);
void addbooks(void);
void deletebooks(void);
void editbooks(void);
void searchbooks(void);
void sellbooks(void);
void viewbooks(void);
void sellrecord(void);
//void closeapplication(void);
void returnfunc(void);
void password(void);
FILE *fp;
FILE *fs;
int s,i;
struct books
{
    int id;
    char name[20];
    char Author[20];
    int quantity;
    int Price;
};
struct sold
{
    int id;
    char name[20];
    char Author[20];
    char customer[20];
    int Price;
};

struct books a;
struct sold b;
int main()

{
    password();
    //mainmenu();
      getch();
   return 0;
}

void password()
{
    system("cls");
    char a[10];
    char b[7]="towsif";
    printf("\n\n\n\n\n\n\n\n\n\n\n\n\n                                               Enter password : ");
    scanf("%s",a);
    if (strcmp(a,b)==0)
    {
        system("cls");
        mainmenu();
    }

    else
    {

        system("cls");
        printf("\n\n\n\n\n\n\n\n\n\n\n\n                                                  Wrong password !!!\n\n");
        printf("                                             Press ANY KEY to try again !");
        if(getch()==13){

        password();
        }
    else
        password();

    }

}

void mainmenu()
{
    system("cls");
    //int option;
    printf("\n            ########################### KHATUN BOOK SHOP ###########################");
    printf("\n\n\n\n\n                              ************* MAIN MENU *************\n\n\n");
    printf("         1.Add Book\n\n");
    printf("         2.Delete Book\n\n");
    printf("         3.Search Book\n\n");
    printf("         4.Sell Book\n\n");
    printf("         5.View Book List\n\n");
    printf("         6.Edit Book Record\n\n");
    printf("         7.Sell Record\n\n");
    printf("         8.Close Application\n\n");
    printf("                          -------------------------------------------\n");
    printf("         Enter your choice: ");
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
        sellbooks();
        break;
        case '5':
        viewbooks();
        break;
        case '6':
        editbooks();
        break;
        case '7':
        sellrecord();
        break;
        case '8':
        {
            system("cls");
            printf("\n         \n        Thanks for using the Program......\n\n\n");
            printf("\n\n        Made by Mokashefa and Towsif \n\n\n\n");
            exit(0);
        }
        default:
        {
        printf("\nWrong Entry!!Please re-entered correct option");
        system("cls");
        mainmenu();
        }
    }
}

void addbooks(void)    //funtion that add books
{
     system("cls");
     //int d;
    printf("\n\n\n\n\n                              ************* SELECT CATAGORY *************\n\n\n");
    printf("         1. Computer\n\n");
    printf("         2. Electronics\n\n");
    printf("         3. Electrical\n\n");
    printf("         4. Civil\n\n");
    printf("         5. Mechanical\n\n");
    printf("         6. Architecture\n\n");
    printf("         7. Back to main menu\n\n");
    printf("         Enter your choice: ");
    scanf("%d",&s);
    if(s==7){

    mainmenu() ;
    system("cls");
    }
    fp=fopen("towsif.txt","a+");
    if(fp==NULL){
        printf("File openning error ");
        return ;
    }
    else
    {
        system("cls");
        printf("Book ID : ");
        scanf("%d",&a.id);
        fprintf(fp,"%d ",a.id);
        fflush(stdin);
        printf("Book name : ");
        gets(a.name);
        fprintf(fp,"%s ",a.name);
        fflush(stdin);
        printf("Author : ");
        gets(a.Author);
        fprintf(fp,"%s ",a.Author);
        fflush(stdin);
        printf("Quantity : ");
        scanf("%d",&a.quantity);
        fprintf(fp,"%d ",a.quantity);
        fflush(stdin);
        printf("Price : ");
        scanf("%d",&a.Price);
        fprintf(fp,"%d\n",a.Price);
        }
        fclose(fp);
        printf("Successfully Added !!!!\n\n");
        printf("Save any more?(Y / N):");
    if(getch()=='n')
        mainmenu();
    else
        system("cls");
        addbooks();


}

void viewbooks(void)
{
    system("cls");
    printf("            ********************************* Book List *****************************\n\n");
    printf("   ID\t\tBOOK NAME\tAUTHOR\t\tQUANTITY\tPRICE\n\n");
    fp=fopen("towsif.txt","r");
    rewind(fp);
    while( !feof(fp))
    {
        fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);
        printf("   %d\t\t%s\t\t%s\t\t%d\t\t%d\n",a.id,a.name,a.Author,a.quantity,a.Price);
        i=i+a.quantity;
    }
    printf("\n\n Total books = %d\n\n",i);
    fclose(fp);
    returnfunc();
}
void returnfunc(void)
{
    {
    printf("\n\n Press ENTER to return to main menu\n\n");
    }
    if(getch()==13)
    mainmenu();
    else
     mainmenu();
}
void searchbooks(void)
{
    system("cls");
    int d,k,check;

    fp=fopen("towsif.txt","r");
    rewind(fp);


     printf("\n\n\n\n\                     ***************************** Search Books *********************************\n\n\n\n");
    printf("1. Search By ID\n\n");
    printf("2. Search By Name\n\n");
    printf("3. Main menu\n\n");
    printf("Enter Your Choice : ");
    switch(getch())
    {
        case '1':
            {

                system("cls");
                printf("**** Search Books By ID ****\n\n");
                printf("Enter the book id : ");
                scanf("%d",&d);
                while( !feof(fp))
    {
        fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);

                if(a.id==d)
                 {
                    printf("\nThe Book is available...\n\n");
                    printf("ID: %d\n",a.id);
                    printf("Name: %s\n",a.name);
                    printf("Author: %s \n",a.Author);
                    printf("Quantity: %d \n",a.quantity);
                    printf("Price: TK. %d\n",a.Price);
                    check=1;
                    returnfunc();
                    break;
                 }


                }
                if(check!=1)
                    printf("\n\n Book not found\n");
                returnfunc();

                break;

            }
                case '2':
        {
            char s[15];
            rewind(fp);
            system("cls");
            printf("**** Search Books By Name ****\n");
            printf("Enter Book Name: ");
            scanf("%s",s);
             while( !feof(fp))
    {
        fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);

                if(strcmp(s,a.name)==0)
                 {
                    printf("\n\n\nThe Book is available\n\n");
                    printf("\nID: %d\n",a.id);
                    printf("Name: %s\n",a.name);
                    printf("Author: %s \n",a.Author);
                    printf("Quantity: %d \n",a.quantity);
                    printf("Price: TK. %d\n",a.Price);
                    check=1;
                    returnfunc();
                    break;
                 }

        }
        if(check!=1)
                    printf("\n\n Book not found\n");
                returnfunc();

                break;

}
            case  '3' :
            {

                mainmenu();
            }
            default:
                    {
                         searchbooks();

                    }


    }
    fclose(fp);
}
void sellbooks(void)
{
    int check,d;
    char c;
    system("cls");
    printf("\n\n*** Sell Book section ***\n\n\n");
    fp=fopen("towsif.txt","r");
    rewind(fp);
    printf("Enter the book id : ");
    scanf("%d",&d);
                while( !feof(fp))
    {
        fflush(stdin);
        fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);

                if(a.id==d)
                {
                    printf("The Book is available\n\n");
                    printf("ID: %d\n",a.id);
                    printf("Name: %s\n",a.name);
                    printf("Author: %s \n",a.Author);
                    printf("Quantity: %d \n",a.quantity);
                    printf("Price: TK. %d\n\n\n",a.Price);
                    check=1;

                    break;
                }

    }
        if(check!=1)
        {
                printf("\n\n Book not found\n");
                returnfunc();
        }

    printf("\n\n Do you want to sell this book (Y/N) ? \n\n");
    fflush(stdin);

    scanf("%c",&c);
    if(c=='y')
    {//(strcmp(s,a.name)==0)
        fs=fopen("sold.txt","a");
        system("cls");

        printf("BOOK DETAILS\n\n");
        printf("ID : %d \n",a.id);
        printf("NAME : %s \n",a.name);
        printf("AUTHOR : %s \n",a.Author);
        printf("PRICE : %d\n",a.Price);
        fflush(stdin);
        fprintf(fs,"%d ",a.id);
        fflush(stdin);
        fprintf(fs,"%s ",a.name);
        fflush(stdin);
        fprintf(fs,"%s ",a.Author);
        printf("\nCustomer name : ");
        fflush(stdin);
        gets(b.customer);
        fprintf(fs,"%s ",b.customer);
        fflush(stdin);
        fprintf(fs,"%d\n",a.Price);
        printf("\n\nBook SOLD !!!\n\n");
        returnfunc();
    }
    else
        returnfunc();

    fclose(fp);
    fclose(fs);

}
void deletebooks(void)
{
    system("cls");
    FILE *f1;
    int found;
    char name1[10];
    printf("******************DELETE BOOK SECTION******************\n\n");
    printf("Enter book name : ");
    fflush(stdin);
    gets(name1);
    fp=fopen("towsif.txt","r");
    f1=fopen("delete.txt","w");
    while(!feof(fp))
    {
         fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);
         if(strcmp(a.name,name1)!=0)
         {
            fflush(stdin);
            fprintf(f1,"%d %s %s %d %d\n",a.id,a.name,a.Author,a.quantity,a.Price);
         }
         else if(strcmp(a.name,name1)==0)
            found=1;
    }
    fclose(fp);
    fclose(f1);
    if(found!=1)
        printf("\n\nBOOK NOT FOUND");
    else
    {
        remove("towsif.txt");
        rename("delete.txt","towsif.txt");
        printf("\n\nDelete complete \n\n");
    }
    returnfunc();
}
void sellrecord(void)
{
    system("cls");
    printf("*********************************Sell Record*****************************\n\n");
    printf("   ID\t\tBOOK NAME\tAUTHOR\t\tCUSTOMER NAME\t\tPRICE\n\n");
    fs=fopen("sold.txt","r");
    rewind(fs);
    while( !feof(fs))
    {
       fscanf(fs,"%d %s %s %s %d\n",&b.id,b.name,b.Author,&b.customer,&b.Price);
       printf("   %d\t\t%s\t\t%s\t\t%s\t\t\t%d\n",b.id,b.name,b.Author,b.customer,b.Price);
    }
    fclose(fs);
    returnfunc();
}
void editbooks(void)
{
    system("cls");
    FILE *f2;
    int found;
    char name1[10];
    printf("******************EDIT BOOK SECTION******************\n\n");
    printf("\n\nEnter book name : ");
    fflush(stdin);
    gets(name1);
    fp=fopen("towsif.txt","r");
    f2=fopen("modify.txt","w");
    while(!feof(fp))
    {
         fscanf(fp,"%d %s %s %d %d\n",&a.id,a.name,a.Author,&a.quantity,&a.Price);
         if(strcmp(a.name,name1)!=0)
         {
            fflush(stdin);
            fprintf(f2,"%d %s %s %d %d\n",a.id,a.name,a.Author,a.quantity,a.Price);
         }
         else if(strcmp(a.name,name1)==0)
         {
             printf("\n\nBOOK DETAILS \n\n");
             printf("ID: %d\n",a.id);
             printf("Name: %s\n",a.name);
             printf("Author: %s \n",a.Author);
             printf("Quantity: %d \n",a.quantity);
             printf("Price: TK. %d\n\n\n",a.Price);
             printf("Enter new information : \n\n");
            printf("Book ID : ");
            scanf("%d",&a.id);
            fprintf(f2,"%d ",a.id);
            fflush(stdin);
            printf("Book name : ");
            gets(a.name);
            fprintf(f2,"%s ",a.name);
            fflush(stdin);
            printf("Author : ");
            gets(a.Author);
            fprintf(f2,"%s ",a.Author);
            fflush(stdin);
            printf("Quantity : ");
            scanf("%d",&a.quantity);
            fprintf(f2,"%d ",a.quantity);
            fflush(stdin);
            printf("Price : ");
            scanf("%d",&a.Price);
            fprintf(f2,"%d\n",a.Price);
            found=1;
            printf("\n\n\nBOOK INFO MODIFIED SUCCESSFULLY \n\n\n");
         }
    }
         fclose(fp);
         fclose(f2);
    if(found!=1)
        printf("BOOK NOT FOUND");
    else
    {
        remove("towsif.txt");
        rename("modify.txt","towsif.txt");
        printf("\n\nEdit complete \n\n");
    }
    returnfunc();
}
