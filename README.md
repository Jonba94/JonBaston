# JonBaston
Casino_Peli
#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>

using namespace std;

void drawLine (int n, char symbol);
void saannot();


int main()
{
    string pelaajaNimi;
    float saldo; /* Pelaajan saldo*/
    float panos;
    int arvaus;
    int nopat; /* Tietokoneen numero*/
    char valinta;

    srand(time(0));

    cout << "Tervetuloa Casino Peliin\n\n\n\n\n";


    cout <<"\n\nSy"<< char(148) <<"t"<< char(132) <<" Nimesi : ";
    getline(cin, pelaajaNimi); /* Tallentaa pelaajan nimen*/

    cout <<"\n\nSy"<< char(148)<< "t" << char(132)<< " raham" << char(132)<<char(132)<<  "r"<< char(132)<< "peli"<<char(132)<<" varten:"<<char(36)<< " ";
    cin >> saldo;

    do
    {
        system("cls"); /* Tyhjentää muistin/ruudun */
        saannot();
        cout << "\n\nNykyinen saldosi on "<<char(36)<< "" << saldo <<"\n\n";

                /* Pelaajan panos*/

        do
        {
            cout << pelaajaNimi<< ", sy"<<char(148)<<"t"<<char(132)<<" panoksen m"<<char(132)<<char(132)<<"r"<<char(132)<<":"<<char(36)<<"\n\n";
            cin>>panos;
            if (panos > saldo)
                cout << "Panoksesi on suurempi kuin t"<<char(132)<<"m"<<char(132)<<"n hetkinen saldosi\n"
                        <<"\nSy"<<char(148)<<"t"<<char(132)<<" panos uudestaan\n ";

        }while(panos > saldo);

        /*Pelaajan Numerot*/

        do
        {
            cout << "\nArvaa numero 1-10 v"<<char(132)<<"lilt"<<char(132)<<":\n";
            cin >> arvaus;
            if (arvaus <= 0 || arvaus > 10)
                cout << "Tarkista sy"<<char(148)<<"tetty numero!!! Numeron pit"<<char(132)<<char(132)<<" olla 1-10 v"<<char(132)<<"lill"<<char(132)<<".\n"
                << "\nSyötä numero uudestaan\n";
        }while (arvaus <=0 || arvaus > 10);

        nopat = rand() %10 +1; /*Valitsee satunnaisen numeron 1-10 väliltä*/

        if (nopat==arvaus)
        {
            cout << "Onnittelut! Voitit!\n" << panos * 10;
            saldo = saldo + panos * 10;
        }
        else
        {
            cout << "Ei voittoa!\n" /*<< panos << "\n"*/;
            saldo = saldo - panos;
        }
        cout << "\nVoittava numero oli: \n" << nopat <<"\n";
        cout << "\n"<< pelaajaNimi << ", Saldosi on " <<saldo<< "\n";
        if (saldo == 0)
        {
            cout << "Sinulla ei ole saldoa j"<<char(132)<<"ljell"<<char(132)<<"";
            break;
        }
        cout << "\nHaluatko pelata uudestaan? (y/n)";
        cin >> valinta;

    }while (valinta == 'Y' || valinta == 'y');
    return 0;

}

void saannot()
{
    system ("cls");
    cout << "Pelin s"<<char(132)<<char(132)<<"nn"<<char(148)<<"t!\n";
    cout << "1. Valitse numero 1-10 v"<<char(132)<<"lill"<<char(132)<<"\n";
    cout << "2. Jos voitat, voitat panoksesi kymmenkertaisena\n";
    cout << "3. Jos h"<<char(132)<<"vi"<<char(132)<<"t menet"<<char(132)<<"t panoksesi";

}
