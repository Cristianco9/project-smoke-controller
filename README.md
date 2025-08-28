# IENSCH

---

# Detector de Humo con Micro:bit

Este proyecto es un **ejercicio educativo interactivo** diseñado para enseñar los 
fundamentos de la **programación con microcontroladores** utilizando la **BBC micro:bit**.  
Forma parte del **semillero tecnológico** y está orientado a estudiantes de grado 8° 
que desean aprender cómo los sensores pueden integrarse con la programación para 
resolver problemas de la vida real.

---

## 📌 Partes requeridas

- **BBC micro:bit**
  ![Micro:bit](images/microbit-bbc-v2.jpg)

- **Sensor de humo MQ-2**  
  ![Sensor MQ-2](images/sensor-mq-2.png)

- **Protoboard**  
  ![Protoboard](images/protoboard.png)

- **Jumpers (cables de conexión)**  
  ![Jumpers](images/jumpers.png)

- **Zumbador (buzzer)**  
  ![Buzzer](images/buzzer.png)

- **LED rojo (opcional)**  
  ![LED rojo](images/led-rojo.png)

  - **LED verde (opcional)**  
  ![LED rojo](images/led-verde.png)

- **Fuente de energía (USB o batería 5V)**  
  ![Fuente](images/cable-usb.png)

---

## 🎯 Funcionalidades principales

- 🔥 **Detección de humo/gas** mediante el sensor MQ-2.  
- 🚨 **Alarma sonora** con un buzzer al detectar humo.  
- 💡 **Indicador visual** en la matriz LED de la micro:bit y con LED externo (opcional).  
- 📊 **Lectura de valores analógicos** para calibrar la sensibilidad del sensor.  

---

## 🧪 ¿Qué aprenderán los estudiantes?

- Conectar y programar un **sensor externo** en la micro:bit.  
- Diferenciar entre **lectura digital (ON/OFF)** y **lectura analógica (valores continuos)**.  
- Usar **condicionales** para activar alarmas según un umbral definido.  
- Representar información en la **matriz LED** de la micro:bit.  
- La importancia de los **sensores en la seguridad** de hogares y espacios públicos.  

---

## ⚙️ ¿Cómo funciona?

1. El **sensor MQ-2** mide la concentración de humo o gas en el aire.  
2. La micro:bit lee el valor de salida del sensor.  
3. Si el valor es mayor al **umbral definido**:  
   - Se activa el buzzer con una alarma sonora.  
   - Se enciende el LED rojo (opcional).  
   - La micro:bit muestra un ícono de alerta 🚨 en su pantalla LED.  
4. Si no hay humo, el buzzer permanece apagado y se muestra un ícono de ✅ indicando seguridad.
   - Se enciende el LED verde (opcional).

---

## ⚠️ Advertencias

- El sensor MQ-2 **no entrega valores exactos**, solo indica una tendencia de concentración de humo/gas.  
- Para pruebas en clase, usar el **gas de un encendedor** (sin fuego), nunca acercar llamas directamente.  
- No usar este prototipo como sustituto de un **detector de humo certificado**.  
- Asegurarse de alimentar el sensor con el voltaje correcto (5V recomendado en la mayoría de módulos).  

---

## 🚀 Ideas para extender el ejercicio

- 📡 Enviar la señal de alarma a **otra micro:bit** mediante comunicación por radio.  
- 📲 Conectar la micro:bit a un teléfono móvil mediante **Bluetooth** para notificaciones.  
- 🔋 Implementar un sistema de **bajo consumo** con batería externa.  
- 🌎 Relacionar el proyecto con la importancia de la **prevención de incendios** en la vida real.  

---

## 👨🏻‍💻👩🏻‍💻 Desarrollo del proyecto

### Código en Bloques:
  ![Blocs](images/code.png)

### Código en JavaScript:
```JavaScript
let Gas = 0
pins.digitalWritePin(DigitalPin.P5, 0)
basic.forever(function on_forever() {
    
    Gas = pins.digitalReadPin(DigitalPin.P0)
    if (Gas == 0) {
        pins.digitalWritePin(DigitalPin.P7, 1)
        pins.digitalWritePin(DigitalPin.P5, 1)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P7, 0)
        pins.digitalWritePin(DigitalPin.P5, 0)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P6, 0)
        basic.showString("'Peligro Humo!'")
    } else {
        pins.digitalWritePin(DigitalPin.P7, 0)
        pins.digitalWritePin(DigitalPin.P5, 0)
        pins.digitalWritePin(DigitalPin.P6, 1)
        basic.showString("'Seguro!'")
    }
    
})
```

### Código en Python:
```Python
Gas = 0
pins.digital_write_pin(DigitalPin.P5, 0)

def on_forever():
    global Gas
    Gas = pins.digital_read_pin(DigitalPin.P0)
    if Gas == 0:
        pins.digital_write_pin(DigitalPin.P7, 1)
        pins.digital_write_pin(DigitalPin.P5, 1)
        basic.pause(500)
        pins.digital_write_pin(DigitalPin.P7, 0)
        pins.digital_write_pin(DigitalPin.P5, 0)
        basic.pause(500)
        pins.digital_write_pin(DigitalPin.P6, 0)
        basic.show_string("'Peligro Humo!'")
    else:
        pins.digital_write_pin(DigitalPin.P7, 0)
        pins.digital_write_pin(DigitalPin.P5, 0)
        pins.digital_write_pin(DigitalPin.P6, 1)
        basic.show_string("'Seguro!'")
basic.forever(on_forever)
```


---

## Licencia

Distribuido bajo la licencia MIT. Consulte la sección «LICENCIA» para más información.