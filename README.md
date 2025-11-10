# Desarrollo de un algoritmo de reducción de ruido en señales de voz utilizando Redes Generativas Antagónicas

**Tesis en curso para obtener el título de Ingeniero de Sonido de la Universidad Nacional de Tres de Febrero (UNTREF)**

---

En esta tesis de grado se propone, diseña, entrena y evalúa un **algoritmo de reducción de ruido en señales de voz** utilizando una **red generativa antagónica con discriminador métrico (MetricGAN)**. Para evaluar el desempeño del modelo y el impacto del diseño, se emplean **métricas objetivas** como **PESQ** y **STOI**, algunas de las cuales aproximan evaluaciones subjetivas de calidad perceptual. Los resultados se contrastan con **métodos tradicionales de procesamiento digital de señales (DSP)**, representando así un análisis comparativo entre paradigmas clásicos y de aprendizaje profundo.

---

### 🎯 Objetivo

Mejorar la calidad e inteligibilidad de señales de voz ruidosas estimando una **máscara espectral** que preserve el contenido vocal, utilizando reconstrucción de fase mediante **PGHI (Phase Gradient Heap Integration)** para minimizar artefactos.

---

### 🧠 Arquitectura

* **Generador:** R2AttU-Net (bloques recurrentes + atención) que produce máscaras en el dominio tiempo-frecuencia.
* **Discriminador (MetricGAN):** predice la calidad perceptual de la señal (PESQ normalizada) y guía al generador a optimizar directamente esa métrica.
* **Reconstrucción:** ISTFT basada en PGHI para mantener la coherencia temporal y de fase.

---

### ⚙️ Entrenamiento

* Dataset: **VoiceBank + DEMAND** (28 hablantes, ruidos reales)
* Configuración: `SR=16k`, `N_FFT=512`, `hop=64`, `batch=8`, `epochs=100`
* Pérdidas combinadas: L1 espectral, L1 temporal, IRM regularización y pérdida adversarial PESQ.

---

### 📊 Herramientas

* **PyTorch**, **pghipy**, **librosa**, **pesq**, **pystoi**
* Entrenamiento en **Google Colab (GPU Tesla T4)**
* Monitoreo con **TensorBoard**

---

**Autor:** Nicolás Racedo — Tesis de Ingeniería en Sonido y Acústica
