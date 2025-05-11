ruteo de alta frecuencia con coupling a GND Y PWR
par diferencial de alta frecuencia por multiples capas 
respetando la impedancia el return path sera por PWR (debido a stack up de GND PWR y no GND GND)
por ello utilizar capacitor en puntos de entrada y salida (conectada a PWR y otro a GND) (split boundary)
ref: https://www.protoexpress.com/blog/wp-content/uploads/2020/11/stitching-cap.png

Stitching capacitor:
ref: https://www.asset-intertech.com/wp-content/uploads/2020/05/6a01348365b3a6970c01b8d06c22f7970c-pi.jpg
ref2: https://www.protoexpress.com/blog/wp-content/uploads/2020/05/28.png
"If that plane is cut, the return current must detour—often radiating or coupling into other nets—and you’ll get reflections, EMI, and extra crosstalk" - gpt
- small (e.g. 0.01–0.1 µF) ceramics right at the split edge
- values of stitching capacitors are between 10nF and 100nF
https://www.protoexpress.com/blog/best-high-speed-pcb-routing-practices/

# Calculos:
par diferencial w: screenshot:
[screenshot]
Z0: 90ohms +-15%
w: εᵣ 4.6 7628 prepreg FR-4 glass-epoxy laminate (ref: https://jlcpcb.com/capabilities/pcb-capabilities)
h: 0.2mm
ancho pista: 0.202 mm - separacion pista recomendada: 0.062 mm, maxima: 0.329 mm
nota: separacion maxima: , minima:

stitching capacitor, capacitancia ideal: 
frequencia usb 3.0: 2.5 Ghz (medible con el "rise time" de la señal)
entonces, para un Zdiff de 90 ohmios el Zbridge 9 ohmios, capacitancia minima: 7.1 pF
- 100 nF 0402 or 0201	for low-frequency return (10 kHz – 100 MHz)	
- 1 nF 0201	covers 100 MHz – 1 GHz
- 100 pF 0201	covers 1 GHz – 3.5+ GHz ✔️
self resonant frequency
asegura: 
Possible bit errors or retries (i.e., lower effective throughput)
Failure to meet USB signal quality compliance (e.g., eye diagram issues)
ref: impedancia vs frequency (gpt)

que pasa si una corriente de PWR pasa por el mismo lugar del coupling de HF en PWR?
"The stitching capacitor gives the high-frequency return current a tiny, low-inductance bridge to ground while remaining invisible to the DC and low-frequency load currents on the power plane. Both currents can coexist on the same copper without interfering, provided you keep the plane wide and the decoupling network healthy"
superimpose - no problema, diferentes frequencias

como fluye la corriente de retorno si el capacitor bloquea DC?
appears as one continuous copper sheet plane
It’s not for power—it’s for fields
small capacitor’s reactance - planes shorted together
Because the capacitor sits directly beneath the pair and is very low-inductance, the loop area stays tiny and the differential-pair sees a continuous impedance environment.

source: https://www.protoexpress.com/blog/best-high-speed-pcb-routing-practices/

Recomendacion (plano de referencia limpio): SIG GND GND SIG + PWR
porq no?
- mas interesante - desgaste de una capa (2 capas gnd... excesivo si es todo low frequency)
- permite usar componentes capa superior lo mas juntos posibles (menos espacio necesario)

objetivo / desafio: mantener bajo cross talk con un coupling corto / cercano (usar PWR 
como plano de referencia)

lo que yo hubiera echo:
GND temporal en PWR (capa 3), justo arriba de par diferencial en la 4ta capa (SIG)

TODO: 

mover pregunta al todo:

averiguar si podemos uasr un capacitor (menor inductancia) 0402 o ... 0201 (actual: protoexpress, 100nF)
"The best high-speed performances are usually accomplished if the component’s width is close to the track width. This will lower the impedance matching issues between the track and the component pad."
- protoexpress (11. Choose ...)
ideal: 100pF 0201

The differential pair itself doesn't require a ground, as it relies on the signal difference between the two traces, not a shared reference to ground. howeber

source copy save to folder clone
