# General Description
- This is just going to be a pictures with dates and updates when i work on it, not really a guide or file specs
- There will be a Datasheets of ICs I purchased but the general parts are assumed to be had when making it
  - Things like Resistors, DIP switches, Buttons, Toggles, Capacitors, Diodes
    - I actually dont have regular diodes but only LEDs
   
# September 25th 2026
- Just opened the repo, things will be added as I get more free time
- Datasheets of ICs added
- Previously completed
  - 8 Bit program counter (PC) with LED signals
  - 10 Hz 555-timer clock
    - For now I just swap out the capacitor to convert to a 1 Hz clock
  - Reset button for resetting the PC
  - The 555-timer is on my [LinkedIn](https://www.linkedin.com/in/lauevansf/)
  - Next update depends on how busy school gets, but I really want to finish this

# September 26th 2026
<img width="2160" height="2880" alt="image" src="https://github.com/user-attachments/assets/34df1dc4-5b5c-4c35-afb3-bdb0d6a2bad1" />
- Blue lines are clock lines
- Red is 5v
- Black is GND

- Leftmost breadboard
  - 555-timer clock
  - Larger capacitor is to switch out the 47uF capacitor with a 470uF capacitor effectively making the frequency to 1 Hz
- Middle breadboard
  - Bus transceiver waiting to be repositioned
  - 8 signal bus to reach different breadboards
- Right breadboard
  - Program Counter (PC)
  - Counts to 8 bits (0 - 255) or 256 addresses 
  - Basically my maximum number of instructions at a time
