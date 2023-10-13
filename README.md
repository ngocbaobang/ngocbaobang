- 👋 Hi, I’m @ngocbaobang
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
ngocbaobang/ngocbaobang is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
---># Import các thư viện cần thiết
import RPi.GPIO as GPIO
import time

# Thiết lập chế độ chân GPIO
GPIO.setmode(GPIO.BOARD)

# Định nghĩa các chân GPIO cho điều khiển motor
motor1_pin1 = 11
motor1_pin2 = 12

# Thiết lập chân GPIO là OUTPUT
GPIO.setup(motor1_pin1, GPIO.OUT)
GPIO.setup(motor1_pin2, GPIO.OUT)

def forward():
    # Điều khiển motor di chuyển tiến về phía trước
    GPIO.output(motor1_pin1, True)
    GPIO.output(motor1_pin2, False)

def stop():
    # Dừng motor lại
    GPIO.output(motor1_pin1, False)
    GPIO.output(motor1_pin2, False)

try:
    while True:
        forward()  # Di chuyển tiến về phía trước trong khoảng thời gian nhất định (có thể thay đổi giá trị time.sleep())
        time.sleep(5)  # Thời gian di chuyển tiến về phía trước (5 giây)
        stop()     # Dừng lại trong khoảng thời gian nhất định (có thể thay đổi giá trị time.sleep())
        time.sleep(2)  # Thời gian dừng lại (2 giây)

except KeyboardInterrupt:
    GPIO.cleanup()
    
