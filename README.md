nrf notes

SAADC
0-3.6V
8/10/12 bit sampling resolution: we select 12?

Note these commands are in Hex format:

00 - All off code 

4A AA AA AA BB CC DD DD DD - LED timing message where:
- 4A = "J" the command code 
- AA AA AA = full time interval [correspondence to the decimal conversion of AA concatenated with AA and AA (ex. decimal "001 002 003" leads to "001002003")]
- BB and CC correspond to decimal values for the duty cycles for LED1 and LED2
- DD DD DD are the hex->decimal numbers added up to give the period of oscillation for the square wave within the duty cycles ON of the LEDs
(when you do this long code it will run the full time interval for 100 times)

04 - change the SAADC to channel AIN0 at P0.02
05 - change the SAADC to channel AIN1 at P0.03
06 - change the SAADC to channel AIN2 at P0.04
07 - change the SAADC to channel AIN3 at P0.05
08 - change the SAADC to channel AIN4 at P0.28

Example:
I use "4A 00 0A 00 28 14 C8 C8 C8" to give the following parameters:
full time interval: 10000us = 10ms
duty cycle LED1 = 40%
duty cycle LED2 = 20%
period = 600us => 1666 Hz
