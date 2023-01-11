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
* Este microcontrolador tiene dos nucleos por lo cual se pueden hacer dos procesos al mismo tiempo

## Codigo para utilizar el doble nucleo
```c++
TaskHandle_t Tarea1; //Objeto

void setup()
{
  //Inicia el puerto serial
  Serial.begin(9600);

  xTaskCreatePinnedToCore(
    funcion, //Nombre de la funcion
    "Tarea1", //Nombre de la tarea
    10000,  //Tamaño de la pila
    NULL,  // Parametros de entrada
    0,  //Prioridad de la tarea
    &Tarea1,  //Objeto TaskHandle_t
    0); // Nucleo donde se correra

}

void loop()
{
  Serial.print("Se esta ejecutando en el nucleo: ");
  Serial.println(xPortGetCoreID());
  delay(2000); //Para no llenar el puerto serial
}

//Esta funcion es la que se ejecutara en el segundo nucleo
void funcion(void * pvParameters)
{
  while (true) //Se utiliza un while para se ejecute siempre
  {
    Serial.print("Se esta ejecutando en el nucleo: ");
    Serial.println(xPortGetCoreID());
    delay(1000); //Para no llenar el puerto serial
  }
}
```

## Debug
<img  src="https://github.com/IDiegoUlises/Esp32-Doble-Nucleo/blob/main/Images/Debug.png">
