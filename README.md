# IOT_MOVECAR
## 1.關於專案
原本是想作能夠辨識交通號誌的自走車，但由於種種原因只有讓它可以依照指令進行動作
## 2.專案構想
輸入指令後，車輛會依指令發動相對應的馬達並因此轉動輪子
## 3.所需材料
* Rasberry Pi 3 X1
* Raspberry Pi 樹莓派UPS 鋰電池擴充板USB 電源供應模組行動電源 X1
* L298N馬達驅動模組 X1
* 四顆並聯電池座(包含正負極單芯線) X1
* 1.5v電池 X4
* 8條單芯線 (目的:連接直流減速電機馬達與L298N)
* 四條母對母杜邦線 (目的:連接Rasberry Pi與L298N,傳達指令)
* 一條公對母杜邦線 (目的:連接Rasberry Pi與L298N,輸入5V電壓)
* Micro USB傳輸線 (目的:連接Rasberry Pi與鋰電池擴充板)
* 四個直流減速電機
* 一套雙層四驅自走車底盤(包含四顆輪胎)
* 筆電
## 4.線路設計
![GITHUB](https://github.com/frest03087/IOT_MOVECAR/blob/main/FourWheelCar.png "FourWheelCar.png")
## 5.程式設計
main.py
```python
import RPi.GPIO as GPIO
import sys
 
GPIO.setmode(GPIO.BOARD)
GPIO.setwarnings(False)
GPIO.setup(31, GPIO.OUT)
GPIO.setup(33, GPIO.OUT)
GPIO.setup(35, GPIO.OUT)
GPIO.setup(37, GPIO.OUT)
 
if len(sys.argv)<=1:
    cmd = 'stop'
else:
    cmd = sys.argv[1]
 
print(cmd)
 
if cmd == 'F':
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.HIGH)
    GPIO.output(35, GPIO.HIGH)
    GPIO.output(37, GPIO.LOW)
elif cmd == 'B':
    GPIO.output(31, GPIO.HIGH)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.HIGH)
elif cmd == 'L':
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.HIGH)
    GPIO.output(37, GPIO.LOW)
elif cmd == 'R':
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.HIGH)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.LOW)
elif cmd == 'BL':
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.HIGH)
elif cmd == 'BR':
    GPIO.output(31, GPIO.HIGH)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.LOW)
elif cmd == 'S':
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.LOW)
else:
    GPIO.output(31, GPIO.LOW)
    GPIO.output(33, GPIO.LOW)
    GPIO.output(35, GPIO.LOW)
    GPIO.output(37, GPIO.LOW)
```
## 6.影片
* https://www.youtube.com/watch?v=1L7Kd24zTDM
## 7.參考資料
* https://github.com/ponponmusic/IOT-Project-_-FourWheelCar-ImageRecognize
* http://hophd.com/raspberry-pi-remote-car-program/
