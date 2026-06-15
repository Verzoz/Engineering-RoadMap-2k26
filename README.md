# 🚀 Engineering Master Roadmap 2026

Questo repository funge da "Cervello" e diario di bordo (DevLog) per un percorso di ingegneria del software e dell'hardware. L'obiettivo finale è partire dalla programmazione desktop di alto livello per arrivare a padroneggiare la memoria, la fisica vettoriale, l'elettronica embedded e la teoria dei controlli di volo.

---

## 🗺️ Visione Generale del Progetto

Il percorso è diviso in 5 grandi moduli incrementali:
- **[IN CORSO] Fase 1:** Dashboard di Monitoraggio Hardware (C# / WPF)
- **[PIANIFICATA] Fase 2:** Motore Fisico 2D e Interazione Particellare (C / C++)
- **[PIANIFICATA] Fase 3:** Rover Autonomo e Telemetria (mCore / Arduino Uno)
- **[PIANIFICATA] Fase 4:** Simulatore di Volo 3D per Quadricottero con PID (C++ / OpenGL)
- **[PIANIFICATA] Fase 5:** Costruzione e Collaudo Drone Reale 

---

## 🔍 Zoom: Fase 1 - WPF Hardware Monitor

**Obiettivo:** Creare un'interfaccia desktop simil-Afterburner per leggere e tracciare le prestazioni di CPU e GPU, imparando a gestire architetture Multithread e il mapping di dati matematici su schermo.

### Modulo 1.1: Il Motore Grafico (Base)
- [x] **Step 1: Struttura Base XAML.** Setup della `Grid`, del `Canvas` e della griglia cartesiana (offset di 20px per origine assi).
- [x] **Step 2: Logica Matematica.** Creazione algoritmo "Forza Bruta" per test di stress della CPU (Caccia ai numeri primi).
- [ ] **Step 3: Normalizzazione Dati.** Convertire i valori matematici puri in coordinate `(X, Y)` relative allo schermo (`ActualWidth`/`ActualHeight`).
- [ ] **Step 4: Rendering Dinamico.** Collegare dinamicamente una `PointCollection` a una `Polyline` in XAML.

### Modulo 1.2: Architettura Multithreading
- [ ] **Step 5: Isolamento del Calcolo.** Spostare l'algoritmo di stress in background usando `Task.Run` per evitare il freeze della UI.
- [ ] **Step 6: Sincronizzazione a Blocchi.** Usare `Dispatcher.Invoke` per comunicare con il Main Thread solo al termine di specifici "chunk" di dati, evitando il flooding.
- [ ] **Step 7: UI Feedback.** Inserire `ProgressBar` e `TextBlock` reattivi in base ai messaggi del background thread.

### Modulo 1.3: Interfacciamento Hardware
- [ ] **Step 8: Libreria Sensori.** Sostituire il generatore matematico con `LibreHardwareMonitorLib` per leggere il WMI.
- [ ] **Step 9: Isolamento Sensori.** Filtrare l'albero hardware per puntare ai sensori di temperatura del Ryzen 5 5600x e carico della RTX 3060.
- [ ] **Step 10: Effetto "Heartbeat" (Scorrimento).** Sostituire il loop statico con un `DispatcherTimer` a 1000ms.
