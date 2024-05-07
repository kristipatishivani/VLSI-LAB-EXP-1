EXP-1

date:

                                               SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS
                                               
AIM: To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.

APPARATUS REQUIRED: VIVADO 2023.2

PROCEDURE: 

STEP:1 Start the Xilinx navigator, Select and Name the New project. 

STEP:2 Select the device family, device, package and speed. 

STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. 

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 

STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. 

STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 

STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. 

STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

STEP:12 Load the Bit file into the SPARTAN 6 FPGA.


LOGIC GATES LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

 VERILOG CODE
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
OUTPUT WAVEFORM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/a62e4538-0094-4126-b762-1a1fdc1e8931)

**HALF ADDER

LOGIC DIAGRAM**

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/8dbaa111-3916-4e39-bd03-852cd2d76982)

VERILOG CODE
```
module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

xor g1(sum,a,b);

and g2(carry,a,b);

endmodule
```
OUTPUT WAVEFORM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/d325278a-9829-4e71-b638-70f7285a1dcd)

**FULL ADDER

LOGIC DIAGRAM**

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/8713d8b5-e4b6-4c9d-a00b-41eae22c9a2c)

VERILOG CODE
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
OUTPUT WAVEFORM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/5c2e8258-da0f-4afd-98eb-f56bd8c7ec30)

**HALF SUBTRACTOR

LOGIC DIAGRAM**

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/a2ece9c5-3ea5-4656-ac14-51ae2f150460)

VERILOG CODE
```
module halfsub(a,b,diff,borrow);

input a,b;

output diff,borrow;

xor(diff,a,b);

and(borrow,~a,b);

endmodule
```
OUTPUT WAVEFORM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/4bdf087c-428c-4822-bc46-c5e7dd254033)

FULL SUBTRACTOR LOGIC DIAGRAM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/1b5c2122-0560-4d64-8eca-093cc6a727ec)

VERILOG CODE
```
module fs(a,b,bin,d,bout);

input a,b,bin;

output d,bout;

wire w1,w2,w3;

xor(w1,a,b);

xor(d,w1,bin);

and(w2,~a,b);

and(w3,~w1,bin);

or(bout,w3,w2);

endmodule
```
OUTPUT WAVEFORM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/bc8d00b2-5048-427d-bf2c-c02c3045914c)

RIPPLE CARRY ADDER LOGIC DIAGRAM

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/a99aff44-dfa3-4e7b-9da8-69196df7a695)

VERILOG CODE
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

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
```
OUTPUT WAVEFORM


![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/6bf9e606-80cb-4def-8503-210f60b0fbd4)

RESULT:

       simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 is verified.



















