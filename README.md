# 4 KB-ROM-Memory-with-Read-and-Write-Operations
**Aim**
To design and simulate a 4KB ROM memory with read and write operations using Verilog HDL and verify the functionality through a testbench in the Vivado 2023.1 simulation environment.

**Apparatus Required**
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.

**Procedure**
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code for ROM:

Write the Verilog code for a 4KB ROM memory with read and write capabilities.
Create the Testbench:

Write a testbench to simulate both the read and write operations, verifying that the data is correctly written to and read from the memory.
Add the Verilog Files:

Add the ROM Verilog module and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado and check the memory's read and write operations.
Observe the Waveforms:

Analyze the waveform to verify that the memory read and write operations work as expected.
Save and Document Results:

Capture the waveform and include the simulation results in the final report.
Verilog Code for 4KB ROM Memory with Read and Write Operations
In this design, we will implement a 4KB ROM. Since ROM is typically read-only, we will simulate the behavior as if it's writable, but in actual hardware, ROM is typically pre-programmed.
4KB = 4096 Bytes = 4096 x 8 bits
The address width for 4KB memory is 12 bits (2^12 = 4096).

**Verilog Code:**
   
    module rom_design(clk,rst,address,dataout);
    input clk,rst;
    input[2:0] address;
    output reg[3:0] dataout;
    reg [3:0] rom_design[7:0];
    initial begin
    rom_design[0]=4'd1;
    rom_design[1]=4'd2;
    rom_design[2]=4'd3;
    rom_design[4]=4'd10;
    rom_design[5]=4'd11;
    rom_design[6]=4'd12;
    rom_design[7]=4'd15;
    end
    always@(posedge clk) begin
    if(rst)
    dataout=4'd0;
    else
    dataout=rom_design[address];
    end 
    endmodule

**Testbench Code For ROM**:
      
    module rom_design_tb;
    reg clk,rst;
    red[2:0]address;
    wire[3:0]dataout;
    rom_design dut(
     .clk(clk),
     .rst(rst),
     .address(address),
     .dataout(dataout)
    );
    initial begin
     clk=1'b0;
     forever #5 clk=~clk;
    end
    intitial begin
     rst=1'b1;
     address=3'b000;
     #10 rst=1'b0;
     #10 address=3'b000;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b001;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b010;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b100;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b101;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b110;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 address=3'b111;
     #10 $display("Address: %d, Dataout: %d, address, dataout);
     #10 rst=1'b1;
     #10 $display("Reset asserted, Dataout: %d, dataout);
     end 
    endmodule
     
