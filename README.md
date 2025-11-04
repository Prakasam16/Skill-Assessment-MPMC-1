# Find Smallest Number in an Array Using 8086 Assembly Language

## AIM
To write and execute an Assembly Language Program in **8086** to find the **smallest number** in an array of N elements stored sequentially in memory using **conditional jump instructions**, and store the result in another memory location.

---

## APPARATUS REQUIRED
- Personal Computer with **MASM** (Microsoft Macro Assembler) or **EMU8086** Software

---

## ALGORITHM
1. Start the program.
2. Initialize the data segment register (DS).
3. Load the starting memory address of the array into SI register.
4. Load first number into AL (assume it as the smallest).
5. Load counter (N−1) into CX register.
6. Compare AL with next value in memory.
7. If memory value < AL, move it to AL.
8. Increment SI to point to the next memory location.
9. Decrement CX and repeat until CX = 0.
10. Store the smallest number in the next memory location.
11. Stop the program.

---

## FLOWCHART
  ┌───────────────┐
 │     Start     │
 └───────┬───────┘
         │
         ▼
 ┌─────────────────────────┐
 │ Initialize DS & Load    │
 │ first array element     │
 └─────────┬───────────────┘
           │
           ▼
 ┌─────────────────────────┐
 │ Compare with next value │
 └─────────┬───────────────┘
           │
   ┌───────▼────────┐
   │ Is smaller?     │
   └───────┬────────┘
           │ Yes
           ▼
 ┌─────────────────────────┐
 │ Update smallest value   │
 └─────────┬───────────────┘
           │ No
           ▼
 ┌─────────────────────────┐
 │ Repeat till end of list │
 └─────────┬───────────────┘
           │
           ▼
 ┌─────────────────────────┐
 │ Display smallest value  │
 └─────────┬───────────────┘
           │
           ▼
 ┌───────────────┐
 │     End       │
 └───────────────┘

---

## PROGRAM

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H

MOV SI,2000H      ; Start of numbers
MOV AL,[SI]       ; Assume first number as smallest
MOV CX,05H        ; Total elements = 5
DEC CX            ; Remaining count = 4
INC SI            ; Point to next value

L1:
CMP AL,[SI]       ; Compare smallest with new number
JBE SKIP          ; If AL <= [SI], skip
MOV AL,[SI]       ; Otherwise update smallest

SKIP:
INC SI            ; Move to next number
LOOP L1           ; Repeat for all numbers

MOV 2005H,AL      ; Store smallest value at 2005H

MOV AH,4CH        ; Terminate program
INT 21H

CODE ENDS
END
```
MEMORY LOCATION

| MEMORY LOCATION | VALUE (HEX) | DESCRIPTION                  |
| --------------- | ----------- | ---------------------------- |
| 2000H           | 08H         | Number 1                     |
| 2001H           | 04H         | Number 2                     |
| 2002H           | 12H         | Number 3                     |
| 2003H           | 02H         | Number 4                     |
| 2004H           | 0AH         | Number 5                     |
| 2005H           | 02H         | Smallest Number (Result)     |

OUTPUT


RESULT

Thus, the Assembly Language Program for 8086 microprocessor to find the smallest number in an array using conditional jump instructions was successfully written and executed using MASM/EMU8086.

