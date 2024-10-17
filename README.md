/*
 * Project1.c
 *
 * Created: 8/27/2024 2:55:03 PM
 * Author : Carissa Ainsworth
 */ 

#define F_CPU 16000000UL //16MHz clock
#include <avr/io.h> //utilize functions 
#include <util/delay.h>

#define LEDON PORTB |= (1<<PORTB5)
#define LEDOFF PORTB &= ~(1<<PORTB5)

//Dot function
	void dot()
	{
		LEDON;// turn on LED
		_delay_ms(200);	//delay 200ms light up (dot time)
		LEDOFF; // turn off LED 
		_delay_ms(200);	//delay 200ms light off (space between units)
	}
	
//Dash function 
	void dash()
	{
		LEDON;//turn on LED
		_delay_ms(600);// delay 600ms light up (dash time)
		LEDOFF; //turn off LED
		_delay_ms(200);//delay 200ms light off (space between units)
	}

//Letter spacing function
	void space()
	{
		_delay_ms(600);
	}
	
//Morse Code 
	void mcode(char sym)//sym to represent symbol to pull up in letter cases
	{
		switch(sym)
		{
			case ' ':
				_delay_ms(1400);//delay 1400ms light off (space between words)
				break;
				
			case 'A':case'a':
				dot();
				dash();
				space(); 
				break;
			
			case 'B':case 'b':
				dash();
				dot();
				dot();
				dot();
				space();
				break;
				
			case 'C':case 'c':
				dash();
				dot();
				dash();
				dot();
				space(); 
				break;
				
			case 'D':case 'd':
				dash();
				dot();
				dot();
				space();
				break;
				
			case 'E':case 'e':
				dot();
				space(); 
				break;
			
			case 'F':case 'f':
				dot();
				dot();
				dash();
				dot();
				space();
				break;
				
			case 'G':case 'g':
				dash();
				dash();
				dot();
				space();
				break;
			
			case 'H':case 'h':
				dot();
				dot();
				dot();
				dot();
				space(); 
				break;
				
			case 'I':case 'i':
				dot();
				dot();
				space();
				break;
				
			case 'J':case 'j':
				dot();
				dash();
				dash();
				dash();
				space();
				break;
				
			case 'K':case 'k':
				dash();
				dot();
				dash();
				space();
				break;
				
			case 'L':case 'l':
				dot();
				dash();
				dot();
				dot();
				space();
				break;
				
			case 'M':case 'm':
				dash();
				dash();
				space();
				break;
				
			case 'N':case 'n':
				dash();
				dot();
				space();
				break;
				
			case 'O':case 'o':
				dash();
				dash();
				dash();
				space();
				break;
				
			case 'P':case 'p':
				dot();
				dash();
				dash();
				dot();
				space();
				break;
				
			case 'Q':case 'q':
				dash();
				dash();
				dot();
				dash();
				space();
				break;
			
			case 'R':case 'r':
				dot();
				dash();
				dot();
				space(); 
				break;
				
			case 'S':case 's':
				dot();
				dot();
				dot();
				space(); 
				break;
				
			case 'T':case 't':
				dash();
				space();
				break; 
				
			case 'U':case 'u':
				dot();
				dot();
				dash();
				space();
				break;
			
			case 'V':case 'v':
				dot();
				dot();
				dot();
				dash();
				space(); 
				break;
				
			case 'W':case 'w':
				dot();
				dash();
				dash();
				space();
				break;
				
			case 'X':case 'x':
				dash();
				dot();
				dot();
				dash();
				space(); 
				break;
				
			case 'Y':case 'y':
				dash();
				dot();
				dash();
				dash();
				space(); 
				break;
				
			case 'Z':case 'z':
				dash();
				dash();
				dot();
				dot();
				space();
				break;
				
			case '1':
				dot();
				dash();
				dash();
				dash();
				dash();
				space();
				break;
				
			case '2':
				dot();
				dot();
				dash();
				dash();
				dash();
				space();
				break;
			
			case '3':
				dot();
				dot();
				dot();
				dash();
				dash();
				space(); 
				break;
				
			case '4':
				dot();
				dot();
				dot();
				dot();
				dash();
				space();
				break;
				
			case '5':
				dot();
				dot();
				dot();
				dot();
				dot();
				space(); 
				break;
				
			case '6':
				dash();
				dot();
				dot();
				dot();
				dot();
				space();
				break;
				
			case '7':
				dash();
				dash();
				dot();
				dot();
				dot();
				space();
				break;
				
			case '8':
				dash();
				dash();
				dash();
				dot();
				dot();
				space();
				break;
				
			case '9':
				dash();
				dash();
				dash();
				dash();
				dot();
				space();
				break;
				
			case '0':
				dash();
				dash();
				dash();
				dash();
				dash();
				space();
				break;
		}
	}
	
//Read Morse String 
	void MorseString(const char* str) //cc is a pointer, cc pointers to constant units
	{
		while (*str!='\0') //continues if not a null value
		{
			mcode(*str); // collects the first string
			str++;	//moves to next unit in the string 
		}
	}
	
int main(void)
{
    DDRB|=(1<<DDB5); //Set B5 output pin 
    while (1) 
    {
			MorseString("Car 82");
			return 0;
    }
	
}


