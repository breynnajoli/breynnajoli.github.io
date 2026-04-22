---
title: "🇰🇪 Simple & Compound Interest Calculator"
date: 2026-04-22 15:54:00 +0300
categories: [Projects, C++]
tags: [cpp, finance, codeblocks, software-development]
---
A robust C++ console application designed to calculate investment returns using real-world Kenyan financial parameters. 

## 🚀 Key Features
* **Dual Calculation Modes:** Computes both Simple and Compound interest based on user preference.
* **Tax Integration:** Automatically deducts a 5% Withholding Tax (WHT) to provide the true net interest.
* **Localized Outputs:** Formats all financial results in Kenyan Shillings (KSH).
* **Maturity Projection:** Calculates the exact month and year of investment maturity.
* **Input Validation:** Features robust error handling to prevent crashes from invalid user inputs.

---

## 💻 The Source Code

 * Project: Kenyan Finance & Tax Calculator
 * Author: Breyn Bush Najoli
 * Date: April 2026
 * Copyright (c) 2026 Breyn Bush Najoli. All rights reserved

#include <iostream>
#include <cmath>
#include <iomanip>
using namespace std;

string Months[]={"", "January","February", "March", "April",
                    "May", "June", "July", "August", "September",
                    "October","November", "December"
};

// Function to handle numeric inputs and prevent crashing on invalid characters
double GetNumber(string prompt ){
    double value;
    cout<<prompt<<endl;
    while (true){
        if (cin>>value && (cin.peek()=='\n' || cin.peek()== ' ')){
            break;
        }
        else {
            cout<< "Invalid input, Please enter numbers only: ";
            cin.clear();
            cin.ignore(1000, '\n');
        }
    }return value;
}

// Main logic for calculating interest, taxes, and maturity dates
void intrest(double deposit, double rate, int monthno) {
    double final_value;
    double r=rate/12;
    double t=1;
    double Total_intrest=0.0;
    double Total_amount=0.0;
    double Tax;
    double netInterest;
    int i=1;
    int n;
    int maturity_month;
    int maturity_year;
    
    cout<< "\nHow many months are you investing? ";
    while (true){
        if (cin>>n && (cin.peek()=='\n' || cin.peek()== ' ')){
            break;
        }
        else {
            cout<< "Invalid number of months. Please enter a number(s): ";
            cout<< "\nHow many months are you investing? ";
            cin.clear();
            cin.ignore(1000, '\n');
        }
    }
    
    int start_year;
    cout<< "Which year did you invest or wish to invest? ";
    while(true){
        if(cin>>start_year && start_year>=1900 && start_year<=9999){
            break;
        }
        else {
            cout<< "Invalid year Entered...."<<endl;
            cout<< "Enter a valid year e.g. 2026: "<<endl;
            cout<<"Enter: ";
            cin.clear();
            cin.ignore(1000, '\n');
        }
    }

    // Calculating the maturity date
    int endno=monthno+(n-1);
    maturity_year=start_year+(endno/12);
    if (endno<12 || endno>12){
        maturity_month=endno%12;
    }
    else {
        maturity_month=endno;
    }
    
    cout<< "\nWhich formula would you like to use?"<<endl;
    cout<< "\nA-> Simple Interest"<<endl;
    cout<< "\nB->Compound Interest"<<endl;
    cout<< "\nQ->Quit"<<endl;
    cout<< "Enter: ";
    char formula1;
    
    while(true){
        cin>>formula1;
        if (formula1=='A' || formula1== 'a'){
            while (i<=n){
                Total_intrest+=deposit*rate*i/n;
                i++;
            }
            Total_amount=deposit*n+Total_intrest;
            Tax=Total_intrest*0.05; // 5% Withholding Tax
            netInterest=Total_amount-Tax;
            
            cout << "\n========================================" << endl;
            cout << "            RESULTS SUMMARY              " << endl;
            cout << "========================================" << endl;
            cout<< "\nInterest after "<<n<< " month(s) is expected to mature on: "<<Months[maturity_month]<<" "<<maturity_year<<endl;
            cout<< "Gross simple interest is: KSH "<<Total_intrest<<endl;
            cout<< "Total simple interest amount: KSH "<<Total_amount<<endl;
            cout<< "WHT Tax of 5%: KSH "<<Tax<<endl;
            cout<< "Final net interest: KSH "<<netInterest<<endl;
            cout<<"\n\n-----------THANK YOU FOR USING CALCULATOR!-----------"<<endl;
            break;
        }
        else if (formula1== 'B' || formula1== 'b'){
            final_value=deposit*(pow(1+r,n*t)-1)/r;
            double final_intrest=final_value-(deposit*n);
            Tax=final_intrest*0.05; // 5% Withholding Tax
            netInterest=final_value-Tax;
            
            cout << "\n========================================" << endl;
            cout << "            RESULTS SUMMARY              " << endl;
            cout << "========================================" << endl;
            cout<< "\nInterest after "<<n<< " month(s) is expected to mature on: "<<Months[maturity_month]<<" "<<maturity_year<<endl;
            cout<< "Gross compound interest is: KSH "<<final_intrest<<endl;
            cout<< "Total compound amount: KSH "<<final_value<<endl;
            cout<< "WHT Tax of 5%: KSH "<<Tax<<endl;
            cout<< "Final net interest: KSH "<<netInterest<<endl;
            cout<<"\n\n-----------THANK YOU!-----------"<<endl;
            break;
        }
        else if(formula1== 'Q' || formula1== 'q'){
            cout<<"\n\n-----------THANK YOU FOR USING THE CALCULATOR------------"<<endl;
            break;
        }
        else {
            cout<< "Invalid Character......"<<endl;
            cout<< "\nPlease enter formula or quit (A, B, or Q): ";
        }
    }
}

int main()
{
    cout << "============================================" << endl;
    cout << "   Simple and Compound Interest Calculator   " << endl;
    cout << "   Developed by Breyn Bush Najoli            " << endl;
    cout << "============================================" << endl;
    
    // Formatting output to 2 decimal places for currency
    cout<<fixed<<setprecision(2);
    
    cout<< "\n\nEnter Q to Quit or Press any key to continue: "<<endl;
    string Quit;
    cin>>Quit;
    
    if(Quit== "q" || Quit== "Q" || Quit== "Quit" || Quit== "quit"){
        cout<<"\n\n-----------THANK YOU FOR USING THE CALCULATOR------------"<<endl;
    }
    else {
        double deposit=GetNumber("\n\nWhat is your monthly deposit amount: ");
        double Rate=GetNumber("\nWhat is the company's interest rate in (%): ");
        double rate=Rate/100;
        
        cout<< "\nSelect the month you'll start investing: "<<endl;
        for (int i=1;i<=12;i++ ){
            cout<<i<< "->"<<Months[i]<<endl;
        }
        
        int monthno;
        cout<< "\nEnter: ";
        while (true){
            if(cin>>monthno && monthno>=1 && monthno<=12 && (cin.peek()=='\n' || cin.peek()== ' ')){
                intrest(deposit,rate,monthno);
                break;
            }
            else {
                cout<< "Invalid month number. Please enter a number between 1 and 12: ";
                cin.clear();
                cin.ignore(1000, '\n');
            }
        }
    }
    return 0;
}
