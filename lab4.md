# ES2022 - 實作4: 七段顯示器, LCD 顯示器 + 超音波感測器

## 目錄 （Table of Contents)

[Lab 4-1 用七段顯示器來顯示數字"8."](#111)

[Lab 4-2 如下圖的Demo, 用七段顯示器, 顯示 . →1→ ... → 9 → 0 → 全滅, 狀態改變的間隔時間為0.5秒](#222)

[Lab 4-3 LCD顯示"Hello" + 你的英文名字 (e.g., "Hello Horace")](#333)

[## Lab 4-4 整合超音波感測器 + LCD + LED](#444)

## 4-1 用七段顯示器來顯示數字"8."

### 電路 ＆ Demo

<img width="1440" alt="截圖 2023-12-18 下午3 10 36" src="https://github.com/gilbert123456789/ES-Fall-2023/assets/144580521/913e2b0d-c3a2-45ed-9b06-b30b4aad12cd">

### 程式

````C
void setup()
{
for(int x = 1; x < 9; x++) {
pinMode(x,OUTPUT);
}
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
digitalWrite(1, a);
digitalWrite(2, b);
digitalWrite(3, c);
digitalWrite(4, d);
digitalWrite(5, e);
digitalWrite(6, f);
digitalWrite(7, g);
digitalWrite(8, h);
delay(500);
}

void loop()
{
//    a, b, c, d, e, f, g, h
seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
}
````






















