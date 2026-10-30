# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.
Apparatus Required:
•	Laptop with internet connection
## Algorithm:
## For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
## For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.
## For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).
## For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.
## Program:
; ---------- ADDITION ----------
LDA 4150H
MOV B,A
LDA 4151H
ADD B
STA 4152H

; ---------- SUBTRACTION ----------
LDA 4150H
MOV B,A
LDA 4151H
SUB B
STA 4152H

; ---------- MULTIPLICATION ----------
MVI A,00H
MVI D,00H
LXI H,0020H
MOV B,M
INX H
MOV C,M
MUL_LOOP: ADD B
JNC NO_CARRY
INR D
NO_CARRY: DCR C
JNZ MUL_LOOP
STA 0022H
MOV A,D
STA 0023H

; ---------- DIVISION ----------
LXI H, 0020H
MOV A, M
INX H
MOV C, M

MVI D, 00H
MOV B, A

MOV A, C
ORA A
JZ STOP

MOV A, B

LOOP: CMP C
JC DIV_END
SUB C
INR D
JMP LOOP

DIV_END: STA 0025H
MOV A, D
STA 0024H

HLT

## Output:
<img width="1917" height="963" alt="Screenshot 2026-10-30 135918" src="https://github.com/user-attachments/assets/3855e378-0cb6-490d-98ac-8d41d2d2f08d" />

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
