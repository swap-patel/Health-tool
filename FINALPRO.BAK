
/* header file required */
#include<fstream.h>       // for files
#include<conio.h>         // for colors
#include<graphics.h>      // for graphics
#include<stdio.h>
#include<ctype.h>
#include<string.h>
#include<stdlib.h>
#include<process.h>       // for exit()
#include<iomanip.h>       // for setw()
#include<dos.h>

// creation of class medicine
class medicine
{
	char name[20],compny[20],state[20];     // data members
	char mrkt_holder[20],location[20];
	float mrp,dis;
	int exp_year;

	public:                       // access specifier

	void add_item();                // member fuctions
	void show_item(char nm[]);
	void del_item(char nm[]);
	void update_item(char nm[]);
	void rec_list(int z);
	void avail(char na1[],char cpy[]);
	void lctn(char na2[],char st[]);
	void disfgr_net(char na3[],char cmp[]);
};

// creation of class staff
class staff
{
	int srno,age;                      // data members
	char gender,name[20];
	char pos[20],qualif[30];
	long sal;

	public:                       // access specifier

	void add_memb();              // member fuctions
	void del_memb(char nm[]);
	void show_details(char nm[]);
	void update_details(char nm[]);
	void show_details_record(int z);
	void salary(char na[]);
};

void medicine::add_item()         // function to add new item
{

	textbackground(YELLOW);
	textcolor(BLUE);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.    */
	gotoxy(6,2);
	/* gotoxy moves the cursor to the given position in the
	current text window. */
	cprintf("ENTER FOLLOWING DETAILS");
	gotoxy(6,6);
	cprintf("NAME OF MEDICINE :");
	gotoxy(45,6);gets(name);
	gotoxy(6,8);
	cprintf("STATE (TABLET/GEL/SYRUP/OTHER) :");
	gotoxy(45,8);gets(state);
	gotoxy(6,10);
	cprintf("COMPANY :");
	gotoxy(45,10);gets(compny);
	gotoxy(6,12);
	cprintf("MARKETING HOLDER :");
	gotoxy(45,12);gets(mrkt_holder);
	gotoxy(6,14);
	cprintf("MAXIMUM PRICE RETAIL :");
	gotoxy(45,14);cin>>mrp;
	gotoxy(6,16);
	cprintf("DISCOUNT FIGURE :");
	gotoxy(45,16);cin>>dis;

	if(dis>=mrp)
	while(1)
	/* checks whether given discount is valid or not */
	{
		if(dis<mrp)
		{
			gotoxy(37,60);
			cprintf("                                     ");
			break;
		}
		textbackground(CYAN);
		textcolor(RED+BLINK);
		gotoxy(40,60);
		cprintf("DATA INCORRECT, ENTER AGAIN");
		gotoxy(45,16);
		textbackground(BLACK);
		textcolor(WHITE);
		cprintf("        ");
		gotoxy(45,16);cin>>dis;
	}
	textbackground(YELLOW);
	textcolor(BLUE);
	gotoxy(6,18);
	cprintf("YEAR OF EXPIRY :");
	gotoxy(45,18);cin>>exp_year;

	if(exp_year<=2017)
	while(1)
	/* checks if the given expiry year is valid or not */
	{
		if(exp_year>2017)
		{
			gotoxy(37,60);
			cprintf("                                         ");
			break;
		}
		textbackground(CYAN);
		textcolor(RED+BLINK);
		gotoxy(40,60);
		cprintf("INCORRECT EXPIRY DATE, ENTER AGAIN");
		textbackground(BLACK);
		textcolor(WHITE);
		gotoxy(45,18);
		cprintf("        ");
		gotoxy(45,18);cin>>exp_year;
	}
	textbackground(YELLOW);
	textcolor(BLUE);
	gotoxy(6,20);
	cprintf("LOCATION ALLOCATED :");
	gotoxy(45,20);gets(location);


}

void medicine::show_item(char nm[])         // function to show details
{
	if(strcmpi(name,nm)==0)
	// compares the entered name of medicine with the record
	{
			clrscr();   // Clears text mode window
			textbackground(CYAN);
			textcolor(RED);
			/* textbackground selects a new text background color.
			textcolor selects a new character color in text mode.  */
			gotoxy(6,2);
			/* gotoxy moves the cursor to the given position
			 in the current text window. */
			cprintf("DETAILS ARE AS FOLLOWS");
			textbackground(YELLOW);
			textcolor(BLUE);
			gotoxy(6,5);
			cprintf("NAME OF MEDICINE :");
			gotoxy(45,5);cout<<" "<<name;
			gotoxy(6,7);
			cprintf("STATE (TABLET/GEL/SYRUP/OTHER) :");
			gotoxy(45,7);cout<<" "<<setw(5)<<state;
			// setw sets the width while writing
			gotoxy(6,9);
			cprintf("COMPANY :");
			gotoxy(45,9);cout<<" "<<setw(5)<<compny;
			gotoxy(6,11);
			cprintf("MARKETING HOLDER :");
			gotoxy(45,11);cout<<" "<<setw(5)<<mrkt_holder;
			gotoxy(6,13);
			cprintf("MAXIMUM PRICE RETAIL :");
			gotoxy(45,13);cout<<" "<<setw(5)<<mrp;
			gotoxy(6,15);
			cprintf("DISCOUNT FIGURE :");
			gotoxy(45,15);cout<<" "<<setw(5)<<dis;
			gotoxy(6,17);
			cprintf("YEAR OF EXPIRY :");
			gotoxy(45,17);cout<<" "<<setw(5)<<exp_year;
			gotoxy(6,19);
			cprintf("LOCATION ALLOCATED :");
			gotoxy(45,19);cout<<" "<<setw(5)<<location;
			getch();
			/* getch gets a character from console but does
			 not echo to the screen  */
	}

}

