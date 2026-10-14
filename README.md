# Epiciclos de Fourier — laboratorio interactivo

Visualizador de **series de Fourier con epiciclos** en un solo archivo HTML: sin
dependencias, sin build y sin servidor. Se abre con doble clic o desde cualquier
navegador, también en el celular.

Dibuja cada figura con círculos que giran a frecuencia entera *n*; la suma de sus
vectores traza la curva. Los coeficientes **no están precalculados**: el navegador
calcula la DFT de la figura y anima sus armónicos.

## Uso

- Abra `index.html` (o visite la versión publicada) y presione **Reproducir**.
- **M (número de epiciclos)**: con pocos armónicos se ve el boceto; al subir *M*
  la curva converge a la figura. Los atajos 6 / 12 / 40 / 120 muestran esa
  progresión, y **Máx** reconstruye la figura de forma exacta.
- **Dibujar mi trazo**: trace cualquier curva con el ratón o el dedo y el
  laboratorio calcula sus epiciclos al soltar.
- Capas: círculos, vectores radiales, figura objetivo y plano complejo.
- Cámara: vista completa o seguimiento de la punta con acercamiento.
- Atajos de teclado: `espacio` pausa, `R` reinicia, `D` modo dibujo.

## La matemática que muestra

Con la curva muestreada en `N` puntos `p_k`, se calcula

```
c_n = (1/N) · Σ_k  p_k · e^(−2πi n k / N),      n = −N/2 … N/2−1
```

y la suma parcial `f(t) = Σ c_n · e^(i n t)` con los `M` armónicos de mayor radio
es la curva reconstruida. El panel informa:

- **Energía (Parseval)**: `Σ|c_n|²` de los armónicos activos sobre el total.
- **Error de la suma parcial**: distancia media en píxeles entre la figura y su
  reconstrucción con `M` armónicos. Al crecer `M` el error baja: es la
  convergencia de la serie de Fourier, medida en vivo.
- **Armónicos principales**: frecuencia `n`, radio `|c_n|` y fase `φ_n`.

Figs. incluidas: pelícano en bicicleta, bicicleta, corazón, estrella, infinito,
cardioide, rosa de 5 pétalos y cuadrado redondeado. Las figuras con esquinas
necesitan más armónicos que las suaves: comparar unas con otras es parte del
ejercicio.

## Uso local

```bash
git clone https://github.com/darwindacier/epiciclos-fourier.git
# abra index.html en el navegador (o sirva la carpeta con: python -m http.server)
```

## Créditos

Recreación interactiva inspirada en los clásicos demos de "dibujar con la
transformada de Fourier" (epiciclos). La implementación, las figuras y el cálculo
de DFT, energía y error son propios de este repositorio.

## Licencia

MIT — véase [LICENSE](LICENSE).
