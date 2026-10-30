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
<img width="1122" height="498" alt="Screenshot 2026-10-30 135824" src="https://github.com/user-attachments/assets/7cbde650-ce60-4feb-87ab-5625f3289698" />
<img width="1917" height="963" alt="Screenshot 2026-10-30 135918" src="https://github.com/user-attachments/assets/756760d4-92fc-463e-8182-92a7fa38c7a0" />
<img width="837" height="420" alt="Screenshot 2026-10-30 140101" src="https://github.com/user-attachments/assets/4ebad4f2-ca06-4ba7-bbdb-dbf4b0081498" />
<img width="827" height="383" alt="Screenshot 2026-10-30 140110" src="https://github.com/user-attachments/assets/21a018f8-1307-4e36-ae89-f171ca5bd4ee" />
<img width="821" height="370" alt="Screenshot 2026-10-30 140242" src="https://github.com/user-attachments/assets/87e20b6e-c85a-41f6-97c2-8d9dfad84418" />
inal Output Summary
Operation	Input (Example)	Result (Hex)	Result (Decimal)
Addition	10, 2	0CH	12
Subtraction	10, 2	08H	8
Multiplication	10 × 2	14H	20
Division	10 ÷ 2	05H / 00H	5 Quotient / 0 Remainder
## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
