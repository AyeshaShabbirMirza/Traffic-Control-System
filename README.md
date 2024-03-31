# Traffic-Control-System
The main objective of this project was to design a Traffic Control System for a T-intersection that consists of a timer at each road and operates the traffic lights in a proper order after a specific delay in time.

# Traffic Control System README

## Components
| Component                        | Quantity | Purpose                                       |
|----------------------------------|----------|-----------------------------------------------|
| And Gate (7408) ICs              | 1        | State decoding                                |
| Not Gate (7404) ICs              | 1        | Logic operations                              |
| Or Gate (7432) ICs               | 1        | Logic operations                              |
| Xor Gate (7486) ICs              | 1        | Logic operations                              |
| J-K Flip-Flops (7473) ICs        | 1        | State transition                              |
| BCD 7-Segment Driver (7447) ICs  | 1        | Display driver                                |
| 7-Segment Display Common Anode   | 1        | Visual indication                             |
| Breadboards                      | -        | Prototyping                                   |
| Connecting Wires                 | -        | Circuit connections                           |
| Jumper Wires                     | -        | Circuit connections                           |
| Power Supply                     | -        | Electrical power                              |
| Function Generator               | -        | Signal generation for testing                 |
| LEDs (Red, Yellow, and Green)    | -        | Visual indication                             |

## Overview
The Traffic Control System manages the sequence of traffic lights (Red, Yellow, Green) at intersections, ensuring timely transitions and safe traffic flow. The system consists of two units: Combinational Unit and Sequential Unit.

## State Diagram
The state diagram illustrates the sequence of states, conditions for each state, and transitions between states. Each state is represented by a 3-Bit Gray code, with transitions occurring based on the output T of And Gates connected to a 2-Bit Synchronous Counter.

## Combinational Unit
The Combinational Unit controls the sequence of traffic lights using And Gates as state decoders. The state decoder decodes the 3-Bit Gray code from the sequential logic to determine the current state and activate the corresponding output. State outputs are determined by Boolean expressions based on the input Gray code bits.

### Truth Table for State Decoder
| STATE INPUTS [GRAY CODE] | STATE OUTPUTS |
|---------------------------|---------------|
| G2 G1 G0                  | S1 S2 S3 S4 S5 S6 |
| 0  0  0                   | 1  0  0  0  0  0  |
| 0  0  1                   | 0  1  0  0  0  0  |
| 0  1  1                   | 0  0  1  0  0  0  |
| 0  1  0                   | 0  0  0  1  0  0  |
| 1  1  0                   | 0  0  0  0  1  0  |
| 1  1  1                   | 0  0  0  0  0  1  |

### Truth Table for Light Output Logic
| G2 G1 G0 | R 01 | R | Y | G |
|----------|------|---|---|---|
| 0  0  0  | 0    | 0 | 0 | 1 |
| 0  0  1  | 1    | 0 | 1 | 0 |
| 0  1  1  | 1    | 0 | 1 | 0 |
| 0  1  0  | 1    | 0 | 0 | 1 |
| 1  1  0  | 1    | 1 | 0 | 0 |
| 1  1  1  | 0    | 1 | 0 | 0 |

## Sequential Unit
The Sequential Unit includes Xor Gates, And Gates, synchronous counters, and clocks to manage state transitions and timing. A 2-Bit Synchronous Counter counts from 0 to 3, triggering state transitions. A 3-Bit Synchronous Counter counts from 0 to 7, generating Gray code numbers for display. Clock frequencies are set to control counter operation.

### Conversion Table
| DECIMAL EQUIVALENT | BINARY | GRAY CODE |
|---------------------|--------|-----------|
| 0                   | 000    | 000       |
| 1                   | 001    | 001       |
| 2                   | 010    | 011       |
| 3                   | 011    | 010       |
| 4                   | 100    | 110       |
| 5                   | 101    | 111       |

The Traffic Control System efficiently manages traffic light sequences using combinational and sequential logic. It ensures smooth transitions between states and safe traffic flow at intersections.
