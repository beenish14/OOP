# OOP
Final Project of OOP.
#include<iostream>
#include<string>
#include<conio.h>
using namespace std;
static int count=0;
class Items
{
	protected:
		string category;
		string itemName;
		float pricePerUnit;
		float price;
		float quantity;
	public:

		virtual void itemSelection()=0;
		virtual string getItemName()=0;
		virtual float getPriceUnit()=0;
		virtual float getQuantity()=0;
		virtual float getPrice()=0;
};
class Menu
{
	private:
		float totalPrice;
		float tax;
		float grandTotal;
		float payment;
		float change;
		string iName[100];
		float pUnit[100];
		float quantity[100];
		float price[100];
		
	public:
		Menu(string iN[],float pU[],float q[],float p[])
		{
			totalPrice=0;
			for(int i=0;i<count;i++)
			{
				iName[i]=iN[i];
				pUnit[i]=pU[i];
				quantity[i]=q[i];
				price[i]=p[i];
			}
		}
		
		void showMenu()
		{
			system("cls");
			cout<<"\n\n\t\t\t\teGrocery\n";
			cout<<"\t\t\tAll your needs at one click\n\n\n";
			cout<<"Serial No.\tItem\t\t\tUnit Price\tQuantity\tPrice\n\n\n";
			for(int i=0 ; i<count ; i++)
			{
				
				cout<<i+1<<".\t\t";
				if(iName[i].length()<8)
					cout<<iName[i]<<"\t";
				else
					cout<<iName[i];
				cout<<"\t\t"<<pUnit[i]<<"\t\t"<<quantity[i]<<"\t\tRs. "<<price[i]<<"\n";
			}
			cout<<"\n\n-------------------------------------------------------------------------------\n\n";
			cout<<"\t\t\t\t\t\tTotal\t\t:\tRs. ";
			for(int i=0;i<count;i++)
			{
				totalPrice+=price[i];
			}
			cout<<totalPrice;
			tax=totalPrice*0.06;
			cout<<"\n\t\t\t\t\t\tTax\t\t:\tRs. "<<tax;
			grandTotal=totalPrice+tax;
			cout<<"\n\n\t\t\t\t\t\tGrand Total\t:\tRs. "<<grandTotal;
			
			
			do
			{
				cout<<"\n\n\t\t\t\t\tPlease make the payment : \tRs. ";
				cin>>payment;
				if(payment<grandTotal)
				{
					cout<<"\n\n\t\t\t\t\t\tInsufficient Payment\n";
				}
			}while(payment<grandTotal);
			
			change=payment-grandTotal;
			cout<<"\n\t\t\t\t\t\t\tChange\t:\tRs. "<<change;
			cout<<"\n\n\t\t\t\t\t\tPayment Successful!\n\n";
			cout<<"\n\n\t\t   Your order will reach you doorstep in 2 hours.\n";
			cout<<"\n\n\t\t\tThank you for Shopping at eGrocery.\n";
			cout<<"\t\t\t\tHave a nice day!";
			cout<<"\n\n____________\n\n";
	}
};
class Cart
{
	private:
		string iName[100];
		float quantity[100];
		
