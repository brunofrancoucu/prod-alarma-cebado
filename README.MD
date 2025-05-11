# Ruteo de alta frecuencia con coupling a GND Y PWR
Par diferencial de alta frecuencia por multiples capas, respetando la impedancia el return path sera por PWR (debido a stack up intermedio de GND PWR y no GND GND), por ello utilizar capacitor en puntos de entrada (source) y salida (exit) (split boundary)

[<img alt="Stitching Capacitor" width="40px" src="images/image.PNG" />](https://www.protoexpress.com/blog/wp-content/uploads/2020/11/stitching-cap.png)

## Stitching capacitor:
[ref1](https://www.asset-intertech.com/wp-content/uploads/2020/05/6a01348365b3a6970c01b8d06c22f7970c-pi.jpg), [ref2](https://www.protoexpress.com/blog/wp-content/uploads/2020/05/28.png)
Valores normales para el stitching capacitor ronda los, 10nF and 100nF (src)[https://www.protoexpress.com/blog/best-high-speed-pcb-routing-practices/]
Evitar: "If that plane is cut, the return current must detour—often radiating or coupling into other nets—and you’ll get reflections, EMI, and extra crosstalk" - gpt

# Calculos:
## Par diferencial:
[screenshot]
Z0: 90ohms +-15%
w: εᵣ 4.6 7628 prepreg FR-4 glass-epoxy laminate [ref](https://jlcpcb.com/capabilities/pcb-capabilities)
h: 0.2mm
Ancho pista: 0.202 mm - separacion pista recomendada: 0.062 mm, maxima: 0.329 mm

## Stitching capacitor, "capacitancia ideal":
Frequencia usb 3.0: 2.5 Ghz (medible con el "rise time" de la señal), entonces, para un Zdiff de 90 ohmios el Zbridge resulta 9 ohmios, capacitancia minima: 7.1 pF
- 100 nF 0402 or 0201	for low-frequency return (10 kHz – 100 MHz)	
- 1 nF 0201	covers 100 MHz – 1 GHz
- 100 pF 0201	covers 1 GHz – 3.5+ GHz (✔️ Recomendable)

Nos aseguramos: effective throughput (bit errors), calidad de señal compliance al USB.

# Complemento

## Recomendacion (plano de referencia limpio): SIG, GND, GND, (SIG + PWR)
Objetivo / desafio: mantener bajo cross talk con un coupling corto / cercano (usando PWR como plano de referencia)

## Otras alternativas:
- GND temporal en PWR (capa 3), justo arriba de par diferencial en la 4ta capa (SIG).
- Rutearlo por arriba.