void medicine::del_item(char nm[])    // function to delete item
{
	fstream k1,k2;
	medicine m;            // object of class medicine
	textbackground(CYAN);
	textcolor(RED);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	k1.open("MEDICINE.DAT",ios::in|ios::binary);
	k2.open("ABC.DAT",ios::out|ios::binary);
	// opening of file
	while(k1.read((char*)&m,sizeof(m)))
	// reads data from stream
	{
		if(strcmpi(nm,m.name)!=0)
			k2.write((char*)&m,sizeof(m));
			// writes data to file
	}
	gotoxy(20,20);cprintf("ITEM NAMED ");
	/* gotoxy moves the cursor to the given position
	 in the current text window. */
	cprintf(nm);cprintf(" DELETED");
	k1.close();k2.close();
	// closing of file
	remove("MEDICINE.DAT");
	rename("ABC.DAT","MEDICINE.DAT");
	getch();
	/* getch gets a character from console
	but does not echo to the screen */


}


void medicine::update_item(char na1[])       // function to update details
{
	fstream k;      int p;
	medicine m;                  //object of class medicine
	textbackground(YELLOW);
	textcolor(BLUE);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	k.open("MEDICINE.DAT",ios::in|ios::out|ios::binary);
	while(k.read((char*)&m,sizeof(m)))
	// reads data from stream
	{
		if (strcmpi(na1,m.name)==0)
		// compares name of the medicine entered
		{
			clrscr();   // Clears text mode window
			p=k.tellg();
			k.seekp(p-sizeof(m),ios::beg);
			// moves the put pointer to desired position
			textbackground(YELLOW);
			textcolor(BLUE);
			gotoxy(6,2);
			/* gotoxy moves the cursor to the given position
			 in the current text window. */
			cprintf("NAME OF ITEM :");
			gotoxy(45,2);
			gets(m.name);
			gotoxy(6,4);
			cprintf("STATE(TABLET/GEL/SYRUP/OTHER) : ");
			gotoxy(45,4);
			gets(m.state);
			gotoxy(6,6);
			cprintf("COMPANY : ");
			gotoxy(45,6);
			gets(m.compny);
			gotoxy(6,8);
			cprintf("MARKETING HOLDER : ");
			gotoxy(45,8);
			gets(m.mrkt_holder);
			gotoxy(6,10);
			cprintf("M.R.P. : ");
			gotoxy(45,10);
			cin>>m.mrp;
			gotoxy(6,12);

			cprintf("DISCOUNT : ");
			gotoxy(45,12);
			cin>>m.dis;
			if(m.dis>=m.mrp)
			while(1)
			{
				if(m.dis<m.mrp)
				{
					gotoxy(37,60);
					cprintf("                                     ");
					break;
				}
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(40,60);
				cprintf("DATA INCORRECT, ENTER AGAIN");
				gotoxy(45,12);
				textbackground(YELLOW);
				textcolor(BLUE);
				cprintf("        ");
				gotoxy(45,12);cin>>m.dis;
			}

			gotoxy(6,14);
			cprintf("YEAR OF EXPIRY : ");
			gotoxy(45,14);
			cin>>m.exp_year;
			if(m.exp_year<=2017)
			while(1)
			{
				if(m.exp_year>2017)
				{
					gotoxy(37,60);
					cprintf("                                         ");
					break;
				}
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(40,60);
				cprintf("INCORRECT EXPIRY DATE, ENTER AGAIN");
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(45,14);
				cprintf("        ");
				gotoxy(45,14);cin>>m.exp_year;
			}

			gotoxy(6,16);
			cprintf("LOCATION ALLOCATED : ");
			gotoxy(45,16);
			gets(m.location);
			k.write((char*)&m,sizeof(m));
			gotoxy(20,20);
			cprintf(" DETAILS OF ITEM ");cout<<na1;
			cprintf(" IS UPDATED. ");getch();
			break;

		}

	}
	k.close();
	// closing of file

}

