# VSDSquadron-FM-research-Internship

## Task 1: RGB LED Control

**Objective:** Understand and document the provided Verilog code, create the necessary PCF file, and integrate the design with the VSDSquadron FPGA Mini board.

### Step 1: Understanding the Verilog Code

* **Access the Verilog Code:**
    * [top.v](https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/top.v)

* **Key Signal Definitions:**
   
    * Output wires for the RGB LED (led_red, led_green, led_blue).
  
  ![image](https://github.com/user-attachments/assets/128fe372-9e2f-438c-ab0c-37b3fa23b706)

    * Input wire for the external hardware clock (hw_clk).

![image](https://github.com/user-attachments/assets/a96e54a2-183f-4480-bdf0-69aed02c1e0a)
    
  * Output wire for testing purposes (testwire).

![image](https://github.com/user-attachments/assets/58118b6d-89ad-4c81-a44c-4949e59a1ca1)

* **Analyze the Internal Components:**
    * **CLKHFPU:** Internal oscillator power up.
    * **CLKHFEN:** Enabling internal oscillator.
 
![image](https://github.com/user-attachments/assets/72e253e7-6eff-4082-8c16-07f3a24bf2fe)
 .
    * Frequency counter logic driven by the internal oscillator.
    * RGB LED driver instantiation with defined current parameters.
    * **RGB LED Configuration:**
        * RGBLEDEN: Enables LED.
        * RGB0PWM: Red LED PWM (Pulse Width Modulation).
        * RGB1PWM: Green LED PWM.
        * RGB2PWM: Blue LED PWM.
        * CURREN: Current control.

![image](https://github.com/user-attachments/assets/35ee4f5a-e5da-4447-996a-eaa4207ab04d)

* **Documentation of Functionality:**
    * The `top` module controls an RGB LED using pulse width modulation (PWM) and an internal oscillator. It includes a frequency counter for a test signal and an RGB driver for LED color management.
    * The internal logic contains a frequency counter that counts clock cycles from the internal oscillator and provides a test output.
    * The internal oscillator generates a high-frequency clock signal, driving the frequency counter.
    * The RGB LED driver changes the RGB LED color.
    * The outputs (led_red, led_green, led_blue) directly control the RGB LED hardware.

### Step 2: Creating the PCF File

* **Access the PCF File:**
    * [VSDSquadronFM.pcf](https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf)

* **PCF File Contents:**

    ```
    set_io led_red 39
    set_io led_blue 40
    set_io led_green 41
    set_io hw_clk 20
    set_io testwire 17
    ```

    * `set_io` defines the connection between named ports and physical hardware pins.

* **Pin Assignments:**
    * led_red -> Pin 39
    * led_blue -> Pin 40
    * led_green -> Pin 41
    * hw_clk -> Pin 20
    * testwire -> Pin 17

### Step 3: Integrating with the VSDSquadron FPGA Mini Board

* **Datasheet Review:**
    * Review the VSDSquadron FPGA Mini board datasheet for features and pinout.

* **Correlation:**
    * Use the datasheet to match physical board connections with the PCF file and Verilog code.

* **Connection:**
    * Connect the board to the computer (e.g., USB-C, FTDI connection).

* **Building and Flashing:**
    * Follow the provided Makefile: [Makefile](https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/Makefile)
        * Change directory to the `led_blue` directory.
        * Run `make clean` to clear previous builds.

![image](https://github.com/user-attachments/assets/0cb3ea9e-5f26-4eac-95b6-a39f0c818f4a)
        * Run `make build` to compile the design.

![image](https://github.com/user-attachments/assets/df62da5d-2428-403b-b3f9-d060e6ad82bc)
        * Run `sudo make flash` to program the FPGA board.

![image](https://github.com/user-attachments/assets/ee489ddb-890f-4f4d-9bca-6bca83349539)

* **Observation:**
    * Observe the RGB LED behavior to confirm successful programming.

vshttps://github.com/user-attachments/assets/6b44cb89-9789-46ac-a4a6-6eace46933b8

 
## Task 2: Using UART

**Objective:** Implement a UART loopback mechanism where transmitted data is immediately received back, facilitating testing of UART functionality.

Block Diagram

![image](https://github.com/user-attachments/assets/98066c76-2be3-4e93-b966-aeaa0b6bc331)

Flashing

![Screenshot 2025-03-27 230735](https://github.com/user-attachments/assets/d4c9d768-7c7a-485f-97fb-ce3702bde055)

Testing Results

![image](https://github.com/user-attachments/assets/63a66f6b-e2e4-4802-b641-75f567623adc)


