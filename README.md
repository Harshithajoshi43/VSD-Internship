# VSD-Internship

<details>
  <summary>Task 1</summary>

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
 <summary>Task 2</summary>

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
  <summary>Task 3</summary>

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

**1. R-Type:**

The R-type instruction format in RISC-V is designed to perform register-to-register operations. Each field has a specific role, contributing to the functionality and flexibility of the instruction. Here's a detailed breakdown of each field:

 - Opcode (7 bits)
  
      Identifies the broad category of the instruction (e.g., arithmetic, logical, shift). The opcode determines the type of operation and the instruction format (e.g., R- type, I-type, S-type).

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

    **2. The I-type (Immediate-type)**
   
       The I-type (Immediate-type) instruction format in RISC-V is used for instructions that operate on one register operand and an immediate value. These instructions are        common for operations such as memory 
       access, arithmetic with constants, or conditional jumps.
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

**3. The S-type (Store-type)**
   
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
       Specify the register holding the base address for memory access.

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

**4. The U-type instruction** 
      The U-type instruction format in the RISC-V architecture is used primarily for instructions that involve immediate values, typically for forming larger constants or calculating addresses. The U-type format is part 
      of the 32-bit RISC-V instruction set.
      The U-type instruction has the following 32-bit structure:
      
   - Immediate (31–12):
      
        This is a 20-bit field that provides the upper 20 bits of a constant or address. The value is sign-extended when needed. The lower 12 bits are typically assumed to be zeros.
   - Destination Register (rd) (11–7): Specifies the register where the result of the instruction will be stored.
   - Opcode (6–0): Identifies the specific instruction. For U-type, common opcodes are:
                LUI (Load Upper Immediate): Opcode 0110111.
                AUIPC (Add Upper Immediate to PC): Opcode 0010111.


