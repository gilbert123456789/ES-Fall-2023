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

### 電路 ＆ Demo

<img width="1440" alt="截圖 2023-12-18 上午11 06 50" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/44418a86-fbef-4ae2-9f81-93b1998ed77e">

https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/66c6b0ff-3ee3-46d6-be5f-f345ae393938

### 程式

'''c
//
/*
int R = 9;
int G = 10;
int B = 11;

int DR = 2;
int DG = 4;
int DB = 7;

void setup()
{
  pinMode(13, OUTPUT); // pin 13
  
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
  
  pinMode(DR, OUTPUT);
  pinMode(DG, OUTPUT);
  pinMode(DB, OUTPUT);   
}

void loop()
{
  // digitalWrite: 2 state (i.e., 0, 1) Only
  digitalWrite(13, 1); // LED @ pin 13, ON
  
  delay(1000); 
  
  digitalWrite(DR, 1);
  digitalWrite(DG, 0);
  digitalWrite(DB, 0);
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 1);
  digitalWrite(DB, 0);  
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 0);
  digitalWrite(DB, 1);  
  delay(1000);

  digitalWrite(13, 0); // OFF
  digitalWrite(DR, 0); // OFF
  digitalWrite(DG, 0); // OFF
  digitalWrite(DB, 0); // OFF  
  delay(1000);
  
  // analogWrite: The brightness can be adjusted with 256 levels
  for (int i = 0; i<= 255; i++)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10);
  } // from dark to bright 

  for (int i = 255; i>= 0; i--)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10); // 10ms = 0.01s
  }  // from bright to dark
  delay(1000);
}

'''









