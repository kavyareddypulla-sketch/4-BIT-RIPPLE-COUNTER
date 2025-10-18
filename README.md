# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

<img width="680" height="340" alt="image" src="https://github.com/user-attachments/assets/43e6407e-f5c1-4630-ba3a-0a2c529babff" />


In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.
<img width="501" height="628" alt="image" src="https://github.com/user-attachments/assets/c2d1e017-d071-4b20-a7c0-f58c49881a50" />

**Procedure**
1.Type the program in Quartus software.
2.Compile and run the program.
3.Generate the RTL schematic and save the logic diagram.
4.Create nodes for inputs and outputs to generate the timing diagram.
5.For different input combinations generate the timing diagram


/* write all the steps invloved */

**PROGRAM**
 Developed by:KAVYA P
 RegisterNumbe:25008896

module RippleCounter(
   input wire clk,  // Clock input
   output reg [3:0] count // 4-bit counter output
);

// Counter logic
always @(posedge clk) begin
   if (count == 4'b1111) // Reset when count reaches 15
       count <= 4'b0000;
   else
       count <= count + 1; // Increment count
end

endmodule

// Testbench
module RippleCounter_tb;

// Inputs
reg clk;

// Outputs
wire [3:0] count;

// Instantiate the counter
RippleCounter uut(
   .clk(clk),
   .count(count)
);

// Clock generation
initial begin
   clk = 0;
   forever #5 clk = ~clk; // Toggle clock every 5 time units
end

// Stimulus
initial begin
   // Wait for a few clock cycles
   #10;
   
   // Display header
   $display("Time | Count");
   $display("-----------------");
   
   // Functional table testing
   // Increment count 16 times and display the count
   repeat (16) begin
       #5; // Wait for one clock cycle
       $display("%4d | %b", $time, count);
   end
   
   // End simulation
   $finish;
end

endmodule
/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by: kavya p
 RegisterNumber:25008896*/

**RTL LOGIC FOR 4 Bit Ripple Counter**
<img width="1158" height="525" alt="image" src="https://github.com/user-attachments/assets/1c600eb9-a3f5-482e-92ad-ab5ded8b356b" />


**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
<img width="1270" height="316" alt="image" src="https://github.com/user-attachments/assets/6deb7710-a9eb-4e1c-bcd7-67f02e2224c9" />

**RESULTS**
The 4-bit ripple counter was successfully implemented using Verilog in Quartus Prime. The functionality was verified using a testbench, which simulated the counter's operation. The counter correctly counted from 0000 to 1111, incrementing by 1 on each clock pulse. After reaching 1111, the counter reset to 0000, as expected. The timing diagrams and the functional table showed that the ripple counter operated as intended, with each flip-flop toggling on the rising edge of the previous flip-flop's output. The simulation results confirmed the correct operation of the 4-bit ripple counter.
