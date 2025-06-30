# Keypad-Scanner
Designed 4x3 keypad scanner with debouncing, generating binary output &amp; valid signal for detected key presses.

# what is Keypad-Scanner
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

                 pressing key 5 must output 0101,

                 pressing the * key must output 1010, and
                 
                 pressing the # key must output 1011. 
                 
When a valid key has been detected, the scanner should output a signal **V** for one clock time. 

Assume that only one key is pressed at a time. The design must include hardware to protect the circuitry from malfunction due to keypad bounces. 
