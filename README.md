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
### Procedure
/* write all the steps invloved */
#### STEP 1:
 Create a new project in Quartus2 software .
 Exp-7-Synchornous-counters-/README.md at main · Nemaleshwar/Exp-7-Synchornous-counters
#### STEP 2:
 Name the project as uc for upcounter and dc for down counter.
####  STEP 3:
 Create a new verilog hdl file in the project file.
####  STEP 4:
 Name the module declare as dc and uc for down counter and upcounter.
#### STEP 5:
 Within the module declare input and output variables.
 #### STEP 6:
 Create a loop using if-else with condition parameter as reset.
#### STEP 7:
 End the loop.
#### STEP 8:
 End the module
 



### PROGRAM 
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: NATARAJ KUMARAN S
RegisterNumber: 23003973
*/
#### UP COUNTER
```verilogcode
Module upcounter(clk,a);
input clk;
output reg[3:0];
always @(posedge clk)
begin
a[3]=(a[2]&a[1]&a[0])^a[3];
a[2]=(a[1]&a[0])^a[2];
a[1]=(a[0]^a[1]);
a[0]= ^a[0];
end
endmodule
```
#### DOWN COUNTER
```verilogcode
Module downcounter(clk,a);
input clk;
output reg[3:0]a;
always @(posedge clk)
begin
a[3]=(~a[2]&~a[1]&~a[0])^a[3];
a[2]=(~a[1]&~a[0])^a[2];
a[1]=(~a[0]^a[1]);
a[0]=1^a[0];
end
endmodule
```

### RTL LOGIC UP COUNTER AND DOWN COUNTER 
#### UP COUNTER
![Screenshot 2024-01-02 183500](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/d2601a60-73fd-47f1-8641-939057a8c533)
#### DOWN COUNTER
![Screenshot 2024-01-02 183525](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/bc97a704-e7dc-4677-800f-33f55579ece3)


### TIMING DIGRAMS FOR COUNTER 
#### UP COUNTER
![Screenshot 2024-01-02 183542](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/b175eb68-b54a-46fb-b4c8-daffe3e52fd5)

#### DOWN COUNTER
![Screenshot 2024-01-02 183602](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/d047c5d1-dc7b-4635-bfa2-92858b697d80)






### TRUTH TABLE 
#### UP COUNTER
![Screenshot 2024-01-02 183625](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/0e74ba7f-62f8-4afa-934e-fd8f5abf75b2)


#### DOWN COUNTER
![Screenshot 2024-01-02 183653](https://github.com/nataraj26/Exp-7-Synchornous-counters-/assets/147514615/4a57f299-ef35-40da-b0ca-1cba69db7d55)






### RESULTS 
The 4 bit up and down counters has been implemented and validated the functionality.
