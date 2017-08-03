# SENZ005 数字震动传感器

###### 翻译

> `英文`请参考 [`这里`](https://github.com/FizzyStudio/SENZ005-Digital-Vibration-Sensor/blob/master/README.md).

> `中文`请参考 [`这里`](https://github.com/FizzyStudio/SENZ005-Digital-Vibration-Sensor/blob/master/README_CN.md).

![](https://github.com/FizzyStudio/SENZ005-Digital-Vibration-Sensor/blob/master/pic/SENZ005.jpg "SENZ005") 

### 产品介绍

> SENZ005数字震动传感器是一个数字的即插即用传感器模块。它可以检测到震动信号，然后输出开关信号到Arduino，
> 模块使用PH2.0接口，使用数字连接线可以很方便的连接到传感器扩展板上。
> 它能够感知微弱震动信号，可实现与震动有关的互动作品。

### 产品参数

* 在外力震动时，达到适当的震动力时导电针将瞬间开启（ON）。
* 无方向，任何角度可能检测震动。
* 适用于小电流电路（二次回路）或触发（IC）。
* 在室温和正常使用情况下的开关使用寿命可达10万次（times/1sec）。
* 供电电压：和所用控制器一致即可。
* 开启时间：0.1ms（建议使用中断捕捉）
* 开路电阻：10Mohm
* 平时保持高电平输出，震动时输出低电平

### 使用教程

#### 连线图

![](https://github.com/FizzyStudio/SENZ005-Digital-Vibration-Sensor/blob/master/pic/SENZ005_2.png "连线图") 

### 示例代码

    #define SensorLED     13
    #define SensorINPUT   3  //Connect the sensor to digital Pin 3 which is Interrupts 1.
    
    unsigned char state = 0;
    
    void setup() 
    { 
      pinMode(SensorLED, OUTPUT); 
      pinMode(SensorINPUT, INPUT);
      attachInterrupt(1, blink, FALLING);// Trigger the blink function when the falling edge is detected
    
    }
    void loop()
    {
          if(state!=0)
          {
            state = 0;
            digitalWrite(SensorLED,HIGH);
            delay(500);
          }  
          else 
            digitalWrite(SensorLED,LOW);
    } 
    
    
    void blink()//Interrupts function
    {
      state++;
    }

#### 结果

> 如图连线，插上LED小灯后，每次振动数字震动传感器，小灯都会短暂点亮，具体点亮时间可在代码中设置

### 更多