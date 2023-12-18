# 實作2: 會呼吸的RGB LED,  按鍵控制, 狀態輸出 (2W)

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (1W: ~ 01:45pm)

### 電路 ＆ Demo

![image](https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/e252807c-8fc3-48b9-b576-84839768a8e1)


https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/6e775db6-7321-4644-ad6a-7d7648d9253e

### 程式
int brightness = 0;

void setup()
{
  pinMode(9, OUTPUT);
}

void loop()
{
  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(9, brightness);
    delay(30); // Wait for 30 millisecond(s)
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(9, brightness);
    delay(30); // Wait for 30 millisecond(s)
  }
}

