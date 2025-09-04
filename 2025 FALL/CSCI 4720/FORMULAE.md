# 1.
![[REPO/2025 FALL/CSCI 4720/1 - CPU + Performance/Pasted Images/CPU Clocking.png]]
- frequency / rate - cycles per second
	- In terms of Hz (1 Hz = 1 cycle per second)

- CPU time = clock cycles / rate
- clock cycles = CPU time * rate
- **clock cycles = Instructions * Avg clock cycles per Instruction (CPI)**

- Execution time or CPU time = clock cycle time * Instructions * CPI
- Execution time or CPU time = Instructions * CPI / clock_rate
- **CPI = (CPUTime * Clock Rate / Instruction Count) **
### Selecting 2 code sequences **run on the SAME CPU**
   *same cpu means clock time is the same (constant)*

![[2 code segments CPI example.png]]

- Total Clock Cycles = total CPI x IC
- CPI = TotalClock Cycles / IC

- Power = CapactitativeLoad x Voltage^2 x Freq(Rate)
- CapacitativeLoad = Power / (V^2 * f)


- SPEC Ratio = Reference Time / Execution Time

# 2.
