
# Experiment--09-Implementation-of Shift-registers-using-verilog-
### AIM: To implement PISO , PIPO,PISO  using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

### Procedure
/* write all the steps invloved */



### PROGRAM (Serial Input Parallel Output (SIPO)):


/*
Program for  Implementation-of Shift-registers-using-verilog-
Developed by: Bharath K
RegisterNumber:  22009080
*/
````
module SIPO(SI,Clk,PO);
input SI,Clk;
output[0:7]PO;
reg[0:7]temp;
always@(posedge Clk)
begin
temp = {temp[0:6],SI};
end
assign PO = temp;
endmodule

````

### RTL LOGIC  REGISTERS   
![output](/213880397-c0d31fd8-181a-4a3f-9a86-6469e28f37c0.png)
### TIMING DIGRAMS FOR SHIFT REGISTERS
![output](/213880561-26ac0b34-4fc9-43bc-bcdf-a36107facf51.png)

## PROGRAM (Parallel Input Serial Output (PISO))

Program for  Implementation-of Shift-registers-using-verilog-

Developed by: Bharath K

RegisterNumber: 22009080
```

 module PISO(Clk, Parallel_In,load, Serial_Out);
 input Clk,load;
 input [3:0]Parallel_In;
 output reg Serial_Out;
 reg [3:0]tmp;
 always @(posedge Clk)
 begin
 if(load)
 tmp<=Parallel_In;
 else
 begin
 Serial_Out<=tmp[3];
 tmp<={tmp[2:0],1'b0};
 endmodule
```
### RTL LOGIC  REGISTERS   
![output](/213880444-89bea996-bab8-4dd5-b564-d3da1bb65a9d.png)

### TIMING DIGRAMS FOR SHIFT REGISTERS
![output](/213880598-04994991-eeea-47ca-85b9-8cb46d684934.png)
## PROGRAM (Parallel Input Parallel Output (PIPO)

  Program for  Implementation-of Shift-registers-using-verilog-
  Developed by: Bharath K
  RegisterNumber: 22009080
```
module PIPO(PI,Clk,PO);
input Clk;
input[3:0]PI;
output reg[3:0]PO;
always@(posedge Clk)
begin
PO = PI;
end 
endmodul
```
### RTL LOGIC  REGISTERS   
![output](/213880847-d5e17c76-7137-45a8-bb48-fcfc43144163.png)








### TIMING DIGRAMS FOR SHIFT REGISTERS

![output](/213880816-e81279e1-3245-4726-92ba-87cee3fbca2a.png)






### RESULTS 
Thus, PISO , PIPO, SIPO are implemented using verilog and their functionality using their functional tables is validated.