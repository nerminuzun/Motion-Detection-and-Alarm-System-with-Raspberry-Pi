# Motion-Detection-and-Alarm-System-with-Raspberry-Pi

import time 
import RPi.GPIO as io 
io.setmode(io.BOARD) 

io.setup(18, io.IN) 
io.setup(16, io.OUT)
io.output(16, True)

def blink(pin):
    io.output(pin,io.HIGH)
    time.sleep(1)
    io.output(pin,io.LOW)
    time.sleep(1)
    return
io.setmode(io.BOARD)
io.setup(11,io.OUT)
io.setup(13,io.OUT)
print("Sensör Hazırlanıyor...")
time.sleep(1)
print("Çalışmaya Hazır")
while True: 
    if io.input(18):
        
        for i in range(0,4):
            blink(11)
        print("Hareket Algılandı")
        io.output(16, False)
        exec(open('buzzer_melody.py').read())
        time.sleep(1);
   
        for i in range(0,4):
            blink(13)
        print("Hareket Yok")
        io.output(16, True) 
        time.sleep(1)
    time.sleep(1)

#Buzzer "buzzer_melody.py" kodu

import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BOARD)
GPIO.setwarnings(False)
GPIO.setup(7, GPIO.OUT)

def play():
   GPIO.output(7,1)
   time.sleep(15)
   GPIO.output(7,0)
   time.sleep(1)

play()
