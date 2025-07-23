# Dudas
## Que pasa si una corriente de PWR pasa por el mismo lugar del coupling de HF en PWR?
"The stitching capacitor gives the high-frequency return current a tiny, low-inductance bridge to ground while remaining invisible to the DC and low-frequency load currents on the power plane. Both currents can coexist on the same copper without interfering, provided you keep the plane wide and the decoupling network healthy"
superimpose - no problema, diferentes frequencias

## Como fluye la corriente de retorno si el capacitor bloquea DC?
appears as one continuous copper sheet plane
It’s not for power—it’s for fields
small capacitor’s reactance - planes shorted together
Because the capacitor sits directly beneath the pair and is very low-inductance, the loop area stays tiny and the differential-pair sees a continuous impedance environment.

source: https://www.protoexpress.com/blog/best-high-speed-pcb-routing-practices/

## Averiguar si podemos uasr un capacitor (menor inductancia) 0402 o ... 0201 (actual: protoexpress, 100nF)
"The best high-speed performances are usually accomplished if the component’s width is close to the track width. This will lower the impedance matching issues between the track and the component pad."
- protoexpress (11. Choose ...)
ideal: 100pF 0201

The differential pair itself doesn't require a ground, as it relies on the signal difference between the two traces, not a shared reference to ground. howeber
