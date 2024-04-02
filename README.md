# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

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
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 8 Bit Ripple Carry Adder
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
OUTPUT:
# Logic Gates
# And Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/4bf726cf-efed-493d-a22c-37516968afe1)
# Or Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/9c885f08-61b8-47ae-aea3-622c9c0a6731)
# Nand Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/440ed87c-fbbd-4a54-ae9d-1738a193922e)
# Nor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/87cf7e59-2450-4fdc-8f80-c5fcfc626564)
# Xor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/15fe78df-e0f5-4a0e-990a-5620ec45f685)
# Xnor Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/b2f72798-0a11-4eeb-80a4-a07177218a10)
# Not Gate
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/69d1e008-d356-438d-b06f-42e319cc6488)
# Half Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/c165c219-2fe8-479b-b5e5-25ffc5dc9a27)
# Full Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/c5abfe9d-1809-4fb6-9757-5a490eb5fe50)
# Half Subtractor
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/cb388612-2022-4923-a86a-b6d3fd4e6b2e)
# Full Subtractor
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/1d20e8d9-8f6f-443f-8d08-add9004f8720)
# 8 Bit Ripple Carry Adder
![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-1/assets/161432255/f06059b6-3229-4b75-a19b-6bad9a8024ac)

RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.