void medicine::rec_list(int z)        // function to show item name list
{

	textbackground(CYAN);
	textcolor(RED);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	gotoxy(6,2+z);
	/* gotoxy moves the cursor to the given position in the
	current text window. */
	textbackground(YELLOW);
	textcolor(BLUE);
	cprintf(":->");
	gotoxy(16,2+z);cout<<" "<<setw(3)<<name;
}

void medicine::avail(char na1[],char cpy[])
 // function to check availability of item
{
	if(strcmpi(name,na1)==0&&strcmpi(compny,cpy)==0)
	// compares name & company entered
	{
		textbackground(CYAN);
		textcolor(RED+BLINK);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(20,20);
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		cprintf("ITEM AVAILABLE");
	}

}

void medicine::lctn(char na2[],char st[])
 // function to return location of item
{
	if(strcmpi(na2,name)==0&&strcmpi(st,state)==0)
	// compares name and state of item entered
	{
		gotoxy(20,20);
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		textbackground(CYAN);
		textcolor(RED+BLINK);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		cprintf("LOCATION");
		gotoxy(45,20);
		cout<<location;
	}
}

void medicine::disfgr_net(char na3[],char c[])
// function to give discount and net price per item
{
	if(strcmpi(na3,name)==0&&strcmpi(c,compny)==0)
	// compares name and company entered
	{
		textbackground(CYAN);
		textcolor(RED+BLINK);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(20,18);
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		cprintf("DISCOUNT ON MRP. ");
		gotoxy(20,20);
		cprintf("NET AMOUNT ");
		gotoxy(45,18);
		cout<<dis;
		gotoxy(45,20);
		cout<<mrp-dis;
	}
}

void chng_item()   // function to call member function of class medicine
{
	while(1)
	{
		clrscr();  // Clears text mode window
		int ch;
		medicine m;   // object of class medicine declared
		fstream f;
		textbackground(CYAN);
		textcolor(RED);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(6,2);cprintf("1.ADD NEW ITEM");
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		gotoxy(6,4);cprintf("2.SHOW ITEM DETAILS");
		gotoxy(6,6);cprintf("3.DELETE ITEM");
		gotoxy(6,8);cprintf("4.EDIT ITEM DETAILS");
		gotoxy(6,10);cprintf("5.SHOW RECORD LIST");
		gotoxy(6,12);cprintf("6.CHECK AVAILABILITY OF MEDICINE");
		gotoxy(6,14);cprintf("7.FIND LOCATION OF MEDICINE");
		gotoxy(6,16);cprintf("8.FIND DISCOUNT FIG. & NET-PRICE ");
		gotoxy(6,18);cprintf("9.BACK TO PREVIOUS PAGE");
		gotoxy(6,20);cprintf("ENTER YOUR CHOICE");
		textbackground(BLACK);
		textcolor(WHITE);
		gotoxy(45,20);cin>>ch;
		switch(ch)
		{
			case 1:
				clrscr();       // Clears text mode window
				f.open("MEDICINE.DAT",ios::app|ios::in|ios::out);
				//opening of file stream (out mode)
				m.add_item();       // function calling
				f.write((char*)&m,sizeof(m));
				// data writing to file
				f.close();
				// closing of file
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(30,22
				);
				cprintf("ITEM ADDED SUCCESSFULLY");
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				break;
			case 2:
				char nm[20];
				clrscr();          // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF MEDICINE");
				gotoxy(45,2);
				gets(nm);
				f.open("MEDICINE.DAT",ios::in|ios::binary);
				// opening of file stream (in mode)
				while(f.read((char*)&m,sizeof(m)))
				// Reads data from a stream
				{
					m.show_item(nm);  // function calling
				}
				f.close();
				// closing of file
				break;
			case 3:
				char nam[20];
				clrscr();        // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF ITEM TO BE DELETED");
				gotoxy(45,2);
				gets(nam);
				m.del_item(nam);  // function calling
				f.close();
				// closing of file
				break;
			case 4:
				char na[20];
				clrscr();          // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF ITEM TO BE EDITED");
				gotoxy(45,2);
				gets(na);
				m.update_item(na);  //function calling
				f.close();  //closinf of file
				break;
			case 5:
				clrscr();         // Clears text mode window
				textbackground(CYAN);
				textcolor(RED+BLINK);
				f.open("MEDICINE.DAT",ios::in|ios::binary);
				//openinf of file stream (in mode)
				gotoxy(6,2);
				cprintf("NAME OF MEDICINE");
				gotoxy(6,5);       int i=4;
				while(f.read((char*)&m,sizeof(m)))
				// reads data from stream
				{
					m.rec_list(i);   //function calling
					i=i+2;
				}
				f.close();
				//closing of file
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				break;

			case 6:
				char na1[20],cpy[20];
				f.open("MEDICINE.DAT",ios::in|ios::binary);
				//opening of file stream (in mode)
				clrscr();         // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("1.NAME OF MEDICINE ");
				gotoxy(45,2);gets(nam);
				gotoxy(6,4);
				cprintf("2.COMPANY ");
				gotoxy(45,4);gets(cpy);
				while(f.read((char*)&m,sizeof(m)))
				// reads data from stream
					m.avail(nam,cpy);   // function calling
				f.close();
				//closing of file
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				break;
			case 7:
				clrscr();        // Clears text mode window
				f.open("MEDICINE.DAT",ios::in|ios::binary);
				// opening of file stream (in mode)
				char na2[20],st[20];
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("1.NAME OF ITEM ");
				gotoxy(45,2);
				gets(na2);
				gotoxy(6,4);
				cprintf("2.STATE OF MEDICINE ");
				gotoxy(45,4);
				gets(st);
				while(f.read((char*)&m,sizeof(m)))
				// read data from stream
					m.lctn(na2,st); //function calling
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				f.close();
				//closing of file stream
				break;
			case 8:
				f.open("MEDICINE.DAT",ios::in|ios::binary);
				//opening of file stream (in mode)
				char na3[20],c[20];
				clrscr();      // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("1.NAME OF ITEM ");
				gotoxy(45,2);
				gets(na3);
				gotoxy(6,4);
				cprintf("2.COMPANY ");
				gotoxy(45,4);
				gets(c);
				while(f.read((char*)&m,sizeof(m)))
				// reads data from stream
					m.disfgr_net(na3,c); //function calling
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				f.close();
				//closing of file
				break;
			case 9:
				void menu();
				menu();          // function
				break;
			default:
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(40,30);
				cprintf("INVALID MATCH");
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
		}
	}
}


