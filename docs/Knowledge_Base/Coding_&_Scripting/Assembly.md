!!! info ""

    ### Summary

    Assembly language depends on the CPU Architecture. An assembler translates mnemonics (e.g. jump, mov, add, etc.) from an assembly language into machine instructions. Machine instructions are entirely dependent on the hardware (they represent the hardware/CPU instruction set).
    The assembler implementation may (and generally is) OS-specific, because of the output program it produces (a Unix executable is not the same as a Windows executable, even though the underlying machine instruction set is x86, for example).

    Hierarchy of Programming Languages
    ![alt text](/Knowledge_Base/images/assembly_0s_2.png)


!!! info ""

    ### Resources
    - [x86 Cheat sheet](https://exploit-notes.hdks.org/exploit/reverse-engineering/assembly/x86-assembly/)
    - [32-bit Cheat sheet](https://exploit-notes.hdks.org/exploit/reverse-engineering/assembly/32-bit-arm-assembly/)
    - [wikipedia Comparison of assemblers](https://en.wikipedia.org/wiki/Comparison_of_assemblers)
    - [wikipedia - Assembly language](https://en.wikipedia.org/wiki/Assembly_language)
    - [seattlewebsitedevelopers - Assembly Language](https://seattlewebsitedevelopers.medium.com/assembly-language-38e4b0edca0d)
      - [YT - javidx9](https://www.youtube.com/watch?v=1FXhjErUz58)
    - [gpfault - x86-64 Assembly](https://gpfault.net/posts/asm-tut-0.txt.html)
    - [tutorialspoint - NASM Assembly Programming Tutorial](https://www.tutorialspoint.com/assembly_programming/index.htm)
    - [Arm Assembly Language](https://developer.arm.com/documentation/107829/0200/Assembly-language-basics)
    - [virginia edu - x86 Assembly Guide](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html)
    - [Intel's architecture manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html#three-volume)
    - [Intel® 64 and IA-32 Architectures Software Developer Manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html)
    - [wikibooks - x86 Assembly](https://en.wikibooks.org/wiki/X86_Assembly)
    - [Jonathan Bartlett - Programming from the Ground Up](https://www.cs.princeton.edu/courses/archive/spr08/cos217/reading/ProgrammingGroundUp-1-0-lettersize.pdf)
    - [NASM Assembly Language Tutorials - asmtutor](https://asmtutor.com/)
    - [Webster](https://www.plantation-productions.com/Webster/)
    - [AMD CS107 Guide to x86-64](https://josemariasola.github.io/reference/assembler/Stanford%20CS107%20Guide%20to%20x86-64.pdf)
    - [Brown.edu x64 cheatsheet](/Knowledge_Base/images/Assembly_Brown.edu_x64_cheatsheet.pdf)


!!! info ""

    ### View disassembly code in the Visual Studio debugger (C#, C++, Visual Basic, F#)

    Source: [Microsoft](https://learn.microsoft.com/en-us/visualstudio/debugger/how-to-use-the-disassembly-window?view=vs-2022)

    To enable the Disassembly window, under **Tools** > **Options** > **Debugging**, select **Enable address-level debugging**
    To open the Disassembly window during debugging, select **Windows** > **Disassembly** or **press Alt+8**



!!! info ""

    ### Info & Cheatsheets

    ![alt text](/Knowledge_Base/images/assembly_0s_3.png)

    [Intel x86 Assembly Language Cheat Sheet](https://scadahacker.com/library/Documents/Cheat_Sheets/Programming%20-%20x86%20Instructions%201.pdf)

    ![alt text](/Knowledge_Base/images/assembly_0s_4.png)

    [X86/WIN32 REVERSE ENGINEERING CHEAT­SHEET](https://trailofbits.github.io/ctf/vulnerabilities/references/X86_Win32_Reverse_Engineering_Cheat_Sheet.pdf)

    [x64 Cheat Sheet](https://cs.brown.edu/courses/cs033/docs/guides/x64_cheatsheet.pdf)



!!! info ""

    ### Instructions quick overview


    #### Jump Instructions

    |Instruction|Description|Condition Code|
    |:-|:-|:-|
    |sete / setz D | Set if equal/zero | ZF | 
    |setne / setnz D | Set if not equal/nonzero | ~ZF |
    |sets D | Set if negative | SF |
    |setns D | Set if nonnegative | ~SF |
    |setg / setnle D | Set if greater (signed) | ~(SF^0F)&~ZF |
    |setge / setnl D | Set if greater or equal (signed) | ~(SF^0F) |
    |setl / setnge D | Set if less (signed) | SF^0F |
    |setle / setng D | Set if less or equal | (SF^OF)|ZF |
    |seta / setnbe D | Set if above (unsigned) | ~CF&~ZF |
    |setae / setnb D | Set if above or equal (unsigned) | ~CF |
    |setb / setnae D | Set if below (unsigned) | CF |
    |setbe / setna D | Set if below or equal (unsigned) | CF/ZF |

    #### Jump Instructions

    | **Instruction** | **Description** | **Condition Code** |
    |:-|:-|:-|
    |jmp | Label | Jump to label |
    |jmp | *Operand | Jump to specified location |
    |je / jz | Label Jump if equal/zero | ZF|
    |jne / jnz|  Label Jump if not equal/nonzero | ~ZF |
    |js | Label Jump if negative | SF |
    |jns | Label Jump if nonnegative | ~SF |
    |jg / jnle | Label Jump if greater (signed) | ~(SF^0F)&~ZF |
    |jge / jnl | Label Jump if greater or equal (signed) | ~(SF^0F) |
    |jl / jnge | Label Jump if less (signed) | SF^0F |
    |jle / jng | Label Jump if less or equal | (SF^OF)|ZF |
    |ja / jnbe | Label Jump if above (unsigned) | ~CF&~ZF|
    |jae / jnb | Label Jump if above or equal (unsigned) | ~CF |
    |jb / jnae | Label Jump if below (unsigned) | CF |
    |jbe / jna | Label Jump if below or equal (unsigned) | CF|ZF |

    #### Conditional Move Instructions

    Conditional move instructions do not have any suffixes, but their source and destination
    operands must have the same size.

    | **Instruction** | **Description** | **Condition Code** |
    |:-|:-|:-|
    |cmove / cmovz S, D | Move if equal/zero | ZF |
    |cmovne / cmovnz S, D | Move if not equal/nonzero | ~ZF |
    |cmovs S, D | Move if negative SF |
    |cmovns S, D | Move if nonnegative | ~SF |
    |cmovg / cmovnle S, D | Move if greater (signed) | ~(SF^0F)&~ZF |
    |cmovge / cmovnl S, D | Move if greater or equal (signed) | ~(SF^0F) |
    |cmovl / cmovnge S, D | Move if less (signed) | SF^0F |
    |cmovle / cmovng S, D | Move if less or equal | (SF^OF)|ZF |
    |cmova / cmovnbe S, D | Move if above (unsigned) | ~CF&~ZF |
    |cmovae / cmovnb S, D | Move if above or equal (unsigned) | ~CF |
    |cmovb / cmovnae S, D | Move if below (unsigned) | CF |
    |cmovbe / cmovna S, D | Move if below or equal (unsigned) | CF|ZF |

    #### Procedure Call Instruction

    Procedure call instructions do not have any suffixes.

    | **Instruction** | **Description** | **Condition Code** |
    |:-|:-|:-|
    |call | Label Push return address and jump to label |
    |call | *Operand Push return address and jump to specified location |
    |leave |  | Set %rsp to %rbp, then pop top of stack into %rbp |
    |ret |  | Pop return address from stack and jump there |


