!!! info ""

    https://www.sciencebuddies.org/science-fair-projects/references/how-to-use-a-breadboard#name-breadboard

    - Breadboard ("solderless" breadboard) & Through-hole circuit board
    - Jumper wire kits https://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2150467_-1
    - LEDs have a positive side (called the anode) and a negative side (called the cathode)
    - Diodes are like one-way valves that only let electricity flow in one direction
    - Capacitors are components that can store electrical charge
    - Transistors are like electronically controlled switches

    - short circuits
    - multimeter

    - Integrated circuits (ICs)
        Many ICs come in something called a dual in-line package, or DIP, meaning they have two parallel rows of pins.
        If you want to connect a chip, you need to connect it across the gap in the middle of the breadboard
        
    - Circuit diagrams, or schematics
    
    - Through-hole vs. surface mount parts
        Breadboards are designed to work with through-hole electronic components. These components have long metal leads that are designed to be inserted through holes in a printed circuit board (PCB) that are plated with a thin copper coating, which allows the components' leads to be soldered to the board.
        Breadboards do not work with surface mount components. These components have short, flat pins on their sides that are designed to be soldered to the surface of a printed circuit board, instead of through holes.

    https://learn.sparkfun.com/tutorials/voltage-current-resistance-and-ohms-law


    -------------------------------
    ### Choose A Power Supply

    #### Question: I have a 3A power supply, will it break my 500mA circuit?
    
    No. A 3A power supply will not force 3A into your circuit. A 3A power supply will supply up to 3A of current. It’s your circuit that decides how much of that current it will actually use.

    (EDIT: Note that a power supply is not the same as a battery charger. Connecting a power supply with too much current directly to a battery could damage it)

    #### Question: My device says 5V (DC) 1A. What power supply do I need?
    
    You need a power supply that gives 5V DC and has a maximum current of more than 1A.
    
    ##### Question: My circuit needs 9V, can I use my 12V supply?

    No. If your circuit needs 9V and you connect it to 12V, it’s a good chance it will break.
    
    -----------------------------




    GPS
    https://www.sparkfun.com/gps
    https://www.adafruit.com/product/746	https://www.jameco.com/z/4279-Adafruit-Industries-Adafruit-Ultimate-Gps-Gnss-with-USB-99-Channel-with-10-Hz-Updates_2517871.html?srsltid=AfmBOorObxPJ1dGGtdoS7z6lGr9EZi3VcljR5XZxWJ-72yfe3WSIt6kaKD0
    https://www.adafruit.com/product/4415
    https://www.adafruit.com/product/4279


    Arduino comparison
    https://www.sparkfun.com/standard_arduino_comparison_guide
    https://learn.sparkfun.com/tutorials/choosing-an-arduino-for-your-project


    Kit
    https://www.sparkfun.com/products/21301
    https://store-usa.arduino.cc/products/arduino-education-starter-kit?pr_prod_strat=e5_desc&pr_rec_id=cf6bc6233&pr_rec_pid=6813188554959&pr_ref_pid=6544108159183&pr_seq=uniform
    https://store-usa.arduino.cc/products/arduino-replacements-pack?pr_prod_strat=jac&pr_rec_id=40be2e783&pr_rec_pid=6544223207631&pr_ref_pid=6813188554959&pr_seq=uniform

    https://docs.arduino.cc/hardware/mkr-gps-shield/?queryID=fdac64c9e30f82767feb97f95e285a8d
        https://www.arduino.cc/reference/en/libraries/arduino_mkrgps/
        https://store-usa.arduino.cc/products/4g-module-global

    Sellers
    https://novelda.com/
    https://www.gilisymo.com/
    https://jlcpcb.com/



    Projects
    https://steemit.com/utopian-io/@kimp0gi/interfacing-gsm-and-gps-module-using-arduino-a-step-by-step-guide-tutorial-for-tracking


    Project research
    https://www.reddit.com/r/arduino/comments/19937aa/which_board_replaces_the_mkr_gsm_1400/?rdt=62824
    https://codeberg.org/johan-m-o/BikeTracker


    Project Purchase list
        https://www.sparkfun.com/products/23386
        Uno R3
        https://www.sparkfun.com/products/21301

    Important references
        https://www.elecrow.com/wiki/?title=32u4_with_A7_GPRS/GSM





    Fix it
    https://www.youtube.com/watch?v=wkAp5x3Z_gc&pp=ygUUbXVsdGltZXRlciB2b2x0bWV0ZXI%3D

    Multimeters - The Complete Guide
    https://www.youtube.com/watch?v=viitNbwrUMI

    GPS Modules with Arduino and Raspberry Pi
    https://www.youtube.com/watch?v=kwk3qzaIcCU

    MUST BUY
    https://www.adafruit.com/product/4279
    https://www.adafruit.com/product/851
    https://www.adafruit.com/product/85
    https://www.adafruit.com/product/3806
    https://www.adafruit.com/product/3445
    https://www.adafruit.com/product/2975


    Best Guide
    https://learn.adafruit.com/how-to-choose-a-microcontroller


