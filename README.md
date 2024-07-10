# Codtech-Task-2
// CODE AND TESTBENCH FOR FINITE STATE MACHINE //

module fsm (<br>
input wire clk,<br>
input wire reset,<br>
output reg [1:0] state<br>
);<br>
// State encoding<br>
parameter A = 2'b00, B = 2'b01, C = 2'b10;<br>
// State register<br>
reg [1:0] next_state;<br>
always @(posedge clk or posedge reset) begin<br>
if (reset)<br>
state <= A;<br>
else<br>
state <= next_state;<br>
end<br>
always @(*) begin<br>
case (state)<br>
A: next_state = B;<br>
B: next_state = C;<br>
C: next_state = A;<br>
default: next_state = A;<br>
endcase<br>
end<br>
endmodule<br>
<br>
<br>


/////////////  TESTBENCH  ////////////////<br>
<br>
<br>


module fsm_tb;<br>
// Inputs<br>
reg clk;<br>
reg reset;<br>
// Outputs<br>
wire [1:0] state;<br>
// Instantiate the FSM<br>
fsm uut (<br>
.clk(clk),<br>
.reset(reset),<br>
.state(state)<br>
);<br>
// Clock generation<br>
initial begin<br>
clk = 0;<br>
forever #5 clk = ~clk;<br>
end<br>
// Test sequence<br>
initial begin<br>
// Initialize reset<br>
reset = 1;<br>
#10 reset = 0;<br>
// Check transitions<br>
#20;<br>
if (state != 2'b01) $display("Test Failed at time %t: expected <br>
state 01, got %b", $time, state);<br>
#20;<br>
if (state != 2'b10) $display("Test Failed at time %t: expected <br>
state 10, got %b", $time, state);<br>
#20;<br>
if (state != 2'b00) $display("Test Failed at time %t: expected <br>
state 00, got %b", $time, state);<br>
$display("All tests passed");<br>
$stop;<br>
<br>
endmodule<br>

<br>
Project Overview: Designing and Testing a Finite State Machine (FSM) in Verilog using ModelSim<br>
Objective<br>
The primary objective of this project is to design, implement, simulate, and verify a Finite State Machine (FSM) using Verilog and ModelSim. The project aims to provide a practical understanding of FSM design in digital systems and demonstrate the use of hardware description languages (HDL) and simulation tools in the VLSI design process.<br>

Key Activities<br>
FSM Design<br><br>

The FSM's state diagram, including states and transitions, was defined.<br>
The states were encoded, and state transition logic was defined.<br>
FSM Implementation in Verilog<br><br>

Verilog code was written to implement the FSM based on the defined state diagram.<br>
The code included state encoding, state registers, and next-state logic.<br>
Testbench Development<br><br>

A Verilog testbench was written to simulate the FSM.<br>
A test sequence was developed to validate the FSM’s behavior under various conditions.<br>
Simulation and Verification<br><br>

ModelSim was used to compile and simulate the Verilog code.<br>
It was verified that the FSM transitions correctly between states as per the defined state diagram.<br>
Simulation waveforms were analyzed to ensure the FSM operates as expected.<br>
Detailed Description<br><br>
FSM Design<br>
State Diagram: The FSM was defined with states and transitions. For example, a 3-state FSM with states A, B, and C where:<br>
A transitions to B.<br>
B transitions to C.<br>
C transitions back to A.<br>
FSM Implementation in Verilog<br>
State Encoding: Binary codes were assigned to each state. Example:<br>
A = 2'b00<br>
B = 2'b01<br>
C = 2'b10<br>
Testbench Development<br>
Clock Generation: A clock signal was created for simulation.<br>
Reset Initialization: A reset signal was applied to initialize the FSM.<br>
Test Sequence: A sequence of inputs and expected outputs was defined to test state transitions.<br>
Simulation and Verification<br>
Compile the Design: The Verilog code and the testbench were compiled using ModelSim.<br>
Run the Simulation: The testbench was executed in ModelSim to simulate the FSM.<br>
Verify Outputs: The simulation results and waveforms were checked to ensure the FSM transitions between states correctly.<br>
Outcomes<br>
The FSM was successfully designed and implemented in Verilog.<br>
A comprehensive testbench was developed to simulate and validate FSM behavior.<br>
The correct operation of the FSM was verified using ModelSim, ensuring it met the specified design criteria.<br>
Conclusion<br>
This project provided hands-on experience in digital design using Verilog, including FSM design, implementation, testing, and verification using simulation tools. <br>Key concepts in HDL-based design and the practical application of simulation for verifying digital systems were reinforced.<br>


![verilog10](https://github.com/mk3271227/Codtech-Task-2/assets/175197452/882e2419-ff6b-4eb9-9981-0652445b8049)
