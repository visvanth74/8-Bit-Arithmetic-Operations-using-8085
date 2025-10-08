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
IN 01H        ; Read input from port 0x01 into A
      

  MOV B,A       ; Save it in B

        IN 02H        ; Read input from port 0x02 into A
        ADD B         ; A = A + B

        OUT 03H       ; Send sum to port 0x03
        HLT           ; Stop execution
<img width="1321" height="544" alt="image" src="https://github.com/user-attachments/assets/06d8466b-c6c6-4f43-96f8-6fc7ecd2f178" />
IN 01H        ; Read first number (A) from port 0x01 into A
        MOV B,A       ; Save it in B

        IN 02H        ; Read second number (B) from port 0x02 into A
        MOV C,A       ; Save B in C

        MOV A,B       ; Restore first number into A
        SUB C         ; A = A - B

        OUT 03H       ; Output result to port 0x03
        HLT           ; End program
<img width="1243" height="540" alt="image" src="https://github.com/user-attachments/assets/a03c7d5e-a3e9-4f9b-bdf6-0707bdd30729" />
IN 01H ; Read first number (Multiplicand) into A
MOV C, A ; Store in C
IN 02H ; Read second number (Multiplier) into A
MOV B, A ; Store in B
MVI A, 00H ; Clear A to hold result
LOOP:
ADD C ; A = A + C
DCR B ; B = B - 1
JNZ LOOP ; Repeat until B = 0
OUT 06H ; Output the result to port 06H
HLT ; End of program
<img width="1221" height="537" alt="image" src="https://github.com/user-attachments/assets/862cfa6e-dee0-4bab-8846-ee8600b913ef" />
IN 01H         ; Read dividend into A
MOV C, A       ; Store dividend in C (for remainder tracking)
MVI A, 00H     ; Clear A for quotient
MOV D, A       ; Use D to store quotient

IN 02H         ; Read divisor into A
MOV B, A       ; Store divisor in B

DIV_LOOP:
MOV A, C       ; Load current remainder into A
CMP B          ; Compare remainder with divisor
JC END_DIV     ; If A < B, jump to END_DIV
SUB B          ; A = A - B
MOV C, A       ; Update remainder in C
INR D          ; Increment quotient
JMP DIV_LOOP   ; Repeat loop

END_DIV:
MOV A, D       ; Move quotient to A
OUT 03H        ; Output quotient to port 03H

MOV A, C       ; Move remainder to A
OUT 04H        ; Output remainder to port 04H

HLT            ; End program
<img width="1612" height="672" alt="image" src="https://github.com/user-attachments/assets/cb42bedc-7b4c-4283-97ff-21bcc24fe8e1" />

## Output:
## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
