bool start = 0;
void setup(){
    serial.Begin(9600);
    pinMode(BorderSensor_1, INPUT);
    pinMode(BorderSensor_2, INPUT);
    pinMode(BorderSensor_3, INPUT);
    pinMode(BorderSensor_4, INPUT);
    pinMode(SensorPrincipal_Ult, INPUT);
    pinMode(Motor_1, OUTPUT);
    pinMode(Motor_2, OUTPUT);
}

void loop(){
    do{
        analogWrite(Motor_1, 0);
        analogWrite(Motor_2, 0);
    }while(start == 0);

    if(digitalRead(BorderSensor_1)){}
    if(digitalRead(BorderSensor_2)){}
    if(digitalRead(BorderSensor_3)){}
    if(digitalRead(BorderSensor_4)){}

    if(analogRead(SensorPrincipal_Ult)<=???){
        
    }
}