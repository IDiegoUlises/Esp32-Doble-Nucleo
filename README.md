# Esp32-Doble-Nucleo

### Codigo Para Conocer Que Nucleo Se Esta Utilizando
```c++
void setup()
{
  //Inicia el puerto serial
  Serial.begin(9600);

  Serial.print("Setup() se corre en el nucleo");
  Serial.println(xPortGetCoreID());

}

void loop()
{
  Serial.print("Loop() se corre en el nucleo");
  Serial.println(xPortGetCoreID());
  delay(1000); //Un retardo para llenar el puerto serial
}
```
