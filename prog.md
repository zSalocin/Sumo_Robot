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
#define min_Distance 10
#define max_Distance 50

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
    delayMicroseconds(10);
    digitalWrite(UltrasonicSensor_trigger, 0);
    return pulseIn(UltrasonicSensor_echo, 1)/29 / 2 ;
}

void fieldLimit(){
    if(digitalRead(BorderSensor_1)){}//direita frente
    if(digitalRead(BorderSensor_2)){}//esquerda frene
    if(digitalRead(BorderSensor_3)){}//direitra traseira
    if(digitalRead(BorderSensor_4)){}//esquerda traseira
}

int locateTarget(){
    int distance = ultrasonicSensor();
    if(distance <= max_Distance)
        return distance;
    else{
        //girar 30 para um lado depois para o outro, ver giroscopio para implementar
    }
}//Localizar inimigo, necessario dados sobre o giroscopio

int debugMode(){
    if(ultrasonicSensor()!=0)
        Serial.println("Ultrasonic_Sensor: OK");
        Serial.println("Start Motors Test");
        Serial.println("Try to go forward");
        motorControl(1,0,1);
        motorControl(0,0,1);
        delay(2000);
        Serial.println("Try to go backward");
        motorControl(1,1,0);
        motorControl(0,1,0);
        delay(2000);
        Serial.println("Try to turn right");
        motorControl(1,0,1);
        motorControl(0,1,0);
        delay(2000);
        Serial.println("Try to turn left");
        motorControl(1,1,0);
        motorControl(0,0,1);
        delay(2000);
        Serial.println("Try to shutdown the motors");
        motorControl(1,0,0);
        motorControl(0,0,0);
}

void atk_1(){}

void atk_2(){}

void atk_3(){}

void loop(){
debugMode();
}