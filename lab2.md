# 實作2: 會呼吸的RGB LED,  按鍵控制, 狀態輸出 (2W)

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (1W: ~ 01:45pm)

### 電路 ＆ Demo

![image](https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/e252807c-8fc3-48b9-b576-84839768a8e1)


https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/6e775db6-7321-4644-ad6a-7d7648d9253e

### 程式

```C
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

```

## 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性?

### 電路 & Demo

<img width="1440" alt="截圖 2023-12-18 上午10 23 52" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/e3eedff4-d69e-4f47-91d9-0507f36ccf76">

https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/6588ea82-cb08-4ab4-bab5-343b9e6cdf21

### 程式

```C
//
/*
  This program blinks pin 13 of the Arduino (the
  built-in LED)
*/

const int Red = 9;
const int Green = 10;
const int Blue = 11;

void setup()
{
  pinMode(Red, OUTPUT);
  pinMode(Green, OUTPUT);
  pinMode(Blue, OUTPUT);
}

void loop()
{
  // turn the LED on (HIGH is the voltage level)
  analogWrite(Red, 255);
  analogWrite(Green, 0);
  analogWrite(Blue, 0);
  delay(1000); // Wait for 1000 millisecond(s)
  
  analogWrite(Red, 0);
  analogWrite(Green, 255);
  analogWrite(Blue, 0);
  delay(1000); // Wait for 1000 millisecond(s)
  
  analogWrite(Red, 0);
  analogWrite(Green, 0);
  analogWrite(Blue, 255);
  delay(1000); // Wait for 1000 millisecond(s)  
}

```

## 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性?

## 電路 ＆ Demo

