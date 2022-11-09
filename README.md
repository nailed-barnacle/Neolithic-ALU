# Neolithic-ALU
This is a simple 8-bit ALU based on Ken Shirriff's dissection of the 8085's ALU at https://www.righto.com/2013/01/inside-alu-of-8085-microprocessor.html

It takes two inputs - A and B - and a number of control inputs to provide an output, one of:
- A (bypass)
- A OR B
- A AND B
- A XOR B
- A plus B with carry
- A minus B with carry 
- Complement of B
- A shifted right

Notes:

The carry input and output for arithmetic operations is inverted. To add or subtract without carry, it must be set. For other logic operations it must be set or cleared.

The zero output is inverted (i.e. set if the output is not zero).

The sign output is simply bit 7 of the result.

The bit shifted out after a right shift is the lowest input bit; it has no dedicated output. A dedicated input - shift_in - provides the high bit of the shift result.

At the time of posting, the only parts available for all components were 74HC; the circuit will operate across the 74HC range but will be faster at 5v than 3v3. I still need to measure the propagation delay but expect it to be around 60-70ns at five volts. Other equivalant parts - e.g. AHC or VLC - will probably be faster. The critical path is the chain of OR gates running right to left through the circuit.