	public:
		Cart(string iN[],float q[])
		{
			for(int i=0;i<count;i++)
			{
				iName[i]=iN[i];
				quantity[i]=q[i];
			}
		}
		void showOrder()
		{
		
			system("cls");
			cout<<"\n\n\t\t\t\t eGrocery\n";
			cout<<"\t\t\tAll your needs at one click\n\n\n";
			cout<<"Item\t\t\tQuantity\n\n\n";
			for(int i=0 ; i<count ; i++)
			{
				if(iName[i].length()<8)
					cout<<iName[i]<<"\t";
				else
					cout<<iName[i];
				cout<<"\t\t"<<quantity[i]<<"\n";
			}
			cout<<"\n\n-------------------------------------------------------------------------------\n\n";
		}

		
};
class Fruits:public Items
{
	public:
		Fruits()
		{
			count++;
			
		}
		void calculatePrice()
			{
				cout<<"\nHow much "<<itemName<<" do you require (Enter in Kg) : ";
				cin>>quantity;
				price=quantity*pricePerUnit;
				cout<<"Price of "<<quantity<<" kg "<<itemName<<" : "<<price<<" Rs\n\n";
				cout<<quantity<<" kg "<<itemName<<" added to your cart\n";
				cout<<"\n\n----------------------------------------------------------------------------";
			}
		void itemSelection()
		{
			cout<<"Select from the following Fruits:\n\n";
			cout<<"1. Apple       --------   Rs 130 per kg\n";
			cout<<"2. Orange      --------   Rs 110 per kg\n";
			cout<<"3. Pineapple   --------   Rs 200 per kg\n";
			cout<<"4. Mango       --------   Rs 180 per kg\n";
			cout<<"5. Strawberry  --------   Rs 170 per kg\n";
			cout<<"6. Peach       --------   Rs 140 per kg\n";
			cout<<"7. Guava       --------   Rs 100 per kg\n";
			cout<<"8. Grapes      --------   Rs 125 per kg\n";
			int option;
			cout<<"\n\nSelection : ";
			cin>>option;
			if(option==1)
			{
				itemName="Apple";
				pricePerUnit=130;
				calculatePrice();
			}
			else if(option==2)
			{
				itemName="Orange";
				pricePerUnit=110;
				calculatePrice();
			}
			else if(option==3)
			{
				itemName="Pineapple";
				pricePerUnit=200;
				calculatePrice();
			}
			else if(option==4)
			{
				itemName="Mango";
				pricePerUnit=180;
				calculatePrice();
			}
			else if(option==5)
			{
				itemName="Strawberry";
				pricePerUnit=170;
				calculatePrice();
			}
			else if(option==6)
			{
				itemName="Peach";
				pricePerUnit=140;
				calculatePrice();
			}
			else if(option==7)
			{
				itemName="Guava";
				pricePerUnit=100;
				calculatePrice();
			}
			else if(option==8)
			{
				itemName="Grapes";
				pricePerUnit=125;
				calculatePrice();
			}
		}
		string getItemName()
		{
			return itemName;
		}
		float getPriceUnit()
		{
			return pricePerUnit;
		}
		float getQuantity()
		{
			return quantity;
		}
		float getPrice()
		{
			return price;
		}
};
class Vegetables:public Items
{
	public:
		Vegetables()
		{
			count++;
			
		}
		void calculatePrice()
		{
			cout<<"\nHow much "<<itemName<<" do you require (Enter in Kg) : ";
			cin>>quantity;
			price=quantity*pricePerUnit;
			cout<<"Price of "<<quantity<<" kg "<<itemName<<" : "<<price<<" Rs\n\n";
			cout<<quantity<<" kg "<<itemName<<" added to your cart\n";
			cout<<"\n\n----------------------------------------------------------------------------";
		}
		void itemSelection()
		{
			cout<<"\n\n----------------------------------------------------------------------------\n\n";
			cout<<"Select from the following Vegetables:\n\n";
			cout<<"1. Onion        --------   Rs 50 per kg\n";
			cout<<"2. Potato       --------   Rs 60 per kg\n";
			cout<<"3. Tomato       --------   Rs 120 per kg\n";
			cout<<"4. Cauliflower  --------   Rs 60 per kg\n";
			cout<<"5. Ginger       --------   Rs 340 per kg\n";
			cout<<"6. Garlic       --------   Rs 300 per kg\n";
			cout<<"7. Carrot       --------   Rs 50 per kg\n";
			cout<<"8. Turnip       --------   Rs 50 per kg\n";
			int option;
			cout<<"\n\nSelection : ";
			cin>>option;
			if(option==1)
			{
				itemName="Onion";
				pricePerUnit=50;
				calculatePrice();
			}
			else if(option==2)
			{
				itemName="Potato";
				pricePerUnit=60;
				calculatePrice();
			}
			else if(option==3)
			{
				itemName="Tomato";
				pricePerUnit=120;
				calculatePrice();
			}
			else if(option==4)
			{
				itemName="Cauliflower";
				pricePerUnit=60;
				calculatePrice();
			}
			else if(option==5)
			{
				itemName="Ginger";
				pricePerUnit=340;
				calculatePrice();
			}
			else if(option==6)
			{
				itemName="Garlic";
				pricePerUnit=300;
				calculatePrice();
			}
			else if(option==7)
			{
				itemName="Carrot";
				pricePerUnit=50;
				calculatePrice();
			}
			else if(option==8)
			{
				itemName="Turnip";
				pricePerUnit=50;
				calculatePrice();
			}
		}
		string getItemName()
		{
			return itemName;
		}
		float getPriceUnit()
		{
			return pricePerUnit;
		}
		float getQuantity()
		{
			return quantity;
		}
		float getPrice()
		{
			return price;
		}
};
class PulsesAndSpices:public Items
{
	public:
		PulsesAndSpices()
		{
			count++;
			
		}
		void calculatePrice()
		{
			cout<<"\nHow much "<<itemName<<" do you require (Enter in Kg) : ";
			cin>>quantity;
			price=quantity*pricePerUnit;
			cout<<"Price of "<<quantity<<" kg "<<itemName<<" : "<<price<<" Rs\n\n";
			cout<<quantity<<" kg "<<itemName<<" added to your cart\n";
			cout<<"\n\n----------------------------------------------------------------------------";
		}