void staff::add_memb()      // function to add new member
{

	textbackground(YELLOW);
	textcolor(BLUE);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	gotoxy(6,2);
	/* gotoxy moves the cursor to the given position in the
	current text window. */
	cprintf("ENTER FOLLOWING DETAILS");
	gotoxy(6,6);
	cprintf("SR.NO. :");
	gotoxy(45,6);cin>>srno;
	while(srno<=0)
	// checks if the sr.no. allocated is valid or not
	{
		textbackground(CYAN);
		textcolor(RED+BLINK);
		gotoxy(20,20);
		cprintf("DATA INCORRECT, ENTER AGAiN");
		gotoxy(45,6);
		textbackground(BLACK);
		textcolor(WHITE);
		cprintf("        ");
		gotoxy(45,6);cin>>srno;
		gotoxy(20,20);
		cprintf("                                  ");
	}
	textbackground(YELLOW);
	textcolor(BLUE);
	gotoxy(6,8);
	cprintf("NAME OF MEMBER :");
	gotoxy(45,8);gets(name);
	gotoxy(6,10);
	cprintf("AGE :");
	gotoxy(45,10);cin>>age;
	gotoxy(6,12);
	cprintf("GENDER(M/F) :");
	gotoxy(45,12);cin>>gender;
	while(gender!='M'&&gender!='F')
	// checks if the gender entered is correct or not
	{
		textbackground(CYAN);
		textcolor(RED+BLINK);
		gotoxy(20,20);
		cprintf("DATA INCORRECT, ENTER AGAiN");
		gotoxy(45,12);
		textbackground(BLACK);
		textcolor(WHITE);
		cprintf("        ");
		gotoxy(45,12);cin>>gender;
		gotoxy(20,20);
		cprintf("                                  ");
	}
	textbackground(YELLOW);
	textcolor(BLUE);
	gotoxy(6,14);
	cprintf("POSITION :");
	gotoxy(45,14);gets(pos);
	gotoxy(6,16);
	cprintf("QUALIFICATION :");
	gotoxy(45,16);gets(qualif);
	gotoxy(6,18);
	cprintf("SALARY :");
	gotoxy(45,18);cin>>sal;

}

void staff::show_details(char nm[])      // function to show member details
{

		if(strcmpi(name,nm)==0)
		// compares name entered
		{
			clrscr();  //Clears text mode window
			textbackground(CYAN);
			textcolor(RED);
			/* textbackground selects a new text background color.
			textcolor selects a new character color in text mode.  */
			gotoxy(6,2);
			/* gotoxy moves the cursor to the given position in the
			current text window. */
			cprintf("DETAILS ARE AS FOLLOWS");
			textbackground(YELLOW);
			textcolor(BLUE);
			gotoxy(6,5);
			cprintf("SR.NO. :");
			gotoxy(45,5);cout<<" "<<srno;
			gotoxy(6,7);
			cprintf("NAME OF PERSON :");
			gotoxy(45,7);cout<<" "<<setw(3)<<name;
			// setw sets the width
			gotoxy(6,9);
			cprintf("AGE :");
			gotoxy(45,9);cout<<" "<<setw(2)<<age;
			gotoxy(6,11);
			cprintf("GENDER :");
			gotoxy(45,11);cout<<" "<<setw(5)<<gender;
			gotoxy(6,13);
			cprintf("POSITION :");
			gotoxy(41,13);cout<<" "<<setw(0)<<pos;
			gotoxy(6,15);
			cprintf("QUALIFICATION :");
			gotoxy(45,15);cout<<" "<<setw(5)<<qualif;
			gotoxy(6,17);
			cprintf("SALARY :");
			gotoxy(45,17);cout<<" "<<setw(5)<<sal;
			getch();
			/* getch gets a character from console
			 but does not echo to the screen */
		}

}

