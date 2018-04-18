1. Dada uma variável `a` do tipo `char` (um byte), escreva os trechos de código em C para:
	(a) Somente setar o bit menos significativo de `a`.
	(b) Somente setar dois bits de `a`: o menos significativo e o segundo menos significativo.
	(c) Somente zerar o terceiro bit menos significativo de `a`.
	(d) Somente zerar o terceiro e o quarto bits menos significativo de `a`.
	(e) Somente inverter o bit mais significativo de `a`.
	(f) Inverter o nibble mais significativo de `a`, e setar o nibble menos significativo de `a`. 

2. Considerando a placa Launchpad do MSP430, escreva o código em C para piscar os dois LEDs ininterruptamente.

3. Considerando a placa Launchpad do MSP430, escreva o código em C para piscar duas vezes os dois LEDs sempre que o usuário pressionar o botão.

4. Considerando a placa Launchpad do MSP430, faça uma função em C que pisca os dois LEDs uma vez.

5. Reescreva o código da questão 2 usando a função da questão 4.

6. Reescreva o código da questão 3 usando a função da questão 4.

Respostas:


1. (a)
	a |= 1;
   (b)
	a |= 3;
   (c)
	a &= 0x11111011b;
   (d)
   	a &= 0x11110011b;
   (e)
   	if((a & 128)== 128) {
	    a &= 128;
	} else {
	    a |= 128;
	}
	
	
2.


void main(void)
{
	WDTCTL = WDTPW | WDTHOLD;
	P1DIR |= 0xff;
	int s =1;
	while(s==1){
	int    i=0;
	while(i<10000) {
	    i++;
	}
	P1OUT= 65;
	i=0;
    while(i<10000) {
        i++;
    }
    P1OUT= 0;
	}
}


3.


void main(void)
{
	WDTCTL = WDTPW | WDTHOLD;		
	P1DIR = 65;					
	P1REN = 8;
	P1OUT=8;
	while(1){
	if ((P1IN & 8)== 0){
	    P1OUT |= 65;
	} else {
	    P1OUT = 8;
	}
	}
}


4. e 5. Pisca LEDs usando a função Pisca();


void main(void)
{
	WDTCTL = WDTPW | WDTHOLD;	
	P1DIR = 65;					
	P1REN = 8;
	P1OUT=8;
	while(1){
	pisca();
    int g=0;
    while(g<10000) {
        g++;
    }
    g=0;
	}
}

void pisca(void){
    P1OUT |= 65;
    int g = 0;
    while(g<10000) {
        g++;
    }
    g=0;
    P1OUT &=~65;
    return;
}


6.


#include <msp430.h>				

void main(void)
{
    WDTCTL = WDTPW | WDTHOLD;       // stop watchdog timer
    P1DIR = 65;                 // configure P1.1 as output
    P1REN = 8;
    P1OUT=8;
    while(1){
    if ((P1IN & 8)== 0){
        pisca();
    } else {
        P1OUT = 8;
    }
    }
}
void pisca(void){
    P1OUT |= 65;
    int g = 0;
    while(g<10000) {
        g++;
    }
    g=0;
    P1OUT &=~65;
    return;
}
