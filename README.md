# Traffic-Controller
Traffic light controller is a basic microcontroller project based on 8051
#include <reg51.h>
sbit RED0=P0^0;
sbit GREEN0=P0^1;
sbit YELLOW0=P0^2;
sbit RED1=P1^0;
sbit GREEN1=P1^1;
sbit YELLOW1=P1^2;
sbit RED2=P2^0;
sbit GREEN2=P2^1;
sbit YELLOW2=P2^2;
sbit RED3=P3^0;
sbit GREEN3=P3^1;
sbit YELLOW3=P3^2;
void delayg();
void delayy();
void traffic0();
void traffic1();
void traffic2();
void traffic3();
void delayg()
{
	 int count=0;
 while(count!=2500)
  {
   TMOD=0x01;  //16-bit timer0 selected in MODE 1
   TH0=0xF8;   // Loading high byte in TH
   TL0=0xCD;   // Loaded low byte in TL
   TR0=1;      // Running the timer
    while(!TF0);   //Checking the timer flag register if it is not equal to 1 
   TR0 = 0;      // If TF0=1 stop the timer
   TF0 = 0;      // Clear the Timer Flag bit for next calculation

   count++;
  }
}
void delayy()
{
 int count=0;
 while(count!=500)
  {
   TMOD=0x01;  //16-bit timer0 selected in MODE 1
   TH0=0xF8;   // Loading high byte in TH
   TL0=0xCD;   // Loaded low byte in TL
   TR0=1;      // Running the timer
    while(!TF0);   //Checking the timer flag register if it is not equal to 1 
   TR0 = 0;      // If TF0=1 stop the timer
   TF0 = 0;      // Clear the Timer Flag bit for next calculation

   count++;
  }
}
void main()
{
RED0=0;
RED1=0;
RED2=0;
RED3=0;
while(1)
{
traffic0();
traffic1();
traffic2();
traffic3();
}
}
void traffic0()
{
RED0=1;
GREEN0=0;
delayg();
GREEN0=1;
YELLOW0=0;
delayy();
YELLOW0=1;
RED0=0;
}
void traffic1()
{
RED1=1;
GREEN1=0;
delayg();
GREEN1=1;
YELLOW1=0;
delayy();
YELLOW1=1;
RED1=0;
}
void traffic2()
{
RED2=1;
GREEN2=0;
delayg();
GREEN2=1;
YELLOW2=0;
delayy();
YELLOW2=1;
RED2=0;
}
void traffic3()
{
RED3=1;
GREEN3=0;
delayg();
GREEN3=1;
YELLOW3=0;
delayy();
YELLOW3=1;
RED3=0;
}