		void itemSelection()
		{
			cout<<"\n\n----------------------------------------------------------------------------\n\n";
			cout<<"\nSelect from the following categories\n\n";
			cout<<"1. Dal Mash       --------  Rs 150 per kg\n";
			cout<<"2. Dal Chana      --------  Rs 180 per kg\n";
			cout<<"3. Dal Mong       --------  Rs 90 per kg\n";
			cout<<"4. Dal Masoor     --------  Rs 210 per kg\n";
			cout<<"5. White Chana    --------  Rs 195 per kg\n";
			cout<<"6. Garam Masala   --------  Rs 900 per kg\n";
			int option;
			cout<<"\n\nSelection : ";
			cin>>option;
			if(option==1)
			{
				itemName="Dal Mash";
				pricePerUnit=150;
				calculatePrice();
			}
			else if(option==2)
			{
				itemName="Dal Chana";
				pricePerUnit=180;
				calculatePrice();
			}
			else if(option==3)
			{
				itemName="Dal Mong";
				pricePerUnit=90;
				calculatePrice();
			}
			else if(option==4)
			{
				itemName="Dal Masoor";
				pricePerUnit=210;
				calculatePrice();
			}
			else if(option==5)
			{
				itemName="White Chana";
				pricePerUnit=195;
				calculatePrice();
			}
			else if(option==6)
			{
				itemName="Garam Masala";
				pricePerUnit=900;
				calculatePrice();
			}
		}
		string getItemName()
		{
			return itemName;
		}
		float getPriceUnit()
		{
			return pricePerUnit;
		}
		float getQuantity()
		{
			return quantity;
		}
		float getPrice()
		{
			return price;
		}
};
class RiceAndFlour:public Items
{
	public:
		RiceAndFlour()
		{
			count++;
		
		}
		void calculatePrice()
		{
			cout<<"\nHow much "<<itemName<<" do you require (Enter in Kg) : ";
			cin>>quantity;
			price=quantity*pricePerUnit;
			cout<<"Price of "<<quantity<<" kg "<<itemName<<" : "<<price<<" Rs\n\n";
			cout<<quantity<<" kg "<<itemName<<" added to your cart\n";
			cout<<"\n\n----------------------------------------------------------------------------";
		}

		void itemSelection()
		{
			cout<<"\n\n----------------------------------------------------------------------------\n\n";
			cout<<"\nSelect from the following categories\n\n";
			cout<<"1. Rice       --------  Rs 190 per kg\n";
			cout<<"2. Flour      --------  Rs 75 per kg\n";
			int option;
			cout<<"\n\nSelection : ";
			cin>>option;
			if(option==1)
			{
				itemName="Rice";
				pricePerUnit=190;
				calculatePrice();
			}
			else if(option==2)
			{
				itemName="Flour";
				pricePerUnit=75;
				calculatePrice();
			}
		}
		string getItemName()
		{
			return itemName;
		}
		float getPriceUnit()
		{
			return pricePerUnit;
		}
		float getQuantity()
		{
			return quantity;
		}
		float getPrice()
		{
			return price;
		}
};
class Beverages:public Items
{
	public:
		Beverages()
		{
			count++;
		
		}
		void calculatePrice()
		{
			cout<<"\nHow many "<<itemName<<" do you need : ";
			cin>>quantity;
			price=quantity*pricePerUnit;
			cout<<"Price of "<<quantity<<" "<<itemName<<" : "<<price<<" Rs\n\n";
			cout<<quantity<<" "<<itemName<<" added to your cart\n";
			cout<<"\n\n----------------------------------------------------------------------------";
		}
		
