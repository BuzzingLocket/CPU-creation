# General Description
- This is just going to be a pictures with dates and updates when i work on it, not really a guide or file specs
- I do not use AI to write the descriptions so I apologize if it a bit messy and confusing
  - It will be updated as my knowledge increases and I understand more and more
  - It will be updated when I add more things as well, like more breadboards or expansions like (ALU, SRAM, etc.)
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
  - Two chained 74HC161's to get to 8 bits since each is 4 bits
  - AND gate above it for the PoR circuit along with my pull up Reset switch
  - Will add an opcode reset eventually which is why there is one pin on that AND gate tied to 5v

- Future additions
  - Working on A and B registers right now
  - Working on a MAR 

# September 28th 2026
<img width="2160" height="2880" alt="image" src="https://github.com/user-attachments/assets/4766cc8c-840b-4faa-939d-dd3adfb8fa44" />
- Image is the PC from before along with a new board containing control signals
- Green wire is for control signal

- Changes
  - Added a Step Counter (SC)
  - From top down on the rightmost breadboard it is Inverter(04), Binary Counter(161), and a Decoder(138)
- Purpose
  - A CPU can't do everything in one pulse
  - Each instruction requires time to happen
  - We make this happen by including the SC, which allows for steps to happen each tick the PC counts
- How
  - The decoder is set so that when the SC counts to five(101) it resets back to zero by pushing the Y5(pin 10) output of the decoder onto the reset pin of the SC
  - By resetting the SC we can ensure that each count that the PC counts now contains 5 steps from 0 to 4 that allow for loading registers and running arithmetic
  - The control signal that enables the PC is referred to as the CE (Count enable)
  - The other outputs Y0-4 are for other control signals, letting the other parts of the CPU run when there is no other thing running at that instance
    - For example, if I am loading the register A, Y2 would be active, then Y3 is active and now I am loading register B and when Y4 is active then I can now save the sum of A + B
  - Not gate is there to ensure that the SC runs on the falling edge of the Clock
