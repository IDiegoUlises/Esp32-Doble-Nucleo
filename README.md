# Esp32-Doble-Nucleo

### Codigo para conocer que nucleo se esta utilizando
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
  delay(1000); //Un retardo para no llenar el puerto serial
}
```

* La funcion ```void setup()``` y ```void loop()``` utilizan el nucleo 1
* La funcion ```xPortGetCoreID()``` se utiliza para conocer que nucleo se esta utilizando
* El Esp32 tiene dos nucleo es decir que se pueden hacer dos activades al mismo tiempo

