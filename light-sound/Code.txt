#define sensor 11
#define led 2
boolean val=1;
boolean ledstatus=0;
void setup() {
pinMode(led,OUTPUT);
pinMode(sensor,INPUT);
Serial.begin(9600);
}
void loop() {
Serial.println(digitalRead(sensor));
while (ledstatus==0) {
val=digitalRead(sensor);
if (val==0) {
ledstatus=1;
digitalWrite(led,ledstatus);
delay(80);
break;
}
}
while (ledstatus==1) {
val=digitalRead(sensor);
if (val==0) {
ledstatus=0;
digitalWrite(led,ledstatus);
delay(80);
break;
}
}
}
