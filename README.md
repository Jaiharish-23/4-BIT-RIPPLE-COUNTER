# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

1.Code Overview: Understand the Verilog module ripple_counter, which includes clock (clk) and reset (rst) inputs, and a 4-bit output count. The counter increments on each positive clock edge unless reset is asserted, resetting the count to 0.

2.Simulation Preparation: Use a Verilog simulator (e.g., ModelSim) and write a testbench module to apply clock and reset signals while monitoring the counter output.

3.Testbench Implementation: Instantiate the ripple_counter module in the testbench, generate clock and reset signals, apply them to the counter module, and observe the count output.

4.Simulation Execution: Compile both the counter module and the testbench, simulate the design, and verify that the counter counts from 0 to 15 (binary 1111) and resets to 0 when the reset signal is activated.

5.Verification and Debugging: Analyze timing diagrams to ensure proper counter behavior, debug any encountered issues during simulation, and make necessary modifications to the design for optimal functionality

**PROGRAM**


 Developed by: Jai Harish R
 RegisterNumber:24006817
*/
```
module RippleCounter(
   input wire clk, 
   output reg [3:0] count 
);
always @(posedge clk) begin
   if (count == 4'b1111) 
       count <= 4'b0000;
   else
       count <= count + 1;
end
endmodule
module RippleCounter_tb;
reg clk;
wire [3:0] count;
RippleCounter uut(
   .clk(clk),
   .count(count)
);
initial begin
   clk = 0;
   forever #5 clk = ~clk; 
end
initial begin
   #10;
   $display("Time | Count");
   $display("-----------------");
   repeat (16) begin
       #5; 
       $display("%4d | %b", $time, count);
   end
   $finish;
end
endmodule
```
**RTL LOGIC FOR 4 Bit Ripple Counter**
![{735BC81F-D442-4A0C-92D5-E9EE5ED043B8}](https://github.com/user-attachments/assets/f7199957-768e-4fe2-90be-1d0afdebe7b9)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![330602293-564c2c83-af3f-4b2b-80d7-ea046405e10f](https://github.com/user-attachments/assets/89c0cbe2-6324-414d-b6af-d6bbd3fd32b4)


**RESULTS**

Thus 4-bit-ripple-counter has been executed successfully

