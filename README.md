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

## Fase 1 - WPF Hardware Monitor

Un'applicazione desktop moderna per il monitoraggio in tempo reale delle prestazioni hardware (CPU, GPU, RAM), sviluppata in **C#** e **WPF** (Windows Presentation Foundation).

Questo progetto è il primo capitolo della *Engineering Roadmap 2026* e ha l'obiettivo di esplorare l'architettura delle interfacce grafiche, il multithreading e l'interfacciamento con i sensori fisici del PC.

## 🎯 Competenze Target
- Sviluppo UI dichiarativa tramite **XAML**.
- Gestione della concorrenza e pattern **Multithreading** (Task & Dispatcher).
- Acquisizione e parsing di dati hardware di basso livello tramite librerie esterne.
- Rappresentazione grafica dinamica di serie temporali (Data Visualization).

---

## 🗺️ Roadmap Architetturale (Fase 1)

### Modulo 1: Il Motore di Rendering (UI & Grafica)
L'obiettivo di questo modulo è creare l'infrastruttura visiva capace di disegnare grafici vettoriali in base a dati numerici astratti.
- [ ] **Setup Ambiente WPF:** Strutturazione del layout principale (Grid, Pannelli di controllo, Area Grafico).
- [ ] **Sistema di Coordinate:** Implementazione della logica di mappatura per tradurre valori numerici astratti nelle coordinate fisiche della finestra.
- [ ] **Disegno Vettoriale Dinamico:** Utilizzo di oggetti WPF nativi (es. `Polyline`, `PointCollection`) per tracciare linee aggiornabili via codice.

### Modulo 2: Il Motore Asincrono (Multithreading)
L'obiettivo di questo modulo è separare la logica di business e di calcolo dal thread dell'interfaccia utente, prevenendo freeze e lag.
- [ ] **Isolamento dei Task:** Spostare i carichi di lavoro simulati in thread di background separati.
- [ ] **Comunicazione Inter-Thread:** Implementare il pattern di delega (tramite `Dispatcher`) per permettere ai thread di background di aggiornare la UI in sicurezza.
- [ ] **Sincronizzazione Dati:** Ottimizzare la frequenza di aggiornamento grafico per mantenere i 60 FPS senza inondare (flooding) la coda dei messaggi di Windows.

### Modulo 3: Il Motore Sensoriale (Hardware API)
L'obiettivo di questo modulo è sostituire i dati simulati con letture reali provenienti dall'hardware della macchina (WMI).
- [ ] **Integrazione API Esterne:** Inclusione e setup di librerie specializzate (es. LibreHardwareMonitorLib).
- [ ] **Interrogazione dell'Hardware Tree:** Scansione dei nodi del sistema per isolare sensori specifici (es. Carico GPU RTX, Temperature Core Ryzen).
- [ ] **Gestione Privilegi:** Configurazione dell'eseguibile per la richiesta di permessi di Amministratore, necessari per le letture a basso livello.

### Modulo 4: Il Loop di Monitoraggio (Sistema Finale)
L'obiettivo di questo modulo è unire i precedenti per creare un ciclo continuo, stabile e autonomo di lettura e disegno.
- [ ] **Implementazione del Polling:** Creazione di un Timer di sistema per campionare i dati hardware a intervalli regolari (es. 1000ms).
- [ ] **Buffer Circolare (Effetto Scorrimento):** Modifica dell'algoritmo di disegno per gestire code di dati FIFO, permettendo al grafico di scorrere visivamente nel tempo (rimuovendo i dati obsoleti).
- [ ] **Polish UI (Simil-Afterburner):** Separazione degli stili XAML in ResourceDictionaries e organizzazione della dashboard in sezioni tematiche (CPU, GPU, RAM).
