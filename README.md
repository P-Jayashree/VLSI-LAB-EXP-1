# Simulation and Implementation of Logic Gates, Adder and Subtractor
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: vivado 2023.2

PROCEDURE: STEP:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

# Full Adder:
```
module fulladder (sum, cout, a,b,c);
input a,b,c;
output sum, cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and al(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,w2,w3); or o2(cout,w5,w4);
endmodule
```
# Full Subractor:
```
module full_subtractor(a, b, c,D, Bout);
input a, b, c;
output D, Bout;
assign D = a^b^c;
assign Bout = (~a & b) | (~(a^ b) & c);
endmodule
```
# Half Adder:
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
or(sum,a,b);
and(carry,a,b);
endmodule
```
# Half Subractor:
```
module half_subtractor(D,Bo,A,B);
input A,B;
output D,Bo;
assign D=A^B;
assign Bo=(~A)&B;
endmodule
```
# Logic Gates:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Ripple Carry Adder 4Bit:
```
module rippe_adder(S, Cout, X, Y,Cin);
 input [3:0] X, Y;// Two 4-bit inputs
 input Cin;
 output [3:0] S;
 output Cout;
 wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;  
  wire w1,w2,w3;  
  xor G1(w1, X, Y); 
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
```
# Ripple Carry Adder 8bit
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule
```
OUTPUT:
# Full Adder
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/657722a1-4fb9-4511-81c3-91b8b34f0806)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/cf116333-3d48-454e-82f3-a7e151f322f3)

# Full Subractor
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/319f0d1b-21bd-4962-8cbe-291c29a9ae8b)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/1be8a3dc-0c89-4081-9515-6571f6daf077)

# Half Adder
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/5440d274-0bcf-4a6d-86a5-d63741ae3b66)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/a733bd57-83db-49f5-87f6-4e62e5929361)

# Half Subractor
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/bbacedf9-c95e-4e3e-bee8-b8974c1bfbef)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/eead9b72-5beb-4317-8d49-6f9b06d85628)

# Logic Gates
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/f08f2d79-b13e-4c8f-8591-3a6f732d4e4a)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/e3d87922-c9d6-4132-9bf8-31647f64f388)

# Ripple Carry Adder 4bit
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/2fb669a9-27bd-4024-9e5e-22a681b06678)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/93186581-7533-44c5-be64-d8db91189bf8)

# Ripple Carry Adder 8bit
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/e93fd4be-cfca-46a6-bdf6-2a4dd21decd5)
![image](https://github.com/P-Jayashree/VLSI-LAB-EXP-1/assets/161108372/165faa8a-fbe8-45d3-91c4-94f0606d463e)


RESULT:
Thus To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE has been verified.


