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

    1. Opcode (7 bits)
Identifies the broad category of the instruction (e.g., arithmetic, logical, shift). The opcode determines the type of operation and the instruction format (e.g., R-type, I-type, S-type).

Placement: Bits [6:0].

Examples: 0110011: R-type operations (add, sub, and, or, etc.).

  2. rd (Destination Register, 5 bits)
Specify the register where the result of the operation will be stored.

Placement: Bits [11:7].
The register index ranges from 0 to 31, corresponding to the 32 general-purpose registers in RISC-V (e.g., x0 to x31).
Writing to x0 is effectively a NOP (writes are ignored since x0 is hardwired to 0).

Example: If rd = 01010, it means the result is stored in register x10.

  3. funct3 (Function Code, 3 bits)
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

    4. rs1 (Source Register 1, 5 bits)
Specifies the first source register containing one of the operands.

Placement: Bits [19:15].

The register index ranges from 0 to 31, like rd. It holds the value used in computation or logical operation.

Example: If rs1 = 00001, it means the first operand is in register x1.

     5. rs2 (Source Register 2, 5 bits)
Specifies the second source register containing the second operand.

Placement: Bits [24:20].

Like rs1, the register index ranges from 0 to 31. It provides the second value used in computations.

Example: If rs2 = 00010, it means the second operand is in register x2.

      6. funct7 (Function Code, 7 bits)
Provides additional specificity to distinguish between operations that share the same opcode and funct3.

Placement: Bits [31:25].

This field is essential for certain instructions with similar opcode and funct3 but different behaviors.
Common values:
0000000: Standard operation (e.g., add).
0100000: Alternative operation (e.g., sub).

Examples:
For ADD: funct7 = 0000000.
For SUB: funct7 = 0100000.


</details>





