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

_EXERCISE 3:_  
a) Connect and write a program that multiplies the upper and lower nibbles of PORTA and sends the result to PORTB. Assume both nibbles are unsigned numbers.
Example: PORTA = 0B0001_1111, then PORTB = 1*15.  
b) Change the state of the DIP Switch and observe the bar LED.

**MAIN:** <br>
**.ORG 0** <br>
LDI R16, 0X00 <br>
OUT DDRA, R16 <br>
LDI R16, 0XFF <br>
OUT PORTA, R16 <br>
OUT DDRB, R16; Cấu hình PORTB - Output <br>
IN R17, PINA <br>
COM R17; Switch ON = LED ON - Switch OFF = LED OFF <br>
MOV R18, R17 <br>
ANDI R18, 0B00001111 <br>
SWAP R17 <br>
MOV R19, R17 <br>
ANDI R19, 0B00001111 <br>
MUL R19, R18 <br>
OUT PORTB, R0 <br>
**RJMP MAIN** 
<img width="927" height="839" alt="image" src="https://github.com/user-attachments/assets/ed3b8085-ce2c-464f-9295-8ac23c5b2bd6" />
<img width="547" height="297" alt="image" src="https://github.com/user-attachments/assets/1bd64456-39a4-49c0-9cd9-fd53871a7b42" />
<img width="616" height="290" alt="image" src="https://github.com/user-attachments/assets/b565ee15-35a7-4aa7-b321-113335c4abf9" />

_EXERCISE 4:_  
a) Connect and write a program that multiplies the upper and lower nibbles of PORTA and sends the result to PORTB. Assume both nibbles are signed numbers.  
Example: PORTA = 0B0111_1111, then PORTB = 3*(-1).  
b) Change the state of the DIP Switch and observe the bar LED.  

**MAIN:** <br>
**.ORG 0** <br>
LDI R16, 0X00 <br>
OUT DDRA, R16 <br>
LDI R16, 0XFF <br>
OUT PORTA, R16 <br>
OUT DDRB, R16; Cấu hình PORTB - Output <br>
IN R17, PINA <br>
COM R17 <br>
MOV R18, R17 <br>
SBRC R18, 3; Kiểm tra bit thứ 3 của nibble thấp có dấu là gì (0 - dương, 1 - âm) <br>
RJMP L1 <br>
ANDI R18, 0B00001111 <br>
L2: <br>
SWAP R17 <br>
MOV R19, R17 <br>
SBRC R19, 3 <br>
RJMP L3 <br>
ANDI R19, 0B00001111 <br>
L4: <br>
MULS R19, R18 <br>
OUT PORTB, R0 <br>
**RJMP MAIN** <br>
L1: <br>
	ORI R18, 0B11110000 <br>
	RJMP L2 <br>
L3: <br>
	ORI R19, 0B11110000 <br>
	RJMP L4  
  **TH1: PORTA = 0011_0101 --> 3*5 = 15** <BR>
  <img width="530" height="287" alt="image" src="https://github.com/user-attachments/assets/5ea60b94-a0be-4bf4-a7b6-05a54250c826" />
  <img width="912" height="813" alt="image" src="https://github.com/user-attachments/assets/883fa114-702d-4da7-8feb-b925eff71e9b" />
  <img width="607" height="285" alt="image" src="https://github.com/user-attachments/assets/e56c0d22-143c-4e24-b3f2-c5c804eb7a28" />  
 **TH2: PORTA = 1001_1101 --> (-7)*(-3) = 21** <BR>
 <img width="540" height="288" alt="image" src="https://github.com/user-attachments/assets/aca3e5eb-9402-4a57-a474-92cbe7a953ab" />
 <img width="913" height="835" alt="image" src="https://github.com/user-attachments/assets/f289d766-c6b2-4d17-aa1c-f87e6d14a117" />
 <img width="610" height="282" alt="image" src="https://github.com/user-attachments/assets/3e253ca6-e202-40d2-8c6e-0438dcf281e2" />

 _EXERCISE 5:_  
 a) Connect PA0 to a single switch and PA1 to a single LED on the LED block (note: same port).  
 b) Write a program to turn ON the LED when the switch is pressed, and turn it OFF when the switch is released.

**MAIN:** <br>
**.ORG 0** <br>
CBI DDRA, 0 <br>
SBI PORTA, 0 <br>
SBI DDRA, 1 <br>
**L1:** <br>
SBIC PINA, 0 <br>
RJMP TAT_LED <br>
**BAT_LED:** <br>
SBI PORTA, 1 <br>
**RJMP L1** <br>
**TAT_LED:** <br>
CBI PORTA, 1 <br>
**RJMP L1** <br>
**TH1: PA0 = 0 - SWITCH ON** <BR>
<img width="441" height="156" alt="image" src="https://github.com/user-attachments/assets/45e66a3f-a6fc-4d98-bdbc-fef346ba3d00" />
<img width="1170" height="321" alt="image" src="https://github.com/user-attachments/assets/889c6916-39ba-4b61-af8d-db35084ffc82" /> <BR>
**TH2: PA0 = 1 - SWITCH OFF** <BR>
<img width="440" height="152" alt="image" src="https://github.com/user-attachments/assets/a514770d-e7a6-4fcc-a744-83a50df1a7a3" />
<img width="1194" height="327" alt="image" src="https://github.com/user-attachments/assets/a8c3af7b-2dce-4d8a-b4b4-401e31ad19bf" />











 








