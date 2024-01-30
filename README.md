# FFT-implementation-in-RISCV-using-PCPI
The objective of this project is to design and implement an FFT co-processor for picorv32 using the PCPI interface. The co-processor will be able to perform FFT on 16-point complex input sequences and output the corresponding frequency spectra. The co-processor will be synthesized and tested on a Xilinx Vivado FPGA board.


Tools Used
Following tools are used:
• Software : Xilinx Vivado
• Language : VERILOG (VHDL)
Challenges
The main challenges of this project are:
• Designing a suitable architecture and data flow for the FFT co-processor that can
interface with the picorv32 CPU and the PCPI signals.
• Implementing the FFT algorithm efficiently and accurately using Verilog, considering the
word size, arithmetic operations, and twiddle factors.
• Optimizing the performance and resource utilization of the FFT co-processor, such as
reducing the latency, memory usage, and power consumption.
• Testing and verifying the functionality and correctness of the FFT co-processor using
simulation tools and FPGA hardware.
Contributions
The main contributions of this project are:
• Developing a novel FFT co-processor for picorv32 that can perform FFT on 16-point
complex input sequences using the PCPI interface.
• Demonstrating the feasibility and effectiveness of using PCPI to extend the functionality
of picorv32 with custom instructions and co-processors.
• Evaluating the performance and accuracy of the FFT co-processor and comparing it with
other existing implementations or benchmarks.
Methodology
The FFT co-processor is designed to accelerate the Fast Fourier Transform (FFT) calculations,
interfacing with the picorv32 CPU through PCPI signals. The PCPI interface allows for easy
integration of co-processors with the RISC-V CPU.
Design and Implementation
• PCPI Interface: The co-processor is connected using PCPI signals which include pcpi_valid,
pcpi_insn, pcpi_ready, pcpi_wait, pcpi_wr, pcpi_rd, and pcpi_im. These signals enable
communication between the CPU and the co-processor, such as sending and receiving data,
indicating instruction validity and readiness, requesting more time, and writing to registers. The
co-processor also uses a custom instruction for FFT that is encoded in the R-type format, with the
opcode 0110011 and the funct7 0000010.
FFT Algorithm
• We implemented a Radix-2 FFT algorithm for its simplicity and efficiency, suitable for real-time
processing. The algorithm performs a series of butterfly operations on the input data, which are
complex numbers with real and imaginary parts. The algorithm also uses twiddle factors, which
are complex numbers that represent the phase shifts of the frequency components. The algorithm
outputs the frequency spectrum of the input data, which are also complex numbers.
Data Flow
• Data from the CPU is sent to the FFT co-processor when pcpi_valid is high.
• The co-processor processes this data and sends back results when pcpi_ready goes high.
The data flow is as follows:
▪ The CPU sends the real and imaginary parts of the input data to the co-processor through
pcpi_rs1 and pcpi_rs2 respectively.
▪ The co-processor stores the input data in a buffer and initializes the twiddle factors.
▪ The co-processor performs the FFT algorithm on the buffer data, using the twiddle factors
and a bit-reversal index function.
▪ The co-processor outputs the real and imaginary parts of the output data to the CPU
through pcpi_rd and pcpi_im respectively, and sets pcpi_wr to high.