void staff::show_details_record(int z)        // function to show name list
{

	textbackground(CYAN);
	textcolor(RED);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	gotoxy(6,2+z);
	/* gotoxy moves the cursor to the given position in the
	current text window. */
	textbackground(YELLOW);
	textcolor(BLUE);
	cprintf(":->");
	gotoxy(16,2+z);cout<<" "<<setw(3)<<name;


}

void staff::del_memb(char nm[])        // function to delete membership
{
	fstream k1,k2;
	staff m;             // object of class staff
	textbackground(CYAN);
	textcolor(RED);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	k1.open("STAFF.DAT",ios::in|ios::binary);
	k2.open("ABC.DAT",ios::out|ios::binary);
	// opening of file
	while(k1.read((char*)&m,sizeof(m)))
	// reads data from stream
	{
		if(strcmpi(nm,name)!=0)
			k2.write((char*)&m,sizeof(m));
			// writes data to file
	}
	gotoxy(20,20);cprintf("MEMBER NAMED ");
	cprintf(nm);cprintf(" DELETED");
	k1.close();k2.close();
	//closing of file
	remove("STAFF.DAT");
	rename("ABC.DAT","STAFF.DAT");
	getch();
	/* getch gets a character from console
	but does not echo to the screen */

}

void staff::update_details(char na1[20])   // function to update member details
{
	fstream k;      int p;
	staff m;                         // object of class staff
	textbackground(YELLOW);
	textcolor(BLUE);
	/* textbackground selects a new text background color.
	textcolor selects a new character color in text mode.  */
	k.open("STAFF.DAT",ios::in|ios::out|ios::binary);
	// opening of file
	while(k.read((char*)&m,sizeof(m)))
	// reads data from stream
	{
		if (strcmpi(na1,m.name)==0)
		// compares name entered
		{
			p=k.tellg();
			k.seekp(p-sizeof(m),ios::beg);
			// moves to put pointer to the desired position
			clrscr();   // Clears text mode window
			textbackground(YELLOW);
			textcolor(BLUE);
			gotoxy(6,2);
			/* gotoxy moves the cursor to the
			given position in the current text window. */
			cprintf("SR.NO. :");
			gotoxy(45,2);
			cin>>srno;
			gotoxy(6,4);
			cprintf("NAME : ");
			gotoxy(45,4);
			gets(name);
			gotoxy(6,6);
			cprintf("GENDER : ");
			gotoxy(45,6);
			cin>>gender;
			gotoxy(6,8);
			cprintf("AGE : ");
			gotoxy(45,8);
			cin>>age;
			gotoxy(6,10);
			cprintf("POSITION : ");
			gotoxy(45,10);
			gets(pos);
			gotoxy(6,12);
			cprintf("QUALIFICATION : ");
			gotoxy(45,12);
			gets(qualif);

			k.write((char*)&m,sizeof(m));
			// writes dtat to file
			gotoxy(20,20);
			cprintf(" DETAILS OF MEMBER ");cout<<na1;
			cprintf(" IS UPDATED. ");getch();
			break;
		}
		else
		{
			clrscr();
			textbackground(CYAN);
			textcolor(RED+BLINK);
			gotoxy(6,2);
			cprintf("INVALID NAME");
			getch();
			/* getch gets a character from console
			but does not echo to the screen */

		}
	}
	k.close();
	// closing of file

}

void staff::salary(char na[])
{
	if(strcmpi(na,name)==0)
	// compares name of member entered
	{
		textbackground(CYAN);
		textcolor(RED+BLINK);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(20,18);
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		cprintf("SALARY : ");
		gotoxy(45,18);
		cout<<sal;

	}
}


