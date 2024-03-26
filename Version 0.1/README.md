# Version 0.1

 "Control Panel" block implementation and "Input keyboard" implementation

 ## "Control Panel" block implementation

"Control Panel" block is the way in which the user can interact with the computer and perform the following operations:
- computer reset
- Manual or Automatic operating mode selection
- program advancement step by step in Manual Mode
- computer programming by editing RAM memory content in programming mode
- setting work mode, Program run or Programming
- byte address setting
- setting binary data value that will be memorized
- storing value in memory

### Circuitul pentru reset

It has the role of initializing the Instruction register through the CLR signal and Program Counter and Ring Counter through the /CLR signal.
It consists of a push button with return and a debouncing circuit.
The debouncing circuit can be realized by RS latch or by monostable, here a debouncer with latch RS was used.
