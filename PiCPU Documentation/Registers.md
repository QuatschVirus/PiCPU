Well, sometimes also "Registers", aka Data sources/targets
## Primary Targets (`0?`)
All of these can be represented by 4 bits, allowing them to be run as "primary" targets
### `01` A
### `02` B
### `03` C
### `04` D
### `05` E
### `06` F
### `07` X
### `08` Y
### `09` Memory Address (`MA`)
### `0A` Memory Data (`MD`)
### `0B` Program Selector (`PS`)
### `0C` System Flags (`SF`)
`IC?? ????`
#### `I`IRQ
Interrupt request. An interrupt has been set and is requesting to be handled
#### `C` Carry
The carry flag

### `0D` System Control (`SC`)
`I??? ????`
#### `I` Interrupt Enable
Allows or disallows interrupts to be raised. They will still be processed
### `0E` 
### `0F` Program Data (`PD`)
## User Interface (`1?`)
### `10` Numeric Display 0 (`ND0`)
### `11` Numeric Display 1 (`ND1`)
### `12` Numeric Display 2 (`ND2`)
### `13` Numeric Display 3 (`ND3`)
### `14` Hexadecimal Display 0 (`HD0`)
### `15` Hexadecimal Display 1 (`HD1`)
### `16` Hexadecimal Display 2 (`HD2`)
### `17` Hexadecimal Display 3 (`HD3`)
### `18` Terminal Control (`TC`)
### `19` Terminal Data (`TD`)
Write Only, prints the character represented by the lowest 7 bits to the Terminal
### `1A` Keyboard Control (`KC`)
### `1B` Keyboard Data (`KD`)
Read only, reads the next character form the keyboard's buffer
### `1C` LEDs (`LED`)
### `1D` Buttons (`BTN`)
Read only, each bit indicates whether the button has been pressed. Resets after being read
### `1E`
### `1F`

## System Internals (`2?`)
### `20` ALU Operation
### `21` ALU Operator A
### `22` ALU Operation B
### `23` ALU Operation C
### `24` ALU Result Low
### `25` ALU Result High
### `26` Program Selector
### `27` Program Counter
### `28`SI bus
Allows the lowest 8 bits into the lower 8 bits of the Subinstruction bus
### `29`
### `2A`
### `2B`

### `2C` 
### `2D` 
### `2E` Counter Return
Where the program should return to after processing all raised interrupts
### `2F` Interrupt
Writing places the interrupt in the interrupt queue, and ensures the IRQ flag is set.
Reading reads the last interrupt and removes it from the queue.
The queue can hold 16 interrupts
## Ports (>= `70`)
**`1XXX XXXX`**
`X` indicates the bits used as the port address, allowing up to 128 ports to be directly controlled