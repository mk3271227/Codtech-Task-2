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