void chng_memb()      // function to call member function of class staff
{
	while(1)
	{
		clrscr();      // Clears text mode window
		int ch;
		staff s;       // bject of class staff
		fstream f;
		textbackground(CYAN);
		textcolor(RED);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(6,2);cprintf("1.ADD NEW MEMBER");
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		gotoxy(6,4);cprintf("2.SHOW MEMBER DETAILS");
		gotoxy(6,6);cprintf("3.DELETE MEMBERSHIP");
		gotoxy(6,8);cprintf("4.UPDATE MEMBER DETAILS");
		gotoxy(6,10);cprintf("5.RECORD LIST");
		gotoxy(6,12);cprintf("6.FIND SALARY OF MEMBER");
		gotoxy(6,14);cprintf("7.BACK TO PREVIOUS MENU ");
		gotoxy(6,16);cprintf("ENTER YOUR CHOICE");
		textbackground(BLACK);
		textcolor(WHITE);
		gotoxy(45,16);cin>>ch;
		switch(ch)
		{
			case 1:
				clrscr();       // Clears text mode window
				f.open("STAFF.DAT",ios::app|ios::in|ios::out);
				// opening of file stream (out mode)
				s.add_memb(); // function calling
				f.write((char*)&s,sizeof(s));
				// writing of data to file
				f.close();
				// closing of file
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(20,22);
				cprintf("MEMBERSHIP CONFIRMED");
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				break;
			case 2:
				char nm[20];
				clrscr();         // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF MEMBER");
				gotoxy(45,2);
				gets(nm);
				f.open("STAFF.DAT",ios::in|ios::binary);
				//opeing of file stream (in mode)
				while(f.read((char*)&s,sizeof(s)))
				// reads data from stream
				{
					s.show_details(nm); // function calling
				}
				f.close();
				break;
			case 3:
				char nam[20];
				clrscr();        // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF MEMBER TO BE DELETED");
				gotoxy(45,2);
				gets(nam);
				s.del_memb(nam);  // function calling
				f.close();
				// closing of file
				break;
			case 4:
				char na[20];
				clrscr();      // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("ENTER NAME OF MEMBER TO BE EDITED");
				gotoxy(45,2);
				gets(na);
				s.update_details(na); // function calling
				f.close();
				//closing of file
				break;
			case 5:
				clrscr();      // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("RECORD OF STAFF MEMBERS ");
				gotoxy(45,2);               int i=4;
				f.open("STAFF.DAT",ios::in|ios::binary);
				//opening of file stream (in mode)
				while(f.read((char*)&s,sizeof(s)))
				//reads data from stream
				{
					s.show_details_record(i);
					// function calling
					  i=i+2;
				}
				f.close();
				//closing of file
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				break;
			case 6:
				f.open("STAFF.DAT",ios::in|ios::binary);
				//opening of file stream (in mode)
				char na1[20];
				clrscr();      // Clears text mode window
				textbackground(YELLOW);
				textcolor(BLUE);
				gotoxy(6,2);
				cprintf("1.NAME OF PERSON : ");
				gotoxy(45,2);
				gets(na1);
				while(f.read((char*)&s,sizeof(s)))
				// reads data from stream
					s.salary(na1); //function calling
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				f.close();
				//closing of file
				break;
			case 7:
				void menu();
				menu();          // function calling
				break;
			default:
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(40,30);
				cprintf("INVALID MATCH");
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
		}
	}
}

void menu()
{
	while(1)
	{

		clrscr();   // Clears text mode window
		int ch;
		textbackground(YELLOW);
		textcolor(BLUE);
		/* textbackground selects a new text background color.
		textcolor selects a new character color in text mode.  */
		gotoxy(6,2);cprintf("1. LOOKING FOR MEDICINES & OTHER ITEMS ");
		/* gotoxy moves the cursor to the given position in the
		current text window. */
		gotoxy(6,4);cprintf("2. LOOKING FOR STAFF DETAILS ");
		gotoxy(6,6);cprintf("3. EXIT ");
		textbackground(CYAN);
		textcolor(RED+BLINK);
		gotoxy(6,9);cprintf("ENTER YOUR CHOICE");
		gotoxy(45,9);cin>>ch;
		switch(ch)
		{
			case 1:
				chng_item();        // function calling
				break;
			case 2:
				chng_memb();       // function calling
				break;
			case 3:
				exit(0);
				 // function to quit the program
			default:
			{
				textbackground(CYAN);
				textcolor(RED+BLINK);
				gotoxy(20,20);
				cprintf("CHOICE DID NOT MATCH");
				getch();
				/* getch gets a character from console
				 but does not echo to the screen */
				exit(0);
			}
		}
	}
}

void intro()
{
	int d=DETECT,l;  initgraph(&d,&l,"");
       //	   void	starpage();
       //	starpage();
	setcolor(RED);
	settextstyle(0,0, 2);
	outtextxy(40,60," INTRODUCTION TO PROJECT ");
	setcolor(10);
	int x=40,y=100;
	settextstyle(0,0, 0);
	outtextxy(x,y,":-> The project has the facility of maintaining records ");
	y=y+15;
	outtextxy(x,y,"of all the medicines and other products available in medical stores.");
	y=y+45;
	outtextxy(x,y,":-> It also maintains various record of staff members ");
	y=y+15;
	outtextxy(x,y,"(employees) working currently at the store. ");
	y=y+45;
	outtextxy(x,y,":-> The project can hold as many number of records as required. ");
	y=y+45;
	outtextxy(x,y,":-> It is very easy to work on with utmost flexibility ");
	y=y+15;
	outtextxy(x,y,"and necessary security options. ");
	y=y+45;
	outtextxy(x,y,":-> The project provides a seperate option for confidential ");
	y=y+15;
	outtextxy(x,y,"details meant only for manager of the stores. ");
	y=y+45;
	outtextxy(x,y,":-> The purpose of this program is to search for all the ");
	y=y+15;
	outtextxy(x,y,"necessary fields efficiently with optimum time consumption. ");
	getch();
	closegraph();

}



  /*
		**********************************
		*                                *
		*        GRAPHIC  FUNCTIONS      *
		*                                *
		**********************************



    */
