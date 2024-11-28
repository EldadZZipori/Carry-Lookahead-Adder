# 8-Bit Carry Lookahead Adder

## [title]
- `Schematics`
- `Graphing Simulations`
- `Operational Verification`
- `Timing Verification`

## Background
A carry look-ahead adder reduces the propagation delay by introducing more complex hardware. 
In this design, the ripple carry design is suitably transformed such that the carry logic over fixed groups of bits of the adder is reduced to two-level logic. (1)

```math
S_i = P_i \oplus C_i \\
C_{i+1} = G_i + P_i \cdot C_i
```

```math
C_1 = G_0 + P_0 C_{in} \\
C_2 = G_1 + P_1 C_1 = G_1 + P_1 G_0 + P_1 P_0 C_{in} \\
C_3 = G_2 + P_2 C_2 = G_2 + P_2 G_1 + P_2 P_1 G_0 + P_2 P_1 P_0 C_{in} \\
C_4 = G_3 + P_3 C_3 = G_3 + P_3 G_2 + P_3 P_2 G_1 + P_3 P_2 P_1 G_0 + P_3 P_2 P_1 P_0 C_{in}
```

## Design 
To implement the full carry lookahead circuit we built the building blocks for the circuit one by one. 

All functionalities were tested individually for every single block verifying its logical operation using stimuli. 
After each individual block was tested it was used to build a higher level block. 
All higher level blocks were also tested for logical functionality using automated code. 
For example - an inverter was built and tested and then used to build a xor gate that was also individually tested.

### Summary of Building Blocks 
- Inverter gate - 1 input 1 output
- And gate - 2 input 1 output
- Or gate - 2 input 1 output
- Xor gate - 2 input 1 output
- Full adder - 3 inputs (a,b, carryin) 4 outputs (sum, generate, propagate, carryout)
- 4 bit carry lookahead combinational logic - 9 inputs (4 generate, 4 propagate, 1 carryin) 4 outputs (carryout 1-4)
- 4 bit carry lookahead adder - 9 inputs (a 1-4, b 1-4, carryin) 5 outputs (sum 1-4, carryout)


## Final Result
The metric achieved was delay time of 2.05nanoseconds. This means that if this adder is the critical path of a system, the system can go at a
maximum clock frequency of 1/delay which will allow a clock speed of 4.88 GHz.

## Appendix

[1] - [GeeksForGeeks - Carry Look-Ahead Adder](ttps://www.geeksforgeeks.org/carry-look-ahead-adder/)