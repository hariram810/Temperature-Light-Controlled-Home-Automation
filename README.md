# Temperature-Light-Controlled-Home-Automation

![nnss](https://user-images.githubusercontent.com/118633170/202870366-ffd9c678-3a19-4f70-a45f-fe82bcc3f75b.png)


Here i use ldr sensor & dht11 Sensors to control the light , Fan Also How The Feed In I2C Lcd Display

If you have hard-time 3d printing stuff and other materials which i have provided in this project please refer the professionals for the help, JLCPCB is one of the best company from shenzhen china they provide, PCB manufacturing, PCBA and 3D printing services to people in need, they provide good quality products in all sectors

Please use the following link to register an account in JLCPCB

https://jlcpcb.com/RNA


Pcb Manufacturing


2 layers

4 layers

6 layers


PCBA Services

JLCPCB have 350k+ Components In-stock. You don’t have to worry about parts sourcing, this helps you to save time and hassle, also keeps your costs down.

Moreover, you can pre-order parts and hold the inventory at JLCPCB, giving you peace-of-mind that you won't run into any last minute part shortages.

3d printing

SLA -- MJF --SLM -- FDM -- & SLS. easy order and fast shipping makes JLCPCB better companion among other manufactures try out JLCPCB 3D Printing servies

JLCPCB 3D Printing starts at $1 &Get $54 Coupons for new users

Home automation or domotics is building automation for a home, called a smart home or smart house. A home automation system will monitor and/or control home attributes such as lighting, climate, entertainment systems, and appliances. It may also include home security such as access control and alarm systems. When connected with the Internet, home devices are an important constituent of the Internet of Things ("IoT").

![wsedfr](https://user-images.githubusercontent.com/118633170/202870296-d557107b-f7fb-46a0-b4b3-1ad1c73eb86f.png)
![eddened](https://user-images.githubusercontent.com/118633170/202870297-d692daca-604b-4ba0-a940-95b8dd7ca54d.png)


A home automation system typically connects controlled devices to a central smart home hub (sometimes called a "gateway"). The user interface for control of the system uses either wall-mounted terminals, tablet or desktop computers, a mobile phone application, or a Web interface that may also be accessible off-site through the Internet.
 
Parts

Arduino UNO
10 KΩ Resistor
20 KΩ Resistor
1 KΩ Resistor X 4
2N2222 NPN Transistor X 4
1N4007 Diode X 4
12 V Relay X 4
Prototyping board (Bread board)
Connecting wires
12 V Power supply
DHT22
LCD Display

The circuit design of Home Automation based on Arduino and Bluetooth is very simple and is explained below.

The Bluetooth module has 4 – pins: VCC, TX, RX and GND. VCC and GND are connected to 5V and ground from Arduino UNO. The Bluetooth module works on 3.3V and it has an on board 5V to 3.3V regulator.


![11111](https://user-images.githubusercontent.com/118633170/202870201-bb2604d5-0dcc-4862-b2ab-bcbc54a153cb.png)
![fvgb](https://user-images.githubusercontent.com/118633170/202870207-fab70ff9-8c37-433b-a846-2af746f278da.png)
![fcvf fg](https://user-images.githubusercontent.com/118633170/202870216-2f84413c-e26c-4eba-afb2-ef09eeae5c9a.png)

The TX and RX pins of the Bluetooth module must be connected to RX and TX pins of the Arduino. In Arduino UNO, we are defining pins 2 and 4 as RX and TX using software. Hence, TX of Bluetooth is connected to pin 4 of Arduino.

But when connecting RX of Bluetooth to TX of Arduino (or any microcontroller as a matter of fact), we need to be careful as the pin can tolerate only 3.3V. But the voltage from TX or Arduino will be 5V.

So, a voltage divider network consisting of 10K and 20K resistors are used to reduce the voltage to 3.3V approximately.

A resistor divider because it divides down the input voltage. We obtain the 3.3V level signal from the intersection of these two resistors.

The equation for a divided down voltage is Vout = [2.2k/(2.2k + 1k)]*5V = (2.2k/3.2k)*5V = 3.46V, which is close enough to 3.3V to prevent any damage to the HC-05.

This crude solution should never be used with a high-speed signal because the resistors form a low-pass RC filter with any parasitic capacitance on the connection.

As you can see the circuit is very simple and does not need many components to build. Let's start our explanation with the ESP8266-01 Wi-Fi module. You can also check out the video at the bottom of the page for a more detailed project explanation. To program the module, you need to first flash the firmware on the ESP8266 module and you also need to flash the firmware on the PIC12F675 module before doing anything.

The code section for this project will be divided into three sections because we are using two microcontrollers in our schematic, first one is an ESP8266 microcontroller and the second is a PIC microcontroller as you can see from the schematic. So the code for those two microcontrollers will be different and there will be another section where we will explain all the details about the webpage section.

Understanding the code for Atmel Microcontroller:

![dcf](https://user-images.githubusercontent.com/118633170/202870111-a805db75-ac1e-4a5e-b0db-fffcb4025a3f.png)
![sdefg](https://user-images.githubusercontent.com/118633170/202870122-db411da5-ac76-4e68-b5bc-b4b71207986e.png)
![sdfgf](https://user-images.githubusercontent.com/118633170/202870128-d98c5be2-8344-44a4-971d-1cebc14571a8.png)
![edftg](https://user-images.githubusercontent.com/118633170/202870133-38765d46-e68f-41be-b1d6-227cc6762d0e.png)


In this section, we will explain how the code for the PIC microcontroller works. We start our code by including all the required libraries in which some are builtin libraries and some are custom libraries. We also define all the required variables.

Next, we declare and define all the required functions that are needed for this code to work. The functions are enable_interrupt(): which is used to enable the external interrupt in the PIC Microcontroller. We also have disable_interrupt(): that is used to disable interrupt.

void enable_interrupt(){
    INTERRUPT_EDGE = FALLING;
    GLOBAL_INTERRUPT = ENABLE;
    EXTERNAL_INTERRUPT = ENABLE;
}
void disable_interrupt(){
    GLOBAL_INTERRUPT = DISABLE;
    EXTERNAL_INTERRUPT = DISABLE;
}
Next, we have our ADCInit() 

function that is used to configure the ADC for the PIC microcontroller.

void ADCInit()
{
   ADCON0bits.ADFM = 0; // Right Justified bit 7
   ADCON0bits.VCFG = 0; // Voltage Reference VDD bit 6
   ADCON0bits.CHS1 = 1; //set AN3 as input
   ADCON0bits.CHS0 = 1;//set AN3 as input
   ADCON0bits.ADON = 1;
   ADC_PORT = INPUT;
   ANSELbits.ANS3 = 1;
}
Up next we have our __custom_delay(unsigned int delay_data) function, in PIC microcontroller with XC8 we don't have the option to pass variables with the built-in delay function so this becomes necessary.

void __custom_delay(unsigned int delay_data){
    for(int i =0; i < delay_data; i++)
    {
        __delay_us(1);
    }
}
Next, we have defined the function through which we are processing the incoming ADC data from the pin of the microcontroller and that returns 8-bit ADC data.

unsigned int GetAdcvalue()
{
    ADCON0bits.GO = 1; //start the conversion
    __delay_us(200);
    while(ADCON0bits.GO==1){}; //wait for the conversion to end
    return ADRESH; //take the most significant bytes
}

![2223432](https://user-images.githubusercontent.com/118633170/202870041-6db7e95a-4d68-499b-aff5-aa8c05034b4f.png)
![dcf](https://user-images.githubusercontent.com/118633170/202870046-e6c06cd0-37fc-45b0-9ac5-adb69d8a41aa.png)
