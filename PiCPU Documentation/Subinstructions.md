## `00 00` No Operation
Nothing happens
## `00 01` End Instruction
Increments the Program Counter to load the next instruction
## `00 FE` Change Counter Source
Sets the Counter Source Latch to High for the current cycle (C2), switching the counter's loading source from the memory to the lower 8 bits of the ProgramData
## `00 FF` Save Program Counter
Sets the WE of the Counter Memory high for one clock pulse (C1)
## `01 XX` Write Enable
Sets the WE address
## `02 XX` Output Enable
Sets the OE address
## `03 XX` Reset
Reset register