**Output:**
![Screenshot 2024-11-13 174049](https://github.com/user-attachments/assets/46d75cec-c7b5-440d-ac55-ca584a19ae72)


**RAM -Memory-with-Read-and-Write-Operations**Aim**
To design and simulate a RAM memory with read and write operations using Verilog HDL and verify the functionality through a testbench in the Vivado 2023.1 simulation environment.

**Apparatus Required**
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.

**Procedure**
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code for RAM:

Write the Verilog code for a RAM memory with read and write capabilities.
Create the Testbench:

Write a testbench to simulate both the read and write operations, verifying that the data is correctly written to and read from the memory.
Add the Verilog Files:

Add the ROM Verilog module and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado and check the memory's read and write operations.
Observe the Waveforms:

Analyze the waveform to verify that the memory read and write operations work as expected.
Save and Document Results:

Capture the waveform and include the simulation results in the final report.

**Verilog Code:**

    module ram(clk,rst,en,data_in,data_out,address);
    input clk,rst,en;
    input[11:0] address;
    input[7:0] data_in;
    output reg[7:0] data_out;
    reg[1023:0] mem[7:0];
    always@(posedge clk)
    begin
    if(rst)
    data_out<=8'd0;
    else if(en)
    mem[address]<=data_in;
    else
    data_out<=mem[address];
    end 
    endmodule

**Testbench code for RAM:**

    module rom_design_tb;
    reg clk,rst;
    reg[2:0]address;
    wire[3:0]dataout;

    rom_design dut(
     .clk(clk),
     .rst(rst),
     .address(address),
     .dataout(dataout)
    );
    initial begin
    rst=1'b1;
    address=3'b000;
    #10 rst=1'b0;
    #10 address=3'b000;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b001;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b010;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b100;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b101;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b110;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 address=3'b111;
    #10 $display("Address: %d, Dataout:%d, address, dataout);
    #10 arst=1'b1;
    #10 $display("Reset assertion, Dataout:%d,dataout);
    end
    endmodule

**Output:**

![verilog](https://github.com/user-attachments/assets/44337cfd-f6b3-4236-9fac-df82e6868b30)




**FIRST IN FIRST OUT[FIFO]:**

To design and simulate a FIFO memory using Verilog HDL and verify the functionality through a testbench in the Vivado 2023.1 simulation environment.

**Apparatus Required**
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.

**Procedure**
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code for FIFO:

Write the Verilog code for a FIFO memory with read and write capabilities.
Create the Testbench:

Write a testbench to simulate both the read and write operations, verifying that the data is correctly written to and read from the memory.
Add the Verilog Files:

Add the ROM Verilog module and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado and check the memory's read and write operations.
Observe the Waveforms:

Analyze the waveform to verify that the memory read and write operations work as expected.
Save and Document Results:

Capture the waveform and include the simulation results in the final report.

**Verilog Code:**

    module fifo_8 #(parameter depth=8, data_width=8)
     (input clk,rst,
     input w_en,r_en,
     input [data_width-1:0] data_in,
     output reg[data_width-1:0] data_out,
     output full, empty);
    reg[$clog2(depth)-1:0] w_ptr, r_pt;
    reg[data_width-1:0] fifo [depth-1:0];
    always@(posedge clk) begin
     if(lrst) begin
     w_ptr<=0;
     r_ptr<=0;
     data_out<=0;
     end 
    end
    always@(posedge clk) begin
    if(w_en && !full) begin
     fifo[w_ptr]<=data_in;
     w_ptr<=(w_ptr+1) % depth;
     end
    end
    always@(posedge clk) begin
     if(r_en && !empty) begin
      data_out<=fifo[r_ptr];
      r_ptr<=(r_ptr+1) % depth;
     end
    end
    assign full =(w_ptr+1==r_ptr);
    assign empty=(w_ptr==r_ptr);
    endmodule

**Testbench code for FIFO:**

    module fifo_8_tb;
    reg clk,rst;
    reg w_en, r_en;
    reg[7:0] data_in;
    wire[7:0] data_out;
    wire full,empty;

    fifo_8 #(depth(8), .data_width(8)) dut(
     .clk(clk),
     .rst(rst),
     .w_en(w_en),
     .r_en(r_en),
     .data_in(data_in),
     .data_out(data_out),
     .full(full),
     .empty(empty)
    );
    initial begin
     clk=1'b0;
     forever #5 clk= ~clk;
    end
    initial begin
     rst=1'b1;
     w_en=1'b0;
     r_en=1'b0;
     data_in=8'd0;
     #10 rst=1'bo;
     #10 w_en = 1'b1;
     data_in=8'd1;
     #10;
     w_en=1'b0;
     $disaply("Write 1,Full: %b, Empty: %b, full, empty);
     #10 w_en=1'b1;
     data_in=8'd2;
     #10;
     w_en=1'b0;
     $disaply("Write 2,Full: %b, Empty: %b, full, empty);
     #10 w_en=1'b1; data_in=8'd3; #10; w_en=1'b0;
     #10 w_en=1'b1; data_in=8'd4; #10; w_en=1'b0;
     #10 w_en=1'b1; data_in=8'd5; #10; w_en=1'b0;
     #10 w_en=1'b1; data_in=8'd6; #10; w_en=1'b0;
     #10 w_en=1'b1; data_in=8'd7; #10; w_en=1'b0;
     #10 w_en=1'b1; data_in=8'd8; #10; w_en=1'b0;
     $display("Write 3-8, Full: %b, Empty: %b, full, empty);
     #10 r_en=1'b1;
     #10;
     r_en=1'b0;
     $display("Read 1, Data: %d, Full: %b, Empty: %b, data_out, full, empty);
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     #10 r_en=1'b1; #10; r_en=1'b0;
     $display("Read 2-8, Full: %b, Empty: %b, full,empty);
     #10 w_en=1'b1;
     data_in=8'd9;
     #10;
     $display("Pverflow, Full: %b, Empty: %b, full, empty);
     #10 r_en=1'b1;
     #10;
     $display("Underflow, Full: %b, Empty: %b, full, empty);
     end
    endmodule

**Output:**
 
  ![fifo](https://github.com/user-attachments/assets/62db8711-d357-4729-ac77-4bc0c81e0c50)




Conclusion
In this experiment, a 4KB ROM and RAM memory with read and write operations and FIFO was designed and successfully simulated using Verilog HDL. The testbench verified both the write and read functionalities by simulating the memory operations and observing the output waveforms. The experiment demonstrates how to implement memory operations in Verilog, effectively modeling both the reading and writing processes for ROM,RAM and FIFO.
