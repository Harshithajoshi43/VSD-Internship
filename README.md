# VSD-Internship

<details>
  <summary>Task1</summary>

```
cd
```

```

leafpad sum1ton.c
```

```
gcc sum1ton.c
```

```
ls -ltr
```

```
./a.out
```




![Screenshot 2024-11-22 201754](https://github.com/user-attachments/assets/224cad40-c7fb-40df-aee4-d17bc776d46b)


![Screenshot 2024-11-23 223821](https://github.com/user-attachments/assets/d6869ce0-8842-4633-aca5-47b1c9f01600)


```
cat sum1ton.c
```



![Screenshot 2024-11-26 155243](https://github.com/user-attachments/assets/2b2e6120-1ec6-42ea-966d-728c444cda2a)

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

![Screenshot 2024-11-26 154713](https://github.com/user-attachments/assets/e621cdf4-0a80-4e5d-a9fe-f14c7a49dd5a)


![Screenshot 2024-11-26 155157](https://github.com/user-attachments/assets/ce03a69e-5bbc-48ba-8a9c-0c8cebba9ac1)
</details>

<details>
 <summary>Task2</summary>

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

```
gcc sum1ton.c
```

```
./a.out
```

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

```
spike pk sum1ton.o
```

 ![Screenshot 2024-11-26 163523](https://github.com/user-attachments/assets/9b1b99c2-67ea-481f-893a-ffc941de284e)
 ![Screenshot 2024-11-26 163847](https://github.com/user-attachments/assets/bf677c63-bd2a-4fa8-9c92-fba81dc1e314)
![Screenshot 2024-11-28 002509](https://github.com/user-attachments/assets/10583888-cbdb-41ba-8453-182ffc0c8f81)
![Screenshot 2024-11-28 004621](https://github.com/user-attachments/assets/b89cc490-ef27-42dd-82eb-94a115eb8a92)

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

```
ls -ltr simplecalc.o
```

```
spike pk simplecalc.o
```

![Screenshot 2024-11-28 005212](https://github.com/user-attachments/assets/3ac04ab4-e2ee-4d58-8e6a-ed56fe0cdffa)
</details>
<details>
  <summary>Task3</summary>

RISC-V RV32 refers to a 32-bit RISC-V instruction set architecture (ISA) implementation. It is an open, royalty-free ISA designed to be simple, efficient, and scalable for various applications. The RISC-V RV32 instruction set has 6 main instruction types, based on their encoding format. These types are determined by how operands and immediate values are encoded in the instruction.
The six instruction types are:
1. R-Type (Register Type)
2. I-Type (Immediate Type)
3. S-Type (Store Type)
4. U-Type (Branch Type)
5. B-Type (Upper Immediate Type)
6. J-Type (Jump Type)
   
RISC-V Instruction Sets

<img width="772" alt="3808 1535301636" src="https://github.com/user-attachments/assets/f85cfaf6-348d-4571-83c3-7078501960c8">

1. R-Type:
The R-type instruction format in RISC-V is designed to perform register-to-register operations. Each field has a specific role, contributing to the functionality and flexibility of the instruction. Here's a detailed breakdown of each field:

  - Opcode (7 bits)
Identifies the broad category of the instruction (e.g., arithmetic, logical, shift). The opcode determines the type of operation and the instruction format (e.g., R-type, I-type, S-type).

Placement: Bits [6:0].

Examples: 0110011: R-type operations (add, sub, and, or, etc.).

  - rd (Destination Register, 5 bits)
Specify the register where the result of the operation will be stored.

Placement: Bits [11:7].

The register index ranges from 0 to 31, corresponding to the 32 general-purpose registers in RISC-V (e.g., x0 to x31).
Writing to x0 is effectively a NOP (writes are ignored since x0 is hardwired to 0).

Example: If rd = 01010, it means the result is stored in register x10.

  - rd (Destination Register, 5 bits)
Specifies the specific operation to be performed within the instruction category defined by opcode.

Placement: Bits [14:12].
funct3 works in combination with funct7 to differentiate between similar operations.
Common values:
000: Add or subtract (depending on funct7).
111: AND operation.
110: OR operation.

Examples:
For an ADD instruction: funct3 = 000.
For an AND instruction: funct3 = 111.

  - rs1 (Source Register 1, 5 bits)
Specifies the first source register containing one of the operands.

Placement: Bits [19:15].

The register index ranges from 0 to 31, like rd. It holds the value used in computation or logical operation.

Example: If rs1 = 00001, it means the first operand is in register x1.

  - rs2 (Source Register 2, 5 bits)
Specifies the second source register containing the second operand.

Placement: Bits [24:20].

Like rs1, the register index ranges from 0 to 31. It provides the second value used in computations.

Example: If rs2 = 00010, it means the second operand is in register x2.

  - funct7 (Function Code, 7 bits)
Provides additional specificity to distinguish between operations that share the same opcode and funct3.

Placement: Bits [31:25].

This field is essential for certain instructions with similar opcode and funct3 but different behaviors.
Common values:
0000000: Standard operation (e.g., add).
0100000: Alternative operation (e.g., sub).

Examples:
For ADD: funct7 = 0000000.
For SUB: funct7 = 0100000.

2. The I-type (Immediate-type)
   
   The I-type (Immediate-type) instruction format in RISC-V is used for instructions that operate on one register operand and an immediate value. These instructions are common for operations such as memory access, arithmetic with constants, or conditional jumps.
The I-type format has the following fields:
- opcode (7 bits):
Identifies the type of instruction (e.g., arithmetic, memory access, etc.).

Placement: Bits [6:0].

Common opcodes for I-type:
0000011: Load instructions (e.g., lw for load word).
0010011: Arithmetic instructions with an immediate (e.g., addi).
  
- rd (Destination Register, 5 bits):
Specifies the destination register where the result of the operation will be stored.
Placement: Bits [11:7].
Holds the result of the operation (e.g., the value loaded from memory or the result of arithmetic with the immediate).
Example: If rd = 00010, the result is written to register x2.

- funct3 (Function Code, 3 bits):
Specifies the specific operation within the instruction type.

Placement: Bits [14:12].

Differentiates between operations like addi, slti, or load instructions like lb (load byte), lw (load word).

Examples:
000: Add immediate (addi).
010: Set less than immediate (slti).
100: XOR immediate (xori).

- rs1 (Source Register 1, 5 bits):
Specifies the register providing the first operand.

Placement: Bits [19:15].

The value in this register is combined with the immediate value (imm) in the specified operation.

Example: If rs1 = 00001, it means the value in register x1 is used as the operand.

- imm (Immediate Value, 12 bits):
Provides a constant value or offset for the instruction.

Placement: Bits [31:20].

Signed 12-bit value (using two's complement).
Can represent values in the range of -2048 to 2047.
Zero-extended or sign-extended as needed based on the operation.
Used for:
Arithmetic operations (e.g., addi adds rs1 and imm).
Load instructions (e.g., memory address is rs1 + I'm).

Examples:
For addi x3, x2, 10: imm = 10 (decimal).
For lw x5, 100(x1): imm = 100 (offset).

3. The S-type (Store-type)
   The S-type (Store-type) instruction format in RISC-V is designed for instructions that store data from a register in memory. It uses a combination of a base address 
   from one register and an immediate offset to calculate the effective memory address.

   The S-type format has the following fields:

   - opcode (7 bits):
   Identifies the type of instruction (store in this case).

   Placement: Bits [6:0].
   
   The common opcode for S-type instructions:
   0100011: Store instructions (e.g., sw, sh, sb).
      
   Example: For a store word (sw) instruction: opcode = 0100011.

   - imm (Immediate Value, 12 bits total):
   Specifies the offset to be added to the base address in rs1 to calculate the effective memory address.

   Placement:
   Upper 7 bits (imm[11:5]): Bits [31:25].
   Lower 5 bits (imm[4:0]): Bits [11:7].

   Immediate is a signed 12-bit value (using two's complement).Can represent offsets from -2048 to 2047.
   The two parts (imm[11:5] and imm[4:0]) are combined during instruction decoding to form the complete immediate.
   
   Example: If imm[11:5] = 0000001 and imm[4:0] = 01010, the full immediate is 000000101010 (42 in decimal).
   
   - rs2 (Source Register 2, 5 bits):
   Specifies the register holding the data to be stored in memory.

   Placement: Bits [24:20].
   
   The contents of this register are written to the memory address calculated from rs1 + imm.
   
   Example: If rs2 = 00010, the data to be stored comes from register x2.
   
   - rs1 (Source Register 1, 5 bits):
   Specifies the register holding the base address for memory access.

   Placement: Bits [19:15].
   
   The effective memory address is calculated as rs1 + imm.
   
   Example: If rs1 = 00001, the base address comes from register x1.
   
   - funct3 (Function Code, 3 bits):
   Specifies the type of data to be stored (e.g., byte, half-word, word).

   Placement: Bits [14:12].
   
   Determines the size of the data being stored.
   Common values:
   000: Store byte (sb).
   001: Store half-word (sh).
   010: Store word (sw).
     
  Example: For a store word instruction: funct3 = 010.





</details>






  


 



      







