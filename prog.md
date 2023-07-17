#include "Ultrasonic.h"

#define BorderSensor_1 3
#define BorderSensor_2 4
#define BorderSensor_3 5
#define BorderSensor_4 6
#define UltrasonicSensor_echo 7
#define UltrasonicSensor_trigger 8
#define Motor_1_1 9
#define Motor_1_2 10
#define Motor_2_1 11
#define Motor_2_2 12
#define Start 13
#define Radius 30

Ultrasonic ultasonic(trigPin, echoPin);//Remover junto com a biblioteca e implementar se possivel, para tornar mas rapido

void setup(){
    Serial.begin(9600);
    pinMode(Start, INPUT);
    pinMode(BorderSensor_1, INPUT);
    pinMode(BorderSensor_2, INPUT);
    pinMode(BorderSensor_3, INPUT);
    pinMode(BorderSensor_4, INPUT);
    pinMode(UltrasonicSensor_echo, INPUT);
    pinMode(UltrasonicSensor_trigger, OUTPUT);
    pinMode(Motor_1_1, OUTPUT);
    pinMode(Motor_1_2, OUTPUT);
    pinMode(Motor_2_1, OUTPUT);
    pinMode(Motor_2_2, OUTPUT);
}

void motorControl(bool n,bool a, bool b){//Motor n sendo 1 motor 2, 0 motor 1 e o input 1 e 2 da ponte H respectivamente
    if(n){
        if(a)
            digitalWrite(Motor_2_1, 1);
        else
            digitalWrite(Motor_2_1, 0);
        if(b)
            digitalWrite(Motor_2_2, 1);
        else
            digitalWrite(Motor_2_2, 0);
    }else{
                if(a)
            digitalWrite(Motor_1_1, 1);
        else
            digitalWrite(Motor_1_1, 0);
        if(b)
            digitalWrite(Motor_1_2, 1);
        else
            digitalWrite(Motor_1_2, 0);
    }
}

int ultrasonicSensor(){
    digitalWrite(UltrasonicSensor_trigger, 0);
    delayMicroseconds(2);
    digitalWrite(UltrasonicSensor_trigger, 1);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);
    return ultrasonic.Ranging(CM);//Remover junto com a biblioteca e implementar se possivel, para tornar mas rapido
}

void fieldLimit(){
     //TODO
}

int locateTarget(){
    //TODO
}//Localizar inimigo, necessario dados sobre o giroscopio

int debugMode(){
    //TODO
}

void loop(){
//TODO
}