**Lab 1 consists of:**
+ Lab 1-1
+ Lab 1-2

**Lab 1-1: I/O COMMUNICATION AND COMPUTATIONAL INSTRUCTIONS**

_EXERCISE 1:_

a) Connect one AVR port (e.g., PORT A) to a DIP switch. Connect another port (e.g., PORT B) to a bar LED.  
b) Write a program that continuously reads the state of the DIP Switch and outputs it to the LED. If the switch is OFF, the corresponding will turn off.  

**.ORG 0** <br>
LDI R16, 0X00 <br>
OUT DDRA, R16 <br>
LDI R16, 0XFF <br>
OUT PORTA, R16 <br>
LDI R16, 0XFF <br>
OUT DDRB, R16 <br>
**MAIN:** <br>
IN R17, PINA <br>
COM R17 <br>
OUT PORTB, R17 <br>
RJMP MAIN <br>
<img width="645" height="595" alt="image" src="https://github.com/user-attachments/assets/cb3c0b23-6a8d-43ff-99eb-acd8d59bcacc" />
<img width="466" height="204" alt="image" src="https://github.com/user-attachments/assets/28f71171-c1c6-4d9b-be44-ee99ec05a432" />
<img width="401" height="188" alt="image" src="https://github.com/user-attachments/assets/4d8384f7-c729-4e7c-bc20-0e9bb38cb86c" />

_EXERCISE 2:_ 

a) Write a program that reads the value of the port connected to the DIP Switch, adds 5, and sends the result to the port connected to the bar LED.  
b) Change the state of the DIP Switch and observe the bar LED.

**.ORG 0** <br>
LDI R16, 0X00 <br>
OUT DDRA, R16 <br>
LDI R16, 0XFF <br>
OUT PORTA, R16 <br>
LDI R16, 0XFF <br>
OUT DDRB, R16 <br>
**MAIN:** <br>
IN R17, PINA <br>
COM R17 <br>
LDI R18, 5 <br>
ADD R17, R18; Cộng giá trị 2 thanh ghi R17 <-- R17 + R18 <br>
OUT PORTB, R17 <br>
RJMP MAIN <br> 
<img width="654" height="599" alt="image" src="https://github.com/user-attachments/assets/1ef0cdc7-b7a7-421b-9318-3ffcdf02af6e" />
<img width="365" height="196" alt="image" src="https://github.com/user-attachments/assets/8752d2a5-c34c-4ac2-ab9a-57e728aa7303" />
<img width="411" height="198" alt="image" src="https://github.com/user-attachments/assets/7ae099fa-062e-4729-916f-c330ba03500d" />



