## Developed by: Shivaram.M
## RegisterNumber: 212223040195
# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure :
1.Create a New Project: Open Quartus and create a new project by selecting "File" > "New Project Wizard." Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA). 2.Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File." Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language. ⦁ Write the Combinational Logic Code:

Open the newly created Verilog or VHDL file and write the code for your combinational logic. 3.Compile the Project: To compile the project, click on "Processing" > "Start Compilation" in the menu. Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device. 4.Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window. Review and fix any issues in your code if necessary. View the RTL diagram. 5.Verification: Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF". Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.

Give the Input Combinations according to the Truth Table and then simulate the Output Waveform.

### PROGRAM :
## Up counter :

module exp_6(clk, A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

 A[2]=(((A[0])&(A[1]))^A[2]);
	
 A[1]=(A[0])^A[1];
	
 A[0]=A[0]^1;

end

endmodule

## Down Counter :

module EXP_6B(clk,A);

input clk;

output reg[2:0]A;

always @(posedge clk)

begin

 A[2]=(((~A[0])&(~A[1]))^A[2]);

A[1]=(~A[0])^A[1];
	
A[0]=1^A[0];

end

endmodule

### RTL LOGIC UP COUNTER AND DOWN COUNTER  

## Up counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/ccc0946f-9fa1-445c-a6c5-e78192648a42)

## Down counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/9db343ce-6445-48b3-904d-ea603c16fb74)

### TIMING DIGRAMS FOR COUNTER  

## Up counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/b5f2b4bb-250e-44ce-84cb-5d2f0b2bb2a0)

## Down counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/02c3a4b2-c92d-45eb-9c4f-870169a49152)


### TRUTH TABLE 

## Up counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/d78f182c-23de-4258-b530-6918705c1255)

## Down counter :

![image](https://github.com/Shivaram2525/Exp-7-Synchornous-counters-/assets/144226303/c732ecdd-2364-4bf9-8fa1-e067301eecd8)

### RESULTS 
By this we have verified the truth table of 4-bit up-counter using verilog.
