pyasm2 - x86 assembler library          (C) 2012 Jurriaan Bremer

Although it's called pyasm2, this is not per se a successor of Pyasm or pyASM.
pyasm2 aims to be as flexible as possible, it will support x86, SSE and SSE2.

A key feature of pyasm2 is the ability to have blocks of instructions and
being able to give the base address at a later time, that is, you don't need
to know the address of instructions before-hand. For example, you can construct
a series of instructions, request the size that will be needed in order to
store all instructions as sequence, allocate this memory and write the
instructions from there, this approach is very useful when making JIT
compilers, etc.

The syntax of pyasm2 is supposed to be as simple as possible.

For example, an instruction such as "**mov eax, dword [ebx+edx*2+32]**" can be
encoded using pyasm2 as in the following.
```python
mov(eax, dword [ebx+edx*2+32])
```

These memory addresses also support **segment registers**, for example,
```python
mov(eax, dword[fs:0xc0])
```
although this is currently only supported in 64-bit Python versions.

Furthermore, pyasm2 makes it possible to **chain multiple instructions**. Take
for example the following statement.
```python
block(mov(eax, ebx), push(32))
```

However, for more implementation-specific details, please refer to the
*IMPLEMENTATION* file.