		void itemSelection()
		{
			cout<<"\n\n----------------------------------------------------------------------------\n\n";
			cout<<"\nSelect from the following categories of Frozen Foods\n\n";
			cout<<"1. Cold Drink     --------  Rs 100 per Bottle\n";
			cout<<"2. Juice          --------  Rs 175 per packet\n";
			cout<<"3. Mineral Water  --------  Rs 60 per packet\n";
			cout<<"4. Tin Can        --------  Rs 70 per tin\n";
			int option;
			cout<<"\n\nSelection : ";
			cin>>option;
			if(option==1)
			{
				itemName="Cold Drink";
				pricePerUnit=100;
				calculatePrice();
			}
			else if(option==2)
			{
				itemName="Juice";
				pricePerUnit=175;
				calculatePrice();
			}
			else if(option==3)
			{
				itemName="Mineral Water";
				pricePerUnit=60;
				calculatePrice();
			}
			else if(option==4)
			{
				itemName="Tin Can";
				pricePerUnit=70;
				calculatePrice();
			}
		}
		string getItemName()
		{
			return itemName;
		}
		float getPriceUnit()
		{
			return pricePerUnit;
		}
		float getQuantity()
		{
			return quantity;
		}
		float getPrice()
		{
			return price;
		}
};
int main()
{
	system("color E0");
	char username;
	int password;
	
   cout<<"Enter Your Username:"<<endl;
   cin>>username;
   
   cout<<"Enter Your Password:"<<endl;
   cin>>password;
   
   if(username=='B' && password==12345)
   
   {	cout<<"YOU HAVE LOGINED SUCCESSFULLY!"<<endl;
   
  cout<<("Press any Key to clear the screen!\n");
   getch();
   system("cls");
   
	cout<<"\n\n\n";
	cout<<"+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++";
	cout<<"\n+++\t\t\t\t\t\t\t\t\t+++\n+++\t\t\t\t\t\t\t\t\t+++\n";
	cout<<"+++\t\t\t   ONLINE GROCERY STORE\t\t\t\t+++\n+++\t\t\t\t\t\t\t\t\t+++\n";
	cout<<"+++\t\t\t\tProject By:\t\t\t\t+++\n+++\t\t\t\t\t\t\t\t\t+++\n";
	cout<<"+++\t\t\t\t\t\t\t\t\t+++\n+++\t\t\tBEE223002  -  BEENISH ARSHAD\t\t\t+++\n";
	cout<<"+++\t\t\tBEE223004  -  KASHAN KAYANI\t\t\t+++\n";
	cout<<"+++\t\t\t\t\t\t\t\t\t+++\n+++\t\t\t\t\t\t\t\t\t+++\n+++\t\t\t\t\t\t\t\t\t+++\n";
	cout<<"+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++";
	cout<<"\n\n\n---------------------------------------------------------------------------\n\n";
	cout<<"\t\t\tWelcome to the eGrocery\n";
	cout<<"\n\t\t      All your needs at one click!\n";

	
	string ItemName[100];
	float PriceUnit[100];
	float Quantity[100];
	float Price[100];
	
	int option;
	char opt;
	do
	{
		cout<<"\n\nSelect from the following Menu\n\n";
		cout<<"1.  Fruits\n2.  Vegetables";
		cout<<"\n3.  Pulses and Spices\n4.  Rice and Flour\n";
		cout<<"5.  Drinks";
		cout<<"\n\nEnter your Selection : ";
		cin>>option;
		

		if(option==1)
		{
			Fruits f;
			f.itemSelection();
			ItemName[count-1]=f.getItemName();
			PriceUnit[count-1]=f.getPriceUnit();
			Quantity[count-1]=f.getQuantity();
			Price[count-1]=f.getPrice();
		}
		else if(option==2)
		{
			Vegetables v;
			v.itemSelection();
			ItemName[count-1]=v.getItemName();
			PriceUnit[count-1]=v.getPriceUnit();
			Quantity[count-1]=v.getQuantity();
			Price[count-1]=v.getPrice();
		}
	
		else if(option==3)
		{
			PulsesAndSpices ps;
			ps.itemSelection();
			ItemName[count-1]=ps.getItemName();
			PriceUnit[count-1]=ps.getPriceUnit();
			Quantity[count-1]=ps.getQuantity();
			Price[count-1]=ps.getPrice();
		}
		else if(option==4)
		{
			RiceAndFlour rf;
			rf.itemSelection();
			ItemName[count-1]=rf.getItemName();
			PriceUnit[count-1]=rf.getPriceUnit();
			Quantity[count-1]=rf.getQuantity();
			Price[count-1]=rf.getPrice();
		}
	
		else if(option==5)
		{
			Beverages b;
			b.itemSelection();
			ItemName[count-1]=b.getItemName();
			PriceUnit[count-1]=b.getPriceUnit();
			Quantity[count-1]=b.getQuantity();
			Price[count-1]=b.getPrice();
		}
		
		else
			cout<<"Invalid input.";
		cout<<"\n\n\nDo you want to order anything else (Y/N) : ";
		cin>>opt;
		cout<<"\n\n----------------------------------------------------------------------------";
		
	}while(opt=='Y' || opt=='y');
	cout<<"\n\n__________";
	
	cout<<"\n\nYour order is complete!\n\n";
	
	do
	{
		cout<<"\n\nSelect from the following options\n\n";
		cout<<"1. View my Cart\n";
		cout<<"2. Proceed to Bill\n";
		cout<<"\nSelection : ";
		cin>>option;
		if (option==1)
		{
			Cart c1(ItemName,Quantity);
			c1.showOrder();
		}
		else if (option==2)
		{
			Menu m1(ItemName,PriceUnit,Quantity,Price);
			m1.showMenu();
		}
	}while(option==1);
		
	cout<<"\n\n\n\n";
	return 0;
}
else
{
	cout<<"INCORRECT USERNAME OR PASSWORD!"<<endl;
}
}
