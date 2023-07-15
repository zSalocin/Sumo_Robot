#define BorderSensor_1 3
#define BorderSensor_2 4
#define BorderSensor_3 5
#define BorderSensor_4 6
#define SensorPrincipal_Ult 7
#define Motor_1 8
#define Motor_2 9
#define Start 10

void setup(){
    serial.Begin(9600);
    pinMode(Start, INPUT)
    pinMode(BorderSensor_1, INPUT);
    pinMode(BorderSensor_2, INPUT);
    pinMode(BorderSensor_3, INPUT);
    pinMode(BorderSensor_4, INPUT);
    pinMode(SensorPrincipal_Ult, INPUT);
    pinMode(Motor_1, OUTPUT);
    pinMode(Motor_2, OUTPUT);
}

void girar(){
    //TODO função de girar
}

void loop(){
    do{
        analogWrite(Motor_1, 0);
        analogWrite(Motor_2, 0);
    }while(digitalRead(Start));

    if(digitalRead(BorderSensor_1)){}
    if(digitalRead(BorderSensor_2)){}
    if(digitalRead(BorderSensor_3)){}
    if(digitalRead(BorderSensor_4)){}

    if(analogRead(SensorPrincipal_Ult)<=???){
        //TODO ataque frontal
    }elif(){
        //TODO ataque lateral
    }elif{
        //TODO ataque traseiro
    }else{
        //TODO busca
    }
}