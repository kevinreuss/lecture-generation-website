# Machine Code Representation

Machine code is the lowest level of programming language, represented in binary format, which is directly executed by the central processing unit (CPU). It is specific to each type of computer architecture.

## Basics of Machine Code

Machine code instructions consist of an opcode and operand(s). The opcode is the command for the CPU, and the operand is the data to be manipulated. For example, a very basic machine code instruction could be "1001 0100", where '1001' is the opcode (say, for addition) and '0100' is the operand (the number 4).

## Assembly and Machine Code

In assembly language, a mnemonic represents each machine code instruction. These mnemonics are then converted into machine code by an assembler. For example, the ADD instruction in assembly language might correspond to the opcode '1001' in our earlier example.

```assembly
ADD R1, R2, R3  ; Assembly language
```

This might translate to the following machine code:

```binary
1001 0001 0010 0011  ; Machine code
```

In this binary sequence, '1001' is the opcode for ADD, and '0001', '0010', and '0011' are the binary representations of the registers R1, R2, and R3.

## Endianness

Endianness refers to the order of bytes that makes up a data word in computer memory. It's a crucial concept when dealing with machine code. There are two types:

1. **Big Endian**: The most significant byte is stored in the smallest address.
2. **Little Endian**: The least significant byte is stored in the smallest address.

For example, consider a 4-byte integer `0x12345678`. In Big Endian, it's stored as `0x12 0x34 0x56 0x78`. In contrast, Little Endian stores it as `0x78 0x56 0x34 0x12`.

## Conclusion

Understanding machine code representation is fundamental for low-level programming, debugging, reverse engineering, and in-depth understanding of computer architecture. It allows you to see the literal binary 'building blocks' that form all the software we use.