# Keypad-Scanner
Designed 4x3 keypad scanner with debouncing, generating binary output &amp; valid signal for detected key presses.

# What is Keypad-Scanner
A **Keypad Scanner** is a digital system that detects which key is pressed on a matrix keypad and converts that into a binary code. It is commonly used in:

  - Digital Locks
  - ATM Keypads
  - Microwave Ovens
  - Security Systems and many more

A scanner for a keypad with three columns and four rows 
as in Figure 4-41. 



The keypad is wired in matrix form with a switch at the intersection of each row and column. Pressing a key establishes a connection between a row and column. The purpose of the scanner is to determine which key has been pressed and to output 
                                 
                                          a binary number : N5 N3 N2 N1 N0
                                          
                                          
which corresponds to the key number. 

For **example**, 

                 Pressing key 5 must output => 0101,

                 Pressing the * key must output => 1010, and
                 
                 Pressing the # key must output => 1011. 
                 
When a valid key has been detected, the scanner should output a signal **V** for one clock time. 

Assume that only one key is pressed at a time. The design must include hardware to protect the circuitry from malfunction due to keypad bounces. 


# Block Diagram

**Component Involved:** 
- **Keypad:** 4 rows (R0 - R3) and 3 columns (C0 - C2), making 12 buttons (3x4).
- **Microcontroller/Circuit block:** This is labeled as "Keypad scanner, debouncer, & decoder".
- **Resistors:** Connected to ground.




The overall block diagram of the circuit is presented in Figure 4-42. 

The keypad contains resistors that are connected to ground. When a switch is pressed, a path is established from the corresponding column line to the ground. If a voltage can be applied on 

                                          the column lines : C0, C1, and C2.
                                          
Then the voltage can be obtained on the row line corresponding to the key that is pressed. One among 

                                          the rows : R0, R1, R2, or R3
will have an active signal.



# Design Modules

We will divide the design into several modules, as shown in Figure 4-43.


The first part of the design will be a scanner that scans the rows and columns of the keypad. The keyscan module generates the column signals to scan the keyboard. 


The debounce module generates a signal **K** when a key has been pressed and a signal **Kd** after it has been debounced. When a valid key is detected, the decoder determines the key number from the row and column numbers.


**Scanner** <br>
We will use the following procedure to scan the keyboard: First apply logic 1s 
  
                    to columns : C0, C1, and C2.

and wait. 
If any key is pressed, a 1 will appear 

                    on rows : R0, R1, R2, or R3.
                    
Then apply a 1 to column C0 only. If any of the Ris is 1, a valid key is detected. 

If R0 is received, one knows that switch 1 was pressed.  <br>
If R1, R2, or R3 is received => it indicates switch 4, 7, or * was pressed. <br>
If so, set V 5 1 and output the corresponding N. <br>
If no key is detected in the first column, apply a 1 to C1 and repeat. <br> 
If no key is detected in the second column, repeat for C2. <br>

When a valid key is detected, apply 1s to C0, C1, and C2 and wait until no key is pressed. This last step is necessary so 
that only one valid signal is generated each time a key is pressed.



**Debouncer** <br>
As discussed in the scoreboard example, we need to debounce the keys to avoid malfunctions due to switch bounce. Figure 4-44 shows a proposed debouncing and 
synchronizing circuit. 

The four row signals are connected to an OR gate to form signal **K**, which turns on when a key is pressed and a column scan signal is applied. 
The debounced signal **Kd** will be fed to the sequential circuit.



**Decoder** <br>
The decoder determines the key number from the row and column numbers using the truth table given in Table 4-4. The truth table has one row for each of the 12 keys. 
The remaining rows have don’t care outputs since we have assumed that only one key is pressed at a time. 

Since the decoder is a combinational circuit, its output will change as the keypad is scanned. At the time a valid key is detected (K 5 1 and V 5 1), 
its output will have the correct value and this value can be saved in a register at the same time the circuit goes to S5.