void elixir()
{

//--------------E
			setfillstyle(SOLID_FILL,12);
			setcolor(12);
			delay(400);
	{
		line(187,123,184,190);line(184,190,215,190);line(215,190,214,176);
		line(214,176,197,177);line(197,177,197,164.5);line(197,164.5,214,165);line(214,165,216,148);
		line(216,148,199,150);line(199,150,199,138);line(199,138,214.5,136);line(214.5,136,215,120);
		line(215,120,187,123);
	}       floodfill(188,124,12);

//--------------L
			setfillstyle(SOLID_FILL,9);
			setcolor(9);
	{
		line(234,122,232,190);line(232,190,259,188);line(259,188,260,170);
		line(260,170,246,173);line(246,173,244,119);line(244,119,234,122);
	}       floodfill(235,132,9);

//--------------I
			setfillstyle(SOLID_FILL,14);
			setcolor(14);
	{
		line(279,120,279,135);line(279,135,290.5,134);line(290.5,134,289,175);
		line(289,175,279,174);line(279,174,280,189);line(280,189,311,189);
		line(311,189,311,171);line(311,171,302,175);line(302,175,302,134);
		line(302,134,311,135);line(311,135,311,122);line(311,122,279,120);
	}       floodfill(280,121,14);

//--------------X
			setfillstyle(SOLID_FILL,4);
			setcolor(4);
	{
		line(337,120,328,122);line(360,120,351,120);
		line(326,190,339,190);line(361,191,351,190);

		line(328,122,334,157);line(334,157,326,190);
		line(339,190,343,165);line(343,165,351,190);
		line(360,120,353,155);line(353,155,361,191);
		line(337,120,344,148);line(344,148,351,120);
	}       floodfill(337,123,4);

//--------------I
			setfillstyle(SOLID_FILL,5);
			setcolor(5);
	{
		line(374,120,374,135);line(374,135,385.5,134);line(385.5,134,384,175);
		line(384,175,374,174);line(374,174,375,189);line(375,189,406,189);
		line(406,189,406,171);line(406,171,397,175);line(397,175,397,134);
		line(397,134,406,135);line(406,135,406,122);line(406,122,374,120);
	}       floodfill(375,121,5);

//--------------R
			setfillstyle(SOLID_FILL,6);
			setcolor(6);
	{
		line(425,123,422,190);line(422,190,433,190);line(433,190,435,167);
		line(435,167,443,190);line(443,190,456,189);line(456,189,445,159);
		line(445,159,454,157);line(454,157,456,120);line(456,120,425,123);

		line(437,135,436,146);line(436,146,442,145);
		line(442,145,444,134);line(444,134,437,135);
	}       floodfill(426,124,6);
	delay(1000);
}
void LINECUT()
{
		 int  x=80;
	setcolor(BLACK);   delay(300);
	line(180,123,470,127);   delay(x);
	line(180,100,470,130);   delay(x);
  //	line(180,90,470,180);    delay(x);
	line(180,165,470,110);   delay(x);
	line(180,150,470,100);   delay(x);
  //	line(180,120,470,196);   delay(x);
	line(180,175,470,175);   delay(x);
	line(180,160,470,170);   delay(x);
  //	line(180,176,470,150);   delay(x);
	line(180,110,470,120);   delay(x);
	line(180,129,470,130);   delay(x);
 //	line(180,145,470,160);   delay(x);
	line(180,185,470,165);   delay(x);
	line(180,190,470,185);   delay(x);
   //	line(180,130,470,140);   delay(x);
	line(180,180,470,190);   delay(x);
	line(180,170,470,135);   delay(x);

	delay(400);
}

void linemove()
{
	delay(1000);
	int x,y,i=0;
	setcolor(BLUE);
	setlinestyle(4,3,4);
	for(x=0,y=220;x<=640;x=x+4)
	if(i==0)
	{
		line(x,y-2,x+4,y+2);
		i=1;
		delay(20);

	}
	else
	{
		line(x,y+2,x+4,y-2);
		i=0;
		delay(20);
	}
}

