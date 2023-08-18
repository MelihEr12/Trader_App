#include <QCoreApplication>
#include <QLocale>
#include <QTranslator>
#include <iostream>
#include "Stocks.h"
#include <fstream>
using namespace std;
int main()
{
    ifstream money;
    string user_money_data;
    money.open("data.txt");
    getline(money,user_money_data);



    int process=1 , choose=1 , adet=100;
    double invest=2234;

    cout << "please select your process" << endl;
    //cin >> process ;

    string corperation[2]={"ASELS","SASA"} ;

    user melih;
    melih.budget=stod(user_money_data);
    melih.name="Melih";

    Stocks asels;
    asels.num=adet;
    asels.name="Aselsan";
    asels.price=80;
    asels.supply=200000;

    Stocks sasa;
    asels.num=adet;
    sasa.name="Sasa Polyester";
    sasa.price=10;
    sasa.supply=200000;

    cout<<melih.budget<<endl;

    switch (process)
    {
    case 1 : //hisse alim
        cout << "select your stock to buy \n 1.ASELS ,2.SASA ; "<<endl;
        //cin>> choose ;
        if(choose==1)
        {
        cout << "enter the number ; "<<endl;
        //cin>>num ;
        melih.budget=melih.budget-(asels.price*adet);
        double dene=asels.buy();

        asels.supply=asels.supply-adet;
        cout<<"you buy:"<<asels.name<<endl;
        cout << "new budget is "<<melih.budget<<endl;
        cout<<"yeni aselsan fiyati"<<" "<<dene<<endl;

        }

        else
        {
         cout << "enter the number ; "<<endl;
         //cin>>num ;
         melih.budget=melih.budget-(sasa.price*adet);
         double dene=sasa.buy();
         cout<<"you buy:"<<sasa.name<<endl;

         cout << "new budget is "<<melih.budget<<endl;

         cout<<"yeni sasa fiyati"<<" "<<dene<<endl;
        }


    break;

    case 2 : //hisse satim
        cout << "select your stock to sell \n 1.ASELS ,2.SASA"<<endl;

        //cin>> choose ;
        if(choose==1)
        {

         cout << "enter the number ; "<<endl;
         //cin>>num ;

         melih.budget=melih.budget+(asels.price*adet);
         asels.supply=asels.supply+adet;
         double dene=asels.buy();

         cout<<"you sell:"<<asels.name<<endl;

         cout << "new budget is "<<melih.budget<<endl;

         cout<<"yeni aselsan fiyati"<<dene<<endl;
        }
        else
        {

         cout << "enter the number ; "<<endl;
         //cin>>num ;
         melih.budget=melih.budget+(sasa.price*adet);
         sasa.supply=sasa.supply+adet;
         double dene=sasa.buy();

         cout<<"you sell:"<<sasa.name<<endl;

         cout << "new budget is "<<melih.budget<<endl;

         cout<<"yeni sasa fiyati"<<dene<<endl;

        }
    break;


    case 3 : // toplam bakiye görüntüleme
        cout << "your bugdet is"<<melih.budget<<endl;

        break;

    case 4 : //list of stocks

        for (int i = 0; i < 2; ++i)
        {
            cout << corperation[i] << endl;
        }
        break;
    case 5 : // add money to your account
    {
        cout<< "enter the money"<<endl;
        //cin>>invest;
        melih.budget=melih.budget+invest;
        cout<<"new budget is"<<melih.budget<<endl;

    }
    }
    ofstream final_budget;
    final_budget.open("data.txt");
    final_budget<<melih.budget;

    final_budget.close();
    money.close();
    return 0;
}


//////////////////////////////////////////////////////////////////////////////////////////////////////////////


