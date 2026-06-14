# FSM-Based Vending Machine Controller
**RTL Design | Verilog HDL | Synthesized on Artix-7 FPGA**

## Overview
A Vending Machine Controller in Verilog HDL using FSM architecture. Handles coin-based payment, online payment, product selection, automatic change return, and transaction cancellation. Synthesized on Xilinx Artix-7 (xc7a50tcsg325-1) using Vivado 2024.2.

## Features
- Dual payment modes: Coin insertion + Online payment bypass
- 5 product support via 3-bit product code
- Automatic change calculation and return
- Cancel transaction at any state
- Fully synthesizable RTL

## Simulation Results

### Online Payment Flow
![Online Payment](simulation/waveform_online_payment.png)
- START + ONLINE_PAYMENT=1 → skips coin collection → direct dispense
- PRODUCT_PRICE=10, ONLINE_PAYMENT=1 → DISPENSE_PRODUCT HIGH, RETURN_CHANGE_VALUE=0 ✅

### Coin Payment — Multiple Products
![Coin Payment](sim/waveform_coin_payment.png)
- Product 1: Price=20, Coins=20 → Dispense ✅, Change=0
- Product 4: Price=20, Coins=30 → Dispense ✅, Change=10
- State transitions 0→1→6→7→0 verified ✅

## Synthesis Results — Xilinx Artix-7 (xc7a50tcsg325-1)

|
 Resource
|
 Used
|
 Available
| 
 Utilization
|
|
|----------
|------
|-----------
|-------------
|
|

| 
 Slice LUTs
|
 45
|
 32,600 
|
 0.14%
|
| 
 Flip-Flops 
|
 16 
|
 65,200
| 
 0.02% 
|
|
 I/O Ports 
|
 34
|
 150
|
 22.67% 
|
|
 BUFGCTRL
|
 1 
|
 32 
| 
 3.13%
|
|
 Block RAM
|
 0
|
 75
|
 0.00%
|
|
 DSPs
|
 0
|
 120
|
 0.00% 
|

### RTL Schematic
![Schematic 1](synth/schematic_1.png)
![Schematic 2](synth/schematic_2.png)

Full utilization report: [synth/utilization_report.txt](synth/utilization_report.txt)

## Project Structure
- src/VendingMachine.v

- src/VendingMachineTB.v

- simulation/# Waveform screenshots

- synth/# Schematic + utilization report

## Tools
- Xilinx Vivado 2024.2
- Target: xc7a50tcsg325-1 (Artix-7, Speed Grade -1)
- HDL: Verilog (IEEE 1364-2001)