void loading()
{
	closegraph();
	int d=DETECT,m;	initgraph(&d,&m,"");
	setcolor(11);
	outtextxy(290,210,"loading...");
	setcolor(YELLOW);
	rectangle(310,230,330,250);   delay(300);
	int x1=310,x2=312;
	for(x1,x2;x2<=330;x1++,x2++)
	{
		setcolor(BLACK);
		rectangle(x1,230,x2+1.2,230.6);
		delay(40);

		setcolor(YELLOW);
		if(x1>=312)
		   {
		   rectangle(x1-2,230,x2-2,230.5);
		   delay(30);
		   }
	}

	int y1=230,y2=232;
	for(y1,y2;y2<=250;y1++,y2++)
	{

		setcolor(BLACK);
		rectangle(330,y1,330.5,y2+1.2);
		delay(40);

		setcolor(YELLOW);
		if(y1==230) rectangle(329,230,330.5,230.5);
		delay(30);

		setcolor(YELLOW);
		if(y1>=232)
		   {
		   rectangle(330,y1-2,330.5,y2-2);
		   delay(30);
		   }

	}

	x1=328;x2=330;
	for(x1,x2;x2>=312;x1--,x2--)
	{
		setcolor(BLACK);
		rectangle(x1-1.2,250,x2,250.6);
		delay(40);

		setcolor(YELLOW);
		if(x1==328)rectangle(330,249,330.5,250);
		delay(30);

		setcolor(YELLOW);
		if(x1<=327)
		   {
		   rectangle(x1+2,250,x2+1,250.5);
		   delay(30);
		   }
	}
	y1=248,y2=250;
	for(y1,y2;y2>=230;y1--,y2--)
	{

		setcolor(BLACK);
		rectangle(310,y1-1.2,310.5,y2);
		delay(40);

		setcolor(YELLOW);
		if(y1==248) rectangle(310,250,311.5,250.5);
		delay(30);

		setcolor(YELLOW);
		if(y1<=246)
		   {
		   rectangle(310,y1+2,310.5,y2+2);
		   delay(30);
		   }

	}

	x1=310;x2=312;
	for(x1,x2;x2<=319;x1++,x2++)
	{
		setcolor(BLACK);
		rectangle(x1,230,x2+1.2,230.6);
		delay(40);

		setcolor(YELLOW);
		if(x1>=312)
		   {
		   rectangle(x1-2,230,x2-2,230.5);
		   delay(30);
		   }
	}

}
void starpage()
{

	setcolor(7);
	for(int l=-190;l<=640;l=l+30)
	{
			int j=l;
			for(int m=10;m<=480;m=m+20)
			{
				outtextxy(l,m,".");
				l=l+10;
			}
			l=j;
	}
	delay(1500);

}

void boarder()
{
	int gd=DETECT,gm; initgraph(&gd,&gm,"");
    //	rectangle(20,20,610,455);
   //	rectangle(42,38,588,437);

	int x,y,i=0,d=12;
	delay(1000);
	setcolor(YELLOW+BLINK);
	setlinestyle(1,3,2);

	for(x=23,y=452;x<=605;x=x+4)
		if(i==0)
		{
			line(x,y-3,x+4,y+3);
			i=1;
			delay(d);
		}
		else
		{
			line(x,y+2,x+4,y-2);
			i=0;
			delay(d);
		}

	i=0;
	for(x=603,y=447;y>=26;y=y-4)
		if(i==0)
		{
			line(x-3,y,x+3,y-4);
			i=1;
			delay(d);
		}
		else
		{
			line(x+2,y,x+2,y+4);
			i=0;
			delay(d);
		}

	i=0;
	for(x=600,y=25;x>=24;x=x-4)
		if(i==0)
		{
			line(x,y-3,x+4,y+3);
			i=1;
			delay(d);
		}
		else
		{
			line(x,y+2,x+4,y-2);
			i=0;
			delay(d);
		}

	i=0;
	for(x=23,y=30;y<=454;y=y+4)
		if(i==0)
		{
			line(x-3,y,x+3,y-4);
			i=1;
			delay(d);
		}
		else
		{
			line(x+2,y,x+2,y+4);
			i=0;
			delay(d);
		}

}

void password()
{
		int gd=DETECT,gm; initgraph(&gd,&gm,"");
		   setcolor(CYAN);
		char pass[9]="";
		outtextxy(200,300,"Enter Password...");

		setcolor(WHITE);
		for(int y=310;y<=400;y=y+8)
			for(int x=0;x<=640;x++)
				outtextxy(x,y,"³");

		setcolor(BLACK);
		outtextxy(330,320,"¯");
		textbackground(WHITE);
		textcolor(CYAN);
		gotoxy(45,21);
	   //	cin>>pass;

		int i=0,z=0;
		while(1)
		{
			z += 10;
			pass[i] = getch();
			outtextxy(335+z,320,"*");

			if(i==7)
			{
				//outtextxy(330,350,pass);

				if(strcmp(pass,"elixirMS")!=0)
				{
					settextstyle(0,1,2);
					setcolor(GREEN);
					outtextxy(610,50,"WRONG PASSWORD");
					delay(2000);
					exit(0);
				}
				else
					break;
			}

			i++;
		}
}

void frontpageandintro()
{
	clrscr();
	int gd=DETECT,gm; initgraph(&gd,&gm,"");
	int i,j;
	linemove();
	setcolor(GREEN); i=getmaxx();  j=getmaxy();
	outtextxy(i/2-135,j/3+41,"M  E  D  I  C  A  L  S  T  O   R  E" );
	delay(300);
	elixir();
    //	LINECUT();
	password();
	loading();
   //	boarder();

}

void main___menu()
{
	clrscr();  // Clears text mode window
	frontpageandintro();
	intro();
	menu();

}



void  main()
{
	  main___menu();
}