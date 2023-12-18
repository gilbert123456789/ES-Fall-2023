# 實作3: 使用超音波感測器 + LED控制, C語言程式速成

## Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output

### 電路 ＆Demo

<img width="1440" alt="截圖 2023-12-18 下午12 01 59" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/074c7a0a-72cf-40cb-8af8-024d43c88b3e">

https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/ebf84271-1da9-4136-ae96-44a517d33749

## 3-2: 超音波感測器 + LED (紅色LED:亮<70cm, 藍色LED: 亮>270cm, 緑色LED:亮, 介於70cm ~ 270cm之間) + RS232 Output

## 電路 ＆ Demo

<img width="1440" alt="截圖 2023-12-18 下午12 19 26" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/9af8c925-014c-444b-8e64-8d1bc00d223a">

https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/46703679-f858-4120-a61e-c7f38bdbfa37

### 程式

int inches = 0;
int GLED = 8;
int RLED = 12;
int BLED = 10;
int cm = 0;

void LED(int RH, int GH, int BH)
{
  digitalWrite(RLED, RH);  
  digitalWrite(GLED, GH);
  digitalWrite(BLED, BH);   
}

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);
  digitalWrite(GLED, OUTPUT);
  digitalWrite(RLED, OUTPUT);  
  digitalWrite(BLED, OUTPUT);    
  
}

void loop()
{
  // measure the ping time in cm
  cm = 0.01723 * readUltrasonicDistance(7, 7);
  // convert to inches by dividing by 2.54
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  
  if(cm<70){
    LED(1, 0, 0); //int RH, int GH, int BH    
  }
  else if(cm>270){
    LED(0, 0, 1); //int RH, int GH, int BH      
  }
  else{
    LED(0, 1, 0); //int RH, int GH, int BH      
  }
    
  Serial.println("cm");
  delay(100); // Wait for 100 millisecond(s)
   
}

## 3-3: Arduino常用的C語言程式介紹與實作

### 電路 ＆ Demo

<img width="1440" alt="截圖 2023-12-18 下午12 28 16" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/02b8de52-2c83-43a9-b888-370d589b7d8b">

https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/29d5320a-0a25-4d20-a69d-b650147de9d2

### 程式

/*
 Lab 3-3, Embedded System, VNU
 Date: 2021/09/26
*/
int RLED = 13;
int GLED = 11;


int result, result2, result3;
String d0 = "****** 9X9 Table ******";
String d1, d2, d3;
void setup()
{
  pinMode(RLED, OUTPUT);   // Configure PIN13
  pinMode(GLED, OUTPUT);   // Configure PIN11
  
  Serial.begin(9600);

}

void loop()
{
  int aa = 0;

  Serial.println(d0); 
  
  digitalWrite(RLED, HIGH);
  analogWrite(GLED, aa); 
  
  for (int i=1;i<=9; i=i+3){
    for (int j=1;j<=9; j++){
      
      result = i*j;
      result2 = (i+1)*j;
      result3 = (i+2)*j;
      
      d1 = String(String(i) + "X" + String(j) + "=" + String(result));

     /*
       待完成
     */
      
      Serial.println(d1 + ", " + d2 + ", " + d3);
    
      aa+=1;
      
      delay(100);
    } // loop j
    analogWrite(GLED, aa*3); 
    Serial.println("");
  } // loop i

  digitalWrite(RLED, LOW);
  analogWrite(GLED, 255); 
  delay(2000);	
  analogWrite(GLED, 0);
}







