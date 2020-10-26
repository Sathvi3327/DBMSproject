#include<iostream>
#include<cstdio>
#include<cstdlib>
#include<conio.h>
#include<cstring>
#include<iomanip>
using namespace std;
void vline(char ch)
{
	for(int i = 80; i > 0;i--)
	cout<<ch;
}
int main()
{
	FILE *fp,*ft;
	char another;
	int choice;
	struct student
	{
		char first_name[50], last_name[50], course[100] ,eNo[10], section;
	}e;
	char eNumber[10];
	long int recsize;
	fp = fopen("users.txt","rb+");
	if(fp== NULL)
	{
		fp = fopen("users.txt","wb+");
		if(fp == NULL)
		{
			cout<<"Cannot open file.";
			return 0;
		}
	}
	recsize = sizeof(e);
	do
	{
		system("cls");
		cout<<"\n\n\n\t\t\t********* STUDENT DATABASE MANAGEMENT SYSTEM *********";
		cout<<"\n\n";
		cout<<"\n\t\t\t\t\t[1] Add Records";
		cout<<"\n\t\t\t\t\t[2] List Records";
		cout<<"\n\t\t\t\t\t[3] Modify Records";
		cout<<"\n\t\t\t\t\t[4] Delete Records";
		cout<<"\n\t\t\t\t\t[5] Exit program";
		cout<<"\n\n";
		cout<<"\t\t\t\t\tSelect your choice :: \t";
		cin>>choice;
		switch(choice)
		{
		case 1:
			fseek(fp,0,SEEK_END);
			another = 'Y';
			while(another == 'y' || another == 'Y')
			{
				system("cls");
				cout<<"\n\n\n\t\t\t";
				cout<<"Enter First name: ";
				cin>>e.first_name;
				cout<<"\t\t\tEnter Last name: ";
				cin>>e.last_name;
				cout<<"\t\t\tEnter Enrollment No.: ";
            	cin>>e.eNo;
				cout<<"\t\t\tEnter the course: ";
				cin>>e.course;
				cout<<"\t\t\tEnter the section: ";
				cin>>e.section;
				fwrite(&e,recsize,1,fp);
				cout<<"\n\t\t\tAdd another record (Y/N) :  ";
				cin>>another;
			}
			break;
		case 2:
			rewind(fp);
			system("cls");
			cout<<"\n\n\t\t\t** Record List **\n";
        	vline('=');
       		while (fread(&e,recsize,1,fp)==1)
			{
				cout<<"\n\t\t\tName: "<<e.first_name<<" "<<e.last_name;
          		cout<<"\n\t\t\tEnrollment No: "<<e.eNo;
            	cout<<"\n\t\t\tCourse: "<<e.course;
            	cout<<"\n\t\t\tSection: "<<e.section;
			}
			break;
		case 3:
			system("cls");
			another = 'Y';
			while(another == 'y' || another == 'Y')
			{
				system("cls");
            	cout<<"\n\t\t\tEnter the Enrollment no. of the student: ";
            	cin>>eNumber;
				rewind(fp);
				while(fread(&e, recsize,1,fp) == 1)
				{
					if(strcmp(eNumber,e.eNo)==0)
					{
						cout<<"\n\n\t\t\tEnter new first name: ";
                        cin>>e.first_name;
                        cout<<"\t\t\tEnter new last name: ";
                        cin>>e.last_name;
                        cout<<"\t\t\tEnter new enrollment number: ";
                        cin>>e.eNo;
                        cout<<"\t\t\tEnter new course: ";
                        cin>>e.course;
                        cout<<"\t\t\tEnter new section: ";
                        cin>>e.section;
                        fseek(fp,-recsize,SEEK_CUR);
                        fwrite(&e,recsize,1,fp);
                        break;
                    }
					else
					{
						cout<<"\n\nRecord not found";
					}
				}
				cout<<"\nModify another record (Y/N) :  ";
				cin>>another;
			}
			break;
		case 4:
			system("cls");
			another = 'Y';
			while(another == 'Y' || another == 'y')
			{
				system("cls");
            	cout<<"\n\t\t\tEnter the Enrollment no. of the student: ";
            	cin>>e.eNo;
				ft = fopen("temp.txt","wb+");
				rewind(fp);
				while(fread(&e,recsize,1,fp) == 1)
				{
					if(strcmp(eNumber,e.eNo)==0)
					{
                   		fwrite(&e,recsize,1,ft);
               		}
					fclose(fp);
					fclose(ft);
					remove("users.txt");
					rename("temp.txt","users.txt");
					fp = fopen("users.txt","rb+");
				}
				cout<<"\n Delete another record(Y/N) :  ";
				cin>>another;
			}
			break;
		case 5:
			cout<<"\n\n";
			cout<<"\t\t   THANK YOU FOR USING   "<<endl<<"\n\n\t\t\t\t\Exited";
			exit(0);
			break;
		default:cout<<"\n\nWrong Choice Try Again!!";
            break;
		}
	}
	while(choice!=5);
	return 0;
}
