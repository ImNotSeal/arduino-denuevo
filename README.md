const int leds[] = {2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13};
const int cantidadLeds = sizeof(leds) / sizeof(leds[0]);


int tiempo = 300;      
const int tiempoMin = 40;  
const int tiempoMax = 300;
const int cambio = 10;     

void setup() {
  for (int i = 0; i < cantidadLeds; i++) {
    pinMode(leds[i], OUTPUT);
  }
}

void loop() {

  for (int i = 0; i < cantidadLeds; i++) {
    digitalWrite(leds[i], HIGH);
    delay(tiempo);
    digitalWrite(leds[i], LOW);

    tiempo -= cambio;

    if (tiempo < tiempoMin) {
      tiempo = tiempoMin;
    }

    delay(tiempo);
  }

  for (int i = cantidadLeds - 2; i >= 0; i--) {
    digitalWrite(leds[i], HIGH);
    delay(tiempo);
    digitalWrite(leds[i], LOW);

    tiempo += cambio;

    if (tiempo > tiempoMax) {
      tiempo = tiempoMax;
    }

    delay(tiempo);
  }
}
