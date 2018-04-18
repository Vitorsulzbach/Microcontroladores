Para todas as questões, considere que as variáveis `f`, `g`, `h`, `i` e `j` são do tipo inteiro (16 bits na arquitetura do MSP430), e que o vetor `A[]` é do tipo inteiro. Estas variáveis estão armazenadas nos seguintes registradores:

- f: R4
- g: R5
- h: R6
- i: R7
- j: R8
- A: R9

Utilize os registradores R11, R12, R13, R14 e R15 para armazenar valores temporários.

1. Traduza as seguintes linhas em C para a linguagem assembly do MSP430. Utilize somente as seguintes instruções: mov.w, add.w, sub.w, clr.w, dec.w, decd.w, inc.w e incd.w.

(a) `f *= 5;`

(b) `g *= 6;`

(c) `A[2] = 6*A[1] + 5*A[0];`

(d) `A[3] = 3*f - 5*h;`

(e) `A[5] = 6*(f - 2*h);`

Respostas

(a) clr.w R13
    add.w R4,R13
    add.w R4,R4
    add.w R4,R4
    add.w R13,R4
(b) clr.w R13
    add.w R5,R13
    add.w R5,R5
    add.w R5,R5
    add.w R13,R5
    add.w R13,R5
(c) clr.w R11
    add.w R10,R11
    add.w R9,R11
    add.w R11,R11
    add.w R11,R11
    add.w R10,R11
    add.w R9,R11
    add.w R10,R11
(d) clr.w R12
    add.w R4,R12
    add.w R6,R12
    add.w R4,R12
    add.w R6,R12
    add.w R4,R12
    add.w R6,R12
    add.w R6,R12
    add.w R6,R127
(e) clr.w R14
    add.w R4,R14
    add.w R4,R14
    add.w R14,R14
    mov.w R14,R15
    add.w R15,R14
    add.w R15,R14
