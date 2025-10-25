# PALINDROME-IN-8051

## AIM:
To Write an assembly language program in 8051 to check whether a given  number is a palindrome or not

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

- # 8051 Palindrome Check Algorithm

## Step-by-Step Algorithm

1. **Start the program.**  
2. **Initialize program counter** at address `00H`.  
3. **Read input number** from **Port 0** and move it to the **Accumulator (A)**.  
4. **Load Register B** with `0AH` (decimal 10).  
5. **Divide A by B** → `A/B`:  
   - **A** = Quotient (Tens digit)  
   - **B** = Remainder (Ones digit)  
6. **Store digits:**  
   - Move **A → R0** (tens digit)  
   - Move **B → R1** (ones digit)  
7. **Reverse the number:**  
   - Move **R1 → A**  
   - Load **B = 0AH**  
   - Perform **MUL AB** → A = (ones × 10)  
   - Add **R0 (tens)** to **A** → A = reversed number  
8. **Compare reversed number** with the original number from Port 0 using **CJNE** instruction.  
9. **If equal:**  
   - Move `#0FFH` to **Port 1** → Indicate *Palindrome*.  
10. **If not equal:**  
    - Move `#00H` to **Port 1** → Indicate *Not Palindrome*.  
11. **Jump to DONE label** to end the program loop.  
12. **Stop (infinite loop)** at `DONE:` using **SJMP DONE**.  
13. **End the program.**

## Output Table

| Condition           | Port 1 Output | Meaning           |
|--------------------|---------------|-----------------|
| Number is Palindrome | `FFH`         | Palindrome Detected |
| Number is Not Palindrome | `00H`     | Not a Palindrome |

## Example

Input: Port 0 (P0)

Output: Port 1 (P1)

P1 = FF → Palindrome

P1 = 00 → Not palindrome

## PROGRAM:
```
ORG 00H
MOV A, P0         ;
MOV B, #0AH
DIV AB
MOV R0, A
MOV R1, B
MOV A, R1
MOV B, #0AH
MUL AB
ADD A, R0
CJNE A, P0, NOTPAL
MOV P1, #0FFH
SJMP DONE
NOTPAL:
MOV P1, #00H
DONE:
SJMP DONE
END
```

### OUTPUT:
<img width="1707" height="600" alt="image" src="https://github.com/user-attachments/assets/52f91e59-01a1-45d9-b7da-810594686af5" />

### RESULT:
Thus the assembly language program in 8051 to check whether a given  number is a palindrome or not was successfully written and simulated using keil software.



