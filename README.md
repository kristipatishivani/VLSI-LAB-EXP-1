# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. 
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



# Logic Gates
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
# Half Adder
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
endmodule
module multi_2(a,b,p,carry);
input [1:0]a,b;
output [2:0]p;
output carry;
endmodule
```
# Full Adder
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Half Subtractor
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Subtractor
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
# 8 Bit Ripple Carry Adder
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
OUTPUT:
# Logic Gates
# And Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/dfcc96d4-c1c0-4c92-8868-04cb9fb10a0c)
# Or Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/bf325e6a-4493-417d-9a36-f1c77042581b)
# Nand Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/95918499-37ac-46f4-a98e-e7eeb87f3453)
# Nor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/a8175373-7740-42d5-8525-02d999bfb8f0)
# Xor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/d95850e9-c740-4991-85c9-fe7f0fab70d6)
# Xnor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/63bbf01f-2f16-4a42-8e62-0c6086cfe4e8)
# Not Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/1d7072be-d5d8-4e09-ad6f-e5182f8c4f9f)
# Half Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/d397a5cc-c568-4d78-8e6f-9685a5d52692)
# Full Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/39e406df-1c06-43dc-9f97-e068f5decdc7)
# Half Subtractor
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/5b384dcc-dc72-466c-9f67-463bf305a500)
# Full Subtractor
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/8af30d27-62d1-46dc-afdb-cb45e67537f4)
# 8 Bit Ripple Carry Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/267b59fd-7787-45bd-af69-65e3e03686d6)

RESULT:
        Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.

