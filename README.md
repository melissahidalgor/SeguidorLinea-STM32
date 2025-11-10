# 🚗 Proyecto: Carrito Seguidor de Línea con Lógica Difusa (Fuzzy Logic)
## Resumen del Proyecto

Este proyecto consiste en el diseño e implementación de un carrito móvil capaz de seguir una línea negra utilizando un sistema de control basado en Lógica Difusa (Fuzzy Logic).

La Lógica Difusa permite que el carrito tome decisiones adaptativas y fluidas al modificar la velocidad de sus motores en función de la intensidad de la línea detectada por los sensores. Esto resulta en un control más robusto y efectivo para sistemas inherentemente no lineales.

## 💻 Hardware y Componentes

| Componente | Conexión/ Tecnología| Función Principal |
| :--- | :---: | :--- |
| **STM32F411 BlackPill** | Microcontrolador | Utilizado por su capacidad de procesamiento con punto flotante |
| **TCRT5000** | ADC1 (Canales 4, 5, y 6) | Sensor de línea, detectan la intensidad de la luz infrarroja reflejada por la línea |
| **TB6612FNG** | GPIO/PWM | Puente H que maneja la potencia y dirección de los motores DC |

## ⚙️ Implementación de Lógica Difusa

1. **Fuzzificación (Entradas ADC):** Se calcula el grado de pertenencia (*Dentro o Fuera*) de cada entrada del sensor (*Izquierdo, Centro, Derecho*) mediante el uso de funciones de membresía (*Funciones Triangulares*).

2.  **Inferencias (Reglas Lógicas):** Se establecieron reglas simplificadas basadas en que solo un sensor a la vez debería detectar la línea dado el grosor de la línea y la separación entre sensores.

| Condición |Salida (Control de Motores) | 
| :--- | :---: | 
| Sensor Izquierdo Dentro| Motor Izquierdo (Baja) / Motor Derecho (Alta) -Giro Derecha |
| Sensor Centro Dentro| Motor Izquierdo (Media) / Motor Derecho (Media) -Avanzar Recto |
| Sensor Derecho Dentro| Motor Izquierdo (Alta) / Motor Derecho (Baja) - Giro a la Izquierda |

3. **Defuzzificación (Salidas PWM):** Se utiliza el centroide para convertir la salida difusa (Baja, Media, Alta) en un valor numérico de PWM (0 a 800).

## 🎥 Video 
[https://drive.google.com/file/d/1-XZC_Tf9S0zmL3UJ1JFDIxQtHfUZZFCX/view?usp=sharing](https://drive.google.com/file/d/1-XZC_Tf9S0zmL3UJ1JFDIxQtHfUZZFCX/view?usp=sharing)

[https://drive.google.com/file/d/1YVrNEFv-BSSDAJJgz_M3N77wPq2cuvl0/view?usp=sharing](https://drive.google.com/file/d/1YVrNEFv-BSSDAJJgz_M3N77wPq2cuvl0/view?usp=sharing)

## 🖼️ Montaje

![Texto alternativo](Documentacion/CarritoLinea.png)
