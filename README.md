## 4-BIT-RIPPLE-COUNTER
## AIM:

To implement 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

## SOFTWARE REQUIRED:

Quartus prime

## THEORY

## 4 Bit Ripple Counter

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

<img width="547" height="253" alt="image" src="https://github.com/user-attachments/assets/656e8626-0ced-4385-8827-0a9156763a73" />


In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

<img width="387" height="507" alt="image" src="https://github.com/user-attachments/assets/0161d486-0422-4849-9aeb-c3ef2b26ed1a" />




## Procedure 
1.Create Project: Open Quartus Prime, start a new project, and name it ripple_counter.

2.Write Code: Create a new Verilog HDL File, write the 4-bit ripple counter code, and save it.

3.Compile: Click Start Compilation and ensure there are zero errors.

4.Create Waveform: Open a new Vector Waveform File (VWF) and insert the clk, reset, and q[3:0] pins.

5.Set Inputs: Apply a toggling clock signal to clk and set reset to 0.

6.Simulate: Click Run Functional Simulation to generate the output waveforms. /* write all the steps invloved */

## PROGRAM
```

module exp6RC(q, clk, reset);

output [3:0] q;
input clk, reset;

T_FF tff0(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);

endmodule


module T_FF(q, clk, reset);

output q;
input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q);

endmodule


module D_FF(q, d, clk, reset);

output q;
input d, clk, reset;

reg q;

always @(negedge clk or posedge reset)
begin
    if (reset)
        q = 1'b0;
    else
        q = d;
end

endmodule
```

## RTL LOGIC FOR 4 Bit Ripple Counter
<img width="380" height="367" alt="image" src="https://github.com/user-attachments/assets/a6b42678-e024-47a6-a394-b5812bebc4a6" />


## TIMING DIGRAMS FOR 4 Bit Ripple Counter 
<img width="828" height="131" alt="image" src="https://github.com/user-attachments/assets/0981c108-0c30-459b-8477-883b672fef5d" />


## RESULTS
The functional simulation verified that the 4-bit ripple counter works correctly.Counting Sequence: With every clock pulse, the output increments sequentially in binary from 0000 (0) to 1111 (15).Rollover: After reaching 1111, the counter automatically resets and rolls over back to 0000 on the next clock pulse.
