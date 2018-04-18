1. Quais as diferenças entre os barramentos de dados e de endereços?

2. Quais são as diferenças entre as memórias RAM e ROM?

3. Considere o código abaixo:

```C
#include <stdio.h>
int main(void)
{
	int i;
	printf("Insira um número inteiro: ");
	scanf("%d", &i);
	if(i%2)
		printf("%d eh impar.\n");
	else
		printf("%d eh par.\n");
	return 0;
}
```

Para este código, responda: (a) A variável `i` é armazenada na memória RAM ou ROM? Por quê? (b) O programa compilado a partir deste código é armazenado na memória RAM ou ROM? Por quê?

4. Quais são as diferenças, vantagens e desvantagens das arquiteturas Harvard e Von Neumann?

5. Considere a variável inteira `i`, armazenando o valor `0x8051ABCD`. Se `i` é armazenada na memória a partir do endereço `0x0200`, como ficam este byte e os seguintes, considerando que a memória é: (a) Little-endian; (b) Big-endian.

6. Sabendo que o processador do MSP430 tem registradores de 16 bits, como ele soma duas variáveis de 32 bits?

Respostas

1. O barramento de dados transmite o dado a ser gravado/lido pela memória ou pelo registrador, o barramento de endereço transmite o endereço da memória em que o dado deve ser lido ou gravado.

2. A memória RAM é mais rápida porem é volátil, ou seja, se apaga quando o microcontrolador é desligado, já a memória ROM é não volatil, porem é mais lenta.

3. (a) A variável 'i' é armazenada na memória RAM pois é a mesma é uma variavel criada pelo programa simplismente para executar um loop, caso a mesma precise ser armazenada na ROM um comando adicinal deve ser executado requerindo a gravação. (b) O programa deve ser armazenado na memória ROM para que quando o microcontrolador seja desligado e religado o mesmo ainda se recorde do código.

4.  A arquitetura Harvard possui um barramento de dados e endereço separado para a memória RAM e ROM, o que aumenta a complexidade e preço do projeto porem o torna mais eficiente, já a arquitetura de Von Neumann possui só um barramento de dados e de endereço o que torna o projeto mais barato porém menos eficiente.

5. (a) Little endian

0x0200 -> DC
0x0201 -> AB
0x0202 -> 80
0x0203 -> 51

(a) Big endian

0x0200 -> 80
0x0201 -> 51
0x0202 -> AB
0x0203 -> DC

6. O MIPS armazena os números em dois registradoires cada número, totalizando 4 registadores para o armazenamento dos números a serem somados, depois ele soma dos dois registradores de menores significancia e caso haja um carry o mesmo soma esse carry ne algum dos números de maior significancia, para então somar os dois de maiores significancia, a flag carry indica se houve overflow ou não.
