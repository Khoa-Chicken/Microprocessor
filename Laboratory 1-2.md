<div align="center">
  
**LAB 1-2: DELAY USING INSTRUCTIONS**
</div>

_EXERCISE 1:_  
a) Given the following program:  
.include "m324PAdef.inc" <br>
.org 00 <br>
&emsp; ldi r16,0x01 <br>
&emsp; out DDRA, r16 <br>
start: <br> 
&emsp; sbi PORTA,PINA0 <br>
&emsp; cbi PORTA, PINA0 <br>
&emsp; rjmp star <br>
Connect PA0 to a measurement channel on the TEST STATION block and measure the waveform on the oscilloscope.  
<img width="656" height="685" alt="image" src="https://github.com/user-attachments/assets/7b63dcd2-fdd4-4e89-9724-ea7d33035a65" />
<img width="1376" height="878" alt="image" src="https://github.com/user-attachments/assets/c4773db0-0b69-445b-af61-560a43bd5dde" />

_EXERCISE 2:_  
a) Write a function <Delay1ms> and use it to write a program that generates a 1kHz square wave on PA0.  
b) Using this function, write additional subroutines: Delay10ms, Delay100ms and Delay1s.  
c) Use the Delay1s function to write a program that blinks an LED connected to PA0.  

**.ORG 0** <BR>
**SET_UP:**  <BR>
&emsp;	SBI DDRA, 0  <BR>
**MAIN:**  <BR>
&emsp;	SBI PORTA, 0  <BR>
&emsp;	RCALL Delay_0_5ms  <BR>
&emsp;	CBI PORTA, 0  <BR>
&emsp;	RCALL Delay_0_5ms  <BR>
**RJMP MAIN** <BR>

**Delay_0_5ms:**  <BR>
&emsp;	LDI R16, 10  <BR>
L2: LDI R17, 100  <BR>
L1: DEC R17  <BR>
&emsp;  	NOP  <BR>
&emsp;	BRNE L1  <BR>
&emsp;	DEC R16  <BR>
&emsp;	BRNE L2  <BR> 
&emsp;	RET  <BR>
<img width="1380" height="882" alt="image" src="https://github.com/user-attachments/assets/4e2a95b7-cc91-4d0f-aefc-44b0be58b9a7" />  <BR>

**subprogram Delay_1ms:** <BR>
&emsp;	LDI R18, 2  <BR>
L3: RCALL Delay_0_5ms <BR>
&emsp;	DEC R18 <BR>
&emsp;	BRNE L3 <BR>
&emsp;	RET <BR>
**subprogram Delay_10ms:**
&emsp;	LDI R19, 10  <BR>
L4: RCALL Delay_1ms <BR>
&emsp;	DEC R19 <BR>
&emsp;	BRNE L4 <BR>
&emsp;	RET <BR>
**subprogram Delay_100ms:**
&emsp;	LDI R20, 10  <BR>
L5: RCALL Delay_10ms <BR>
&emsp;	DEC R20 <BR>
&emsp;	BRNE L5 <BR>
&emsp;	RET <BR>
**subprogram Delay_1s:**
&emsp;	LDI R21, 10  <BR>
L6: RCALL Delay_100ms <BR>
&emsp;	DEC R21 <BR>
&emsp;	BRNE L6 <BR>
&emsp;	RET <BR>
**A program that blinks an LED connected to PA0: (use Delay_1s)**  
.ORG 0 
SET_UP:
	SBI DDRA, 0
MAIN:	
	SBI PORTA, 0
	RCALL Delay_1s
	CBI PORTA, 0
	RCALL Delay_1s
	RJMP MAIN

Delay_1s:
	LDI R16, 80
L1:	LDI R17, 100
L2: LDI R18, 250
L3: DEC R18
  	NOP 
	BRNE L3
	DEC R17
	BRNE L2
	DEC R16
	BRNE L1
	RET