!!! info ""

    ## JTAG (Joint Test Action Group) & UART (Universal Asynchronous Receiver / Transmitter)


    ### JTAG

    ![alt text](/Knowledge_Base//Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12-s//Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12-0.png)


    ### UART
    
    ![alt text](/Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12--1.png)

    #### Communication in UART can be:
    - simplex (data is sent in one direction only)
    - half-duplex (each side speaks but only one at a time)
    - full-duplex (both sides can transmit simultaneously)

    #### Timing and synchronization of UART protocols

    - UART is that is asynchronous, the transmitter and receiver do not share a common clock signal.
    - Since they do not share a clock, both ends must transmit at the same, pre-arranged speed in order to have the same bit timing.
    - The most common UART baud rates are 4800, 9600, 19.2K, 57.6K, and 115.2K.

    #### UART frame format

    ![alt text](/Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12--2.png)

    **As with most digital systems**
    - “high” or "mark" voltage level is used to indicate a logical “1”
    - “low” or "space" voltage level is used to indicate a logical “0”
    
    Note that in the idle state (where no data is being transmitted), the line is held high. This allows an easy detection of a damaged line or transmitter.


    ##### Start and stop bits
    
    Because UART is asynchronous, the transmitter needs to signal that data bits are coming. This is accomplished by using the start bit.
    The start bit is a transition from the idle high state to a low state, and immediately followed by user data bits.
    After the data bits are finished, the stop bit indicates the end of user data. The stop bit is either a transition back to the high or idle state or remaining at the high state for an additional bit time. A second (optional) stop bit can be configured, usually to give the receiver time to get ready for the next frame, but this is uncommon in practice.

    ##### Data bits
    
    The data bits are the user data or “useful” bits and come immediately after the start bit. There can be 5 to 9 user data bits, although 7 or 8 bits is most common. These data bits are usually transmitted with the least significant bit first.

    **Example**
    If we want to send the capital letter “S” in 7-bit ASCII, the bit sequence is 1 0 1 0 0 1 1. We first reverse the order of the bits to put them in least significant bit order, that is 1 1 0 0 1 0 1, before sending them out. After the last data bit is sent, the stop bit is used to end the frame and the line returns to the idle state.

    7-bit ASCII ‘S’ (0x52) = 1 0 1 0 0 1 1
    LSB order = 1 1 0 0 1 0 1

    ###### Start and stop bits

    ![alt text](/Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12--3.png)

    ###### Data bits

    ![alt text](/Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12--4.png)


    ###### Parity bit

    A UART frame can also contain an optional parity bit that can be used for error detection. This bit is inserted between the end of the data bits and the stop bit. The value of the parity bit depends on the type of parity being used (even or odd):

    - In even parity, this bit is set such that the total number of 1s in the frame will be even.
    - In odd parity, this bit is set such that the total number of 1s in the frame will be odd.
    
    **Example**

    Capital “S” (1 0 1 0 0 1 1) contains a total of three zeros and 4 ones. If using even parity, the parity bit is zero because there already is an even number of ones. If using odd parity, then the parity bit has to be one in order to make the frame have an odd number of 1s.
    
    The parity bit can only detect a single flipped bit. If more than one bit is flipped, there’s no way to reliably detect these using a single parity bit.

    ![alt text](/Knowledge_Base/images/HW-HKNG-s98uhnos8-sjns12--5.png)

    #### Summary
    Asynchronous means no shared clock, so for UART to work, the same bit or baud rate must be configured on both sides of the connection.
    Start and stop bits are used to indicate where user data begins and ends, or to “frame” the data.
    An optional parity bit can be used to detect single bit errors.
    serial ports are almost always UART-based. Such as devices using RS-232 interfaces, external modems, etc.


!!! info ""
    
    ## Soldering

    
    ### Resources
    - [Branchus Creations - Beginner's Guide to Soldering Electronics Part 3: Surface Mount Soldering](https://www.youtube.com/watch?v=o8UmA6oC_tU)



!!! info 

    ## Tools




!!! info ""

    ## Resources






