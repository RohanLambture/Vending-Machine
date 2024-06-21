# Vending Machine 

## Overview
This project is a Verilog implementation of a vending machine controller. The vending machine allows for item selection, money input, item dispensation, and transaction cancellation. It also features a display system to show the current balance and item count using seven-segment displays.

## Features
- **Item Selection**: Users can select items with varying costs.
- **Money Input**: Supports multiple increments of money input.
- **Item Dispensation**: Dispenses items when sufficient balance is available.
- **Transaction Cancellation**: Allows users to cancel a transaction and reset the balance and item count.
- **Display System**: Shows the current balance and item count on seven-segment displays.

## Module Descriptions

### vendingMachine_1
This is the main module that integrates all the functionalities of the vending machine.

**Inputs:**
- `DATA [2:0]`: Input data for item selection.
- `load1, load3, load4`: Signals for loading money into the machine.
- `take1, take2, take3, take4`: Signals for item dispensation.
- `start, clk, rst, cancel`: Control signals for starting, resetting, and cancelling a transaction.

**Outputs:**
- `co`: Clock output.
- `inputDATA [4:0]`: Extended data input.
- `itemCount [4:0]`: Number of items selected.
- `money [5:0]`: Current balance in the vending machine.
- `moneySign`: Sign of the balance (0 for positive, 1 for negative).
- `SSD_tens, SSD_ones [6:0]`: Seven-segment display outputs for balance.
- `outputDATA [2:0]`: Data output.

**Functionality:**
- Handles the core functionality of money input, item dispensation, and transaction cancellation.
- Updates the balance and item count based on user inputs.
- Converts binary data to decimal and drives seven-segment displays for visual feedback.

### multiply_by_4bit
Performs multiplication of a 3-bit number by a 4-bit number.

**Inputs:**
- `number1 [2:0]`: First number.
- `number2 [3:0]`: Second number.

**Outputs:**
- `result [5:0]`: Multiplication result.
- `c_out`: Carry out (not used).

### BinaryToDecimal
Converts a 5-bit binary number to a decimal value.

**Inputs:**
- `binary [4:0]`: Binary input.

**Outputs:**
- `decimal [4:0]`: Decimal output.

### DecimalSplitter
Splits a decimal number into tens and ones.

**Inputs:**
- `decimal [4:0]`: Decimal input.

**Outputs:**
- `dec_tens [3:0]`: Tens digit.
- `dec_ones [3:0]`: Ones digit.

### BCD_to_SevenSegment
Converts a BCD digit to a seven-segment display format.

**Inputs:**
- `bcd_input [3:0]`: BCD input.

**Outputs:**
- `seven_segment_output [6:0]`: Seven-segment display output.

### disp_add
Combines the BCD to seven-segment conversion for tens and ones digits.

**Inputs:**
- `dec_tens [3:0]`: Tens digit.
- `dec_ones [3:0]`: Ones digit.

**Outputs:**
- `s_tens [6:0]`: Seven-segment display for tens digit.
- `s_ones [6:0]`: Seven-segment display for ones digit.

### fivebitadd_display
Displays a 5-bit binary number on two seven-segment displays.

**Inputs:**
- `A [4:0]`: Binary input.

**Outputs:**
- `SSD_tens, SSD_ones [6:0]`: Seven-segment display outputs for tens and ones digits.

### carry_lookahead_Adder
Implements a carry look-ahead adder for fast addition.

**Inputs:**
- `in1, in2 [n-1:0]`: Numbers to add.
- `cin`: Carry-in.

**Outputs:**
- `sum [n-1:0]`: Sum of the inputs.
- `cout`: Carry-out.

## Usage
To use the vending machine, follow these steps:
1. Load money using the `load1`, `load3`, and `load4` signals.
2. Select items using the `take1`, `take2`, `take3`, and `take4` signals.
3. Monitor the current balance and item count on the seven-segment displays.
4. Cancel a transaction using the `cancel` signal if needed.
5. Reset the machine using the `rst` signal.
