Language name: "Recipe" (rcp) because Pi(e)
Format of this document: 
`Opcode in hex` `shorthand` Name
## `00` `nop` No Operation
Nothing happens
## Data Operations
### `01` `cpy` Copy
Copy data from the first specified register to the second specified register
### `02` `rst` Reset
Resets the specified register
## `1X` `ldd` Load Data Direct
Directly loads data into the [[Registers#Primary Targets (`0?`)]] register specified by `X`
Example:
```rcp
ldd(A) FFFF
```
or:
```rcp
ldd:PC FFFF
```
## Arithmetic Operations
### `20` `inc` Increment
Increments the specified register
### `21` `dec` Decrement
Decrements the specified register
### `22` `add` Add
$A + B + C[0] = D + SF[C_F]$
### `23` `sub` Subtract
$A - B - C[0] = D - SF[C_F]$
### `24` `mul` Multiply
$A \times B + C = D + (E << 16)$
E represents the product's upper bits. If $E \neq 0$, the Carry Flag is set to High
### `25` `mls` Signed Multiply
Same as the [[#`34` `mul` Multiply]] instruction, but using Two's Complement
### `26` `div` Divide
$(A + (B << 16)) \div C = D$
E is set to the remainder. If this remainder is not zero, the Carry Flag is also set
### `27` `dvs` Signed Divide
Same as the [[#`36` `div` Divide]] instruction, but using Two's Complement
### `28` `shl` Shift Left
$A << B = C$
### `29` `shr` Shift Right
$A >> B = C$
### `2A` `rol` Rotate Left
$A <<< B = C$
### `2B` `ror` Rotate Right
$A >>> B = C$
### `2C` `not` Logical NOT
B = ~A
### `2D` `and` Logical AND
A & B = C
### `2E` `lor` Logical OR
A | B = C
### `2F` `xor` Logical XOR
A ^ B = C
### `30` `nan` Logical NAND
~(A & B) = C
### `31` `nor` Logical NOR
~(A | B) = C
### `32` `xnr` Logical XNOR
~(A ^ B) = C
### `33` `neg` Negate
-A = B
## Program Flow Control
### `F0` `jmp` Jump
Jumps to the specified line without any condition
### `F1` `jmc` Jump If Carry
Jumps to the specified line if the carry bit in the [[Registers#`0C` System Flags]] register is High
### `F2` `jxz` Jump If X Zero
Jumps if the [[Registers#`07` X]] register is zero
### `F3` `jyz` Jump If Y Zero
Jumps if the [[Registers#`08` Y]] register is zero
### `F4` `jmr` Jump To Register
Jumps to the line specified by the register
### `F5` `jrc` Jump To Register If Carry
Jumps to the line specified by the register if the carry bit in the [[Registers#`0C` System Flags]] register is High
### `F6` `jrx` Jump To Register If X Zero
Jumps to the line specified by the register if the [[Registers#`07` X]] register is zero
### `F7` `jry` Jump To Register If Y Zero
Jumps to the line specified register if the [[Registers#`08` Y]] register is zero
### `F8` `wtc` Wait For Clock
Wait the specified amount of clock cycles
### `F9` `wtm` Wait Milliseconds
Wait the specified amount of milliseconds
### `FA` `wti` Wait For Interrupt
Wait until the the specified interrupt is invoked. The interrupt will be reset after the instruction
### `FB` `spz` Select Program At Zero
Change the active program and begin executing it at line zero
### `FC` `spm` Select Program at Memory
Change the active program and begin executing it at the last stored address in the Counter Memory
### `FD`
### `FE` `tri` Trigger Interrupt
Raises the specified interrupt if allowed
### `FF` `end` End Program
