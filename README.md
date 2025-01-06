# VHDL Counter Overflow Bug

This repository demonstrates a common bug in VHDL code: an integer counter that can overflow.  The `counter.vhdl` file contains the buggy code. The `counter_fixed.vhdl` file shows the corrected version.

## Bug Description

The original VHDL code implements a simple counter. However, it lacks a check to prevent the `internal_count` signal from exceeding its defined range (0 to 15).  When the counter reaches 15, the next increment will wrap around to 0, resulting in an unexpected reset.  This can be a subtle bug that is difficult to detect.

## Solution

The solution involves adding a check within the `if rising_edge(clk)` statement to prevent the overflow. This is done in `counter_fixed.vhdl` by ensuring the counter only increments when it is less than 15.

## How to Reproduce

1. Simulate `counter.vhdl` and observe the counter behavior.  You should see the counter wrap around after it reaches 15.
2. Simulate `counter_fixed.vhdl` and observe the corrected behavior. The counter will stop incrementing when it reaches 15.

This example highlights the importance of range checking in VHDL designs to prevent unexpected behavior and ensure code robustness.