**5. The B-type (Branch-type)**
       The B-type (Branch-type) instruction format in RISC-V is designed for conditional branch instructions that control the flow of execution based on a comparison     
       between two registers. These instructions are typically used to implement if-else conditions, loops, and other control flow operations.
       The B-type format has the following fields:
   
   - opcode (7 bits):
        Identifies the type of instruction (branch in this case).
     
        Placement: Bits [6:0].
     
        The opcode for B-type instructions is 1100011. This indicates that the instruction is related to branching.
     
        Example: For a branch instruction: opcode = 1100011.
     
   - imm (Immediate Value, 13 bits):
        Provides the offset that is added to the program counter (PC) when the branch condition is met. This offset is calculated relative to the next instruction (PC + 4).
     
        Placement:
        imm[12]: The most significant bit (bit 12).
        imm[10:5]: Bits [10:5] for the middle 6 bits.
        imm[4:1]: Bits [4:1] for the least significant 4 bits.
        imm[11]: The second most significant bit (bit 11).

        The immediate value is signed (using two's complement) and is used to calculate the address of the target instruction. The immediate is shifted left by 1 bit during         instruction decoding to account for word-aligned addresses.
     
        Example: If imm[12] = 0, imm[10:5] = 000100, imm[4:1] = 0101, and imm[11] = 1, the complete immediate would be 000100010101 (in binary), which is 0x115 (277 in              decimal).
     
  - rs2 (Source Register 2, 5 bits):
        Specifies the second register that is compared to rs1 for the branch decision.

    Placement: Bits [24:20].

    The value in rs2 is compared with the value in rs1. This field is used in the comparison operation for the branch (e.g., beq, bne).
      
    Example: If rs2 = 00010, the second operand is x2.

   - rs1 (Source Register 1, 5 bits):
        Specifies the first register that is compared to rs2.

        Placement: Bits [19:15].

        The value in rs1 is compared with the value in rs2. For a beq (branch if equal) instruction, if the values in rs1 and rs2 are equal, the branch is taken.
   
        Example: If rs1 = 00001, the first operand is x1.
   
   - funct3 (Function Code, 3 bits):
        Specify the type of comparison (e.g., equal, not equal, greater than, etc.).

        Placement: Bits [14:12].

        The comparison determines whether the branch will be taken. Common values:
        000: Branch if equal (beq).
        001: Branch if not equal (bne).
        100: Branch if less than (blt).
        101: Branch if greater than or equal (bge).
        110: Branch if unsigned less than (bltu).
        111: Branch if unsigned greater than or equal (bgeu).\n
        Examples:

        beq (branch if equal): funct3 = 000.
        bne (branch if not equal): funct3 = 001.

6. **The J-type (Jump-type)**
       The J-type (Jump-type) instruction format in RISC-V is designed for unconditional jump operations. These instructions allow the program to change its execution flow         by jumping to an address specified by a 
       12-bit signed immediate value. The immediate value is used to calculate the target address relative to the current Program Counter (PC).

      Placement: Bits [19:15].

      The J-type format has the following fields:

   - opcode (7 bits):
      Identifies the type of instruction. In J-type, the opcode specifies that the instruction is a jump.
     
      Placement: Bits [6:0].

      The opcode for J-type instructions is always 1101111 (which indicates the jump instruction category).

      Example: For a jump instruction (jal or jalr), opcode = 1101111.

   - imm (Immediate Value, 21 bits total):
      Purpose: Specifies the offset to be added to the current Program Counter (PC) to calculate the target address.
   
      Placement:
      imm[20]: Most significant bit of the immediate value (bit 20).
      imm[10:1]: Middle 10 bits of the immediate value.
      imm[11]: Second most significant bit (bit 11).
      imm[19:12]: Lower 8 bits of the immediate value.

      The immediate value is signed and used to calculate the target address relative to the current instruction. The immediate value is shifted left by 1 bit to account          for the word-aligned address (because 
      instructions are 4 bytes in RISC-V). This offset allows the jump to be within a ±1 MiB range (a total of 2^20 bytes, or 2^18            words).
   
      Example: If imm[20] = 0, imm[10:1] = 0101010101, imm[11] = 1, and imm[19:12] = 10101010, the full immediate value would be 0101010101101010101 (in binary), which is         0x55555 (349525 in decimal).
   
   - rs1 (5 bits):
      Purpose: This field is not used in J-type instructions and is always 0. It is reserved for compatibility with other instruction formats.
     
  
  


# 32-bit instructions from application ( Simple Calculator )

![Screenshot 2024-12-02 211938](https://github.com/user-attachments/assets/7ee28e7c-6cde-4e8e-9678-d7670f5eebc7)

**1. lui a0, 0x2b**

  Instruction Type: U-Type Instruction
  
  Fields:
  
  imm[31:12]: 0x2b (Upper 20-bit immediate value)
  
  rd: a0
  
  opcode: 0110111 (LUI)
  
32-bit Representation: 00000000001010110000 00010 0110111

**2. addi sp, sp, -48**

Instruction Type: I-Type Instruction

Fields:

  imm[11:0]: -48 (Signed immediate: 111111111100)
  
  rs1: sp
  
  funct3: 000 (Addition)
  
  rd: sp
  
  opcode: 0010011
  
32-bit Representation: 111111111100 00010 000 00010 0010011

**3. sd ra, 40(sp)**
Instruction Type: S-Type Instruction
Fields:

  imm[11:5]: 101000 (Higher 7-bits of offset)
  
  rs2: ra
  
  rs1: sp
  
  funct3: 011 (Store Doubleword)
  
  imm[4:0]: 01000 (Lower 5-bits of offset)
  
  opcode: 0100011
  
32-bit Representation: 1010000 00001 00010 011 01000 0100011

**4. jal ra, 106c <printf>**

Instruction Type: J-Type Instruction

Fields:

imm[20|10:1|11|19:12]: Address offset to 106c split into fields.

rd: ra (00001)

opcode: 1101111 (JAL)

32-bit Representation: (Encoded based on the offset)

**5. lbu a5, 7(sp)**

Instruction Type: I-Type Instruction

Fields:

  imm[11:0]: 7
  
  rs1: sp (00010)
  
  funct3: 100 (Load Byte Unsigned)

  rd: a5 (00101)

  opcode: 0000011

32-bit Representation: 000000000111 00010 100 00101 0000011

**6. li a4, 4**

Instruction Type: Pseudo-Instruction (ADDI)

Fields:

  imm[11:0]: 4
  
  rs1: x0 (00000)
  
  funct3: 000
  
  rd: a4 (00100)
  
  opcode: 0010011
  
32-bit Representation: 000000000100 00000 000 00100 0010011

**7. beq a5, a4, 101dc**

Instruction Type: B-Type Instruction

Fields:

imm[12|10:5|4:1|11]: Offset to 101dc split into parts.

rs1: a5 (00101)

rs2: a4 (00100)

funct3: 000 (Branch if Equal)

opcode: 1100011

32-bit Representation: (Encoded with offset fields)

8. bgeu a5, a4, 101c4

Instruction Type: B-Type Instruction

Fields:

  imm[12|10:5|4:1|11]: Offset to 101c4.
  
  rs1: a5 (00101)
  
  rs2: a4 (00100)
  
  funct3: 011 (Branch if Greater or Equal Unsigned)
  
  opcode: 1100011
  
32-bit Representation: (Encoded with offset fields)

**9. lw s0, 12(sp)**

Instruction Type: I-Type Instruction


Fields:
  
  imm[11:0]: 12
  
  rs1: sp (00010)
  
  funct3: 010 (Load Word)
  
  rd: s0 (10000)

opcode: 0000011

32-bit Representation: 000000001100 00010 010 10000 0000011

**10. beqz s0, 101fc**

Instruction Type: B-Type Instruction

Fields:
  
  imm[12|10:5|4:1|11]: Offset to 101fc.
  
  rs1: s0 (10000)
  
  rs2: x0 (00000 for BEQZ)
  
  funct3: 000
  
  opcode: 1100011

32-bit Representation: (Encoded with offset fields)

**11. mv a1, s0**

Instruction Type: Pseudo-Instruction (ADDI)

Fields:

imm[11:0]: 0

rs1: s0 (10000)

funct3: 000
  
  rd: a1 (01001)
  
  
  opcode: 0010011

32-bit Representation: 000000000000 10000 000 01001 0010011

**12. j 10198**

Instruction Type: J-Type Instruction

Fields:
  
  imm[20|10:1|11|19:12]: Offset to 10198.
  
  rd: x0 (Implicit for j)
  
  opcode: 1101111

32-bit Representation: (Encoded with offset fields)

**13. ld ra, 40(sp)**

Instruction Type: I-Type Instruction

Fields:
  
  imm[11:0]: 40
  
  rs1: sp (00010)
  
  funct3: 011 (Load Doubleword)

  rd: ra (00001)
  
  opcode: 0000011

32-bit Representation: 000000101000 00010 011 00001 0000011

**14. subw a3, a3, a2**

Instruction Type: R-Type Instruction

Fields:
  
  funct7: 0100000 (Subtraction)
  
  rs2: a2 (00010)

  rs1: a3 (00011)
  
  funct3: 000

  rd: a3 (00011)

  
  opcode: 0111011

32-bit Representation: 0100000 00010 00011 000 00011 0111011

**15. addw a3, a3, a2**


Instruction Type: R-Type Instruction

Fields:

  
  funct7: 0000000 (Addition)
  
  rs2: a2 (00010)
  
  rs1: a3 (00011)
  
  funct3: 000
  
  rd: a3 (00011)
  
  opcode: 0111011

32-bit Representation: 0000000 00010 00011 000 00011 0111011

</details>

<details>
  <summary>Task 4</summary>

  **Functional simulation of RISC-V instructions modeled as a Verilog netlist and observe the output waveforms using GTKWave**.
  
In Verilog design workflows, simulations are typically executed using tools like Icarus Verilog. During these simulations, waveform data is captured in files such as Value Change Dump (VCD). These files record the state of signals over time and are later viewed using waveform viewers like GTKWave. This graphical visualization helps in analyzing signal transitions and verifying both the design's functionality and timing behavior.

Installing iverilog using ```command sudo apt install iverilog gtkwave```
![Screenshot 2024-12-07 152748](https://github.com/user-attachments/assets/2b229ce4-c07b-47a1-9a62-1abba3e1dddc)

1. Create a directory with your name using the command:
mkdir <your_name>

2. Use the ```touch``` command to create two Verilog files named harshitha_rv32i.v and harshitha_rv32i_tb.v:
   
```touch harshitha_rv32i.v harshitha_rv32i_tb.v```

3. Copy the required Verilog code and testbench code from the reference GitHub repository into the respective files.
      
  ![Screenshot 2024-12-07 164503](https://github.com/user-attachments/assets/208babda-6267-4ee6-a4d5-272164f2e517)
  ![Screenshot 2024-12-07 164435](https://github.com/user-attachments/assets/f99ddf5f-014d-4f2d-b048-047d7ef1b37c)
  ![Screenshot 2024-12-07 164503](https://github.com/user-attachments/assets/49b3a5c7-2af4-4610-96ef-1e90ec3daba1)
  
4. To compile and simulate the Verilog code, execute the following commands:

    ```iverilog -o harshitha_rv32i harshitha_rv32i.v harshitha_rv32i_tb.v```
    ```./harshitha_rv32i``` 

it will create iiitb_rv32i.vcd file which is used for gtkwave.

![Screenshot 2024-12-07 170508](https://github.com/user-attachments/assets/f82eae06-6b85-4e4a-b035-15095d2ce846)


5. Open the gtkwave using command gtkwave ```iiitb_rv32i.vcd```

All the instructions in the given verilog file is hard-coded. Hard-coded means that instead of following the RISCV specifications bit pattern, the designer has hard-coded each instructions based on their own pattern. Hence the 32-bits instruction that we generated in Task-2 will not match with the given instruction.


| Operation     | Description                 | Standard RISC-V ISA    | Hard-Coded ISA|
|---------------|-----------------------------|------------------------|---------------|
| ADD R6, R2, R1| Adds the values in R2 and R1,stores result in R6|32'h00110333|32'h02208300|                   	                   
|SUB R7, R1, R2|	Subtracts the value in R2 from R1, stores result in R7 |	32'h402083b3|	32'h02209380|
|AND R8, R1, R3	|Performs bitwise AND between R1 and R3, stores in R8	|32'h0030f433	|32'h0230a400|
|OR R9, R2, R5	|Performs bitwise OR between R2 and R5, stores in R9	|32'h005164b3	|32'h02513480|
|XOR R10, R1, R4	|Performs bitwise XOR between R1 and R4, stores in R10	|32'h0040c533|	32'h0240c500|
|SLT R1, R2, R4	|Sets R1 to 1 if R2 < R4, else sets to 0	| 32'h0045a0b3	|32'h02415580|
|ADDI R12, R4, 5	|Adds immediate value 5 to R4, stores result in R12	|32'h004120b3	|32'h00520600|
|BEQ R0, R0, 15	|Branches to offset 15 if R0 equals R0	| 32'h00000f63	|32'h00f00002|
|SW R3, R1, 2	|Stores word from R3 to memory address (R1 + 2)	| 32'h0030a123	|32'h00209181|
|LW R13, R1, 2	|Loads word from memory address (R1 + 2) into R13	| 32'h0020a683	|32'h00208681|
|SRL R16, R14, R2|	Shifts R14 right by the value in R2, stores in R16 |	32'h0030a123|	32'h00271803|
|SLL R15, R1, R2|	Shifts R1 left by the value in R2, stores in R15	| 32'h002097b3	|32'h00208783|		

# Veifying instructions using Gtkwave

1.ADD R6, R2, R1

![WhatsApp Image 2024-12-08 at 22 21 58_02a33daa](https://github.com/user-attachments/assets/76a88b92-0a09-4f2f-b840-d6313183c61f)


2.SUB R7, R1, R2

![WhatsApp Image 2024-12-08 at 22 21 57_6de4ccb1](https://github.com/user-attachments/assets/be696bfa-4098-4e90-aa7a-55536012a721)

3.AND R8, R1, R3

![WhatsApp Image 2024-12-08 at 22 21 57_f626c078](https://github.com/user-attachments/assets/347fbc9d-e616-45d4-9805-4f43c7447249)

4.OR R9, R2, R5

![WhatsApp Image 2024-12-08 at 23 04 46_e89d44bd](https://github.com/user-attachments/assets/0dcbbf5f-7e7d-4cc7-9cf7-9c7b1679243d)


5.XOR R10, R1, R4

![WhatsApp Image 2024-12-08 at 22 21 56_dba82745](https://github.com/user-attachments/assets/853e546c-c609-40cb-86bc-8d9754acac0b)

6.SLT R1, R2, R4

![WhatsApp Image 2024-12-08 at 22 21 56_68749d39](https://github.com/user-attachments/assets/b12f4c20-5f16-4f29-b49e-dc97eba9f2f4)

7.ADDI R12, R4, 5

![WhatsApp Image 2024-12-08 at 22 21 55_2b9695b0](https://github.com/user-attachments/assets/539d4a9a-9a8f-44a2-bca6-c329974f6dd5)

8.SW R3, R1, 2

![WhatsApp Image 2024-12-08 at 22 21 55_98ef53a6](https://github.com/user-attachments/assets/7b3cad3c-2450-49c2-9e28-67385472e31e)

9.SRL r16, r11, r2

![Screenshot 2024-12-08 222003](https://github.com/user-attachments/assets/4c891ccc-4884-44d5-9837-3a25c00c7976)

10.BEQ R0, R0, 15

![WhatsApp Image 2024-12-08 at 22 56 16_f27b1b8c](https://github.com/user-attachments/assets/88521f77-f20b-4fb4-a123-7d00d8bd08c4)

11. SLL R15, R1, R2
    
![Screenshot 2024-12-08 155153](https://github.com/user-attachments/assets/84c1e15e-78f3-4688-aaa8-37b203905be1)


</details>

<details>
<summary>Task 5</summary>

### Introduction
This project is designed to empower ambulance drivers to navigate traffic signals efficiently during emergencies, minimizing delays and potentially saving lives. By enabling direct control over traffic signals, ambulances can turn red signals green, clearing their path through intersections.

### Overview
Traffic congestion in urban areas often hinders ambulances, delaying critical care during emergencies. This project provides a practical and scalable solution to address this challenge by allowing ambulance drivers to control traffic signals.

Using a secure code-based system, the ambulance driver inputs the signal's unique identifier displayed at each traffic light. The transmitter unit sends this code to the receiver unit at the traffic signal, which verifies and triggers the green light. This mechanism ensures efficient traffic management without disrupting the flow for other road users.

This repository contains the hardware schematics, software code, and implementation guidelines for setting up this system. The project leverages affordable and readily available components to ensure accessibility and scalability for widespread adoption.



</details>





  


 



      







