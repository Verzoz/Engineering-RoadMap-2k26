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

## 🖥️[Fase 1] - WPF Hardware Monitor

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




# ⚛️ [Fase 2] - C++ Particle Engine 2D

Un motore fisico bidimensionale scritto da zero in **C/C++**. 

Questo progetto segna la transizione dall'ecosistema gestito (.NET/C#) alla programmazione a basso livello ("Bare Metal"). L'obiettivo è costruire un simulatore capace di calcolare e renderizzare le interazioni elettromagnetiche e cinematiche tra migliaia di particelle in tempo reale, affrontando le sfide classiche dello sviluppo di motori grafici e fisici.

## 🎯 Competenze Target
- Gestione manuale della memoria (Allocazione dinamica, Puntatori e Memory Leaks).
- Architettura software basata su **Game Loop** (Input, Update, Render) e *Fixed Time Step*.
- Implementazione di logiche di **Integrazione Numerica** (es. Metodo di Eulero o Verlet) per la simulazione cinematica.
- Ottimizzazione algoritmica avanzata: superare il limite computazionale $O(N^2)$ per le interazioni a molti corpi.

---

## 🗺️ Roadmap Architetturale (Fase 2)

### Modulo 1: Infrastruttura e Rendering Base (Il Core)
L'obiettivo di questo modulo è configurare l'ambiente di compilazione C/C++ e stabilire il battito cardiaco dell'applicazione: il Game Loop.
- [ ] **Build System:** Configurazione del compilatore e del sistema di build (es. CMake o Makefile) per gestire dipendenze e link statici/dinamici.
- [ ] **Astrazione Grafica:** Setup di un layer grafico essenziale tramite librerie native (es. Raylib o SDL2) per l'apertura del contesto OpenGL e il disegno di primitive.
- [ ] **Game Loop Architecture:** Implementazione di un ciclo di vita ad alta frequenza che separi rigidamente l'elaborazione degli input, l'aggiornamento dello stato fisico e il rendering a schermo.

### Modulo 2: Sottosistema Matematico e Cinematico
L'obiettivo di questo modulo è definire le regole dello spazio bidimensionale e far muovere i primi oggetti basandosi sulle leggi del moto.
- [ ] **Libreria Algebra Vettoriale:** Sviluppo di strutture dati custom (es. `Vector2`) per calcolare somme, differenze, prodotti scalari e distanze euclidee.
- [ ] **Rappresentazione dello Stato:** Definizione delle entità fisiche tramite attributi vettoriali isolati (Posizione, Velocità, Accelerazione, Massa).
- [ ] **Integrazione Temporale:** Traduzione del Tempo Delta ($dt$) in spostamento spaziale, applicando la gravità e i vincoli ambientali (es. rimbalzo perfettamente elastico sui bordi della finestra).

### Modulo 3: Il Motore Dinamico (Forze e N-Body Problem)
L'obiettivo di questo modulo è far interagire le particelle tra loro, applicando le leggi della dinamica e dell'elettromagnetismo.
- [ ] **Campi di Forza:** Implementazione di funzioni per applicare forze continue e repentine (es. Legge di Coulomb per l'attrazione/repulsione).
- [ ] **Broad-Phase Collision Detection:** Sviluppo di logiche per individuare quali entità sono sufficientemente vicine da collidere (sovrapposizione di bounding box o raggi).
- [ ] **Collision Response:** Calcolo della conservazione della quantità di moto per risolvere urti elastici tra entità con masse diverse.

### Modulo 4: Ottimizzazione Strutturale (Performance)
L'obiettivo finale è scalare il sistema. Con il calcolo "forza bruta", controllare ogni particella contro tutte le altre ($N^2$) fa collassare la CPU già a 1.000 entità.
- [ ] **Profilazione Memoria:** Utilizzo di tool di base per identificare colli di bottiglia computazionali e ottimizzare la localizzazione in cache (Data-Oriented Design).
- [ ] **Spatial Partitioning (Griglie o QuadTree):** Implementazione di strutture dati spaziali avanzate per suddividere l'area di rendering, limitando il calcolo delle forze solo alle particelle appartenenti alle celle vicine.
- [ ] **Stress Test:** Portare la simulazione fluida (60 FPS) oltre le 10.000 entità interattive simultanee.




# 🤖 [Fase 3] - mCore Autonomous Rover

Sviluppo di firmware embedded (C/C++) per un microcontrollore basato su architettura AVR (ATmega328P / Arduino Uno custom). 

Questo progetto rappresenta il primo contatto con il mondo cyber-fisico. L'obiettivo è superare la pura simulazione software per costruire un sistema autonomo capace di leggere dati dall'ambiente reale, prendere decisioni tramite logica di controllo (Macchine a Stati Finiti) e comunicare lo stato operativo a una Ground Station (la dashboard sviluppata nella Fase 1).

## 🎯 Competenze Target
- Sviluppo Firmware "Bare Metal" e comprensione dei vincoli hardware (Limiti di clock, RAM misurata in Kilobyte).
- Configurazione e utilizzo di interfacce I/O fisiche: GPIO, PWM (Pulse Width Modulation) e ADC (Analog-to-Digital Converter).
- Architettura software per sistemi real-time (Interruzioni hardware, Watchdog, loop non bloccanti).
- Design e implementazione di protocolli di comunicazione Seriale (UART) bidirezionali.

---

## 🗺️ Roadmap Architetturale (Fase 3)

### Modulo 1: Hardware Abstraction Layer (HAL) e Attuazione
L'obiettivo di questo modulo è separare la logica di alto livello dai dettagli fisici dei pin e dei registri della scheda mCore.
- [ ] **Toolchain Setup:** Configurazione dell'ambiente di cross-compilazione (es. PlatformIO o Arduino IDE) e del programmatore seriale.
- [ ] **Sottosistema di Attuazione (PWM):** Sviluppo di interfacce per il controllo proporzionale dei driver motori DC, gestendo accelerazione, decelerazione e inversione di polarità.
- [ ] **Costruzione dell'HAL:** Creazione di classi C++ "wrapper" per incapsulare il controllo hardware (es. `MotorController`, `LEDManager`), garantendo che la logica di business ignori l'esistenza dei pin fisici.

### Modulo 2: Acquisizione Dati e Signal Conditioning
L'obiettivo di questo modulo è leggere lo stato del mondo fisico tramite i sensori integrati, gestendo l'inevitabile rumore elettrico e le latenze.
- [ ] **Polling vs Interrupts:** Implementazione della lettura del sensore a ultrasuoni (Time-of-Flight) utilizzando interrupt hardware per non bloccare il ciclo di clock (Super Loop).
- [ ] **Digital Signal Filtering:** Sviluppo di algoritmi di filtraggio matematico (es. Filtro a Media Mobile / Moving Average) per stabilizzare le letture dei sensori di distanza ed eliminare i "falsi positivi" generati dal rumore ambientale.
- [ ] **Gestione Sensori Ottici:** Calibrazione e lettura analogica del modulo Line Follower (sensori a infrarossi) per il riconoscimento dei pattern a terra.

### Modulo 3: Logica di Autonomia (Macchina a Stati)
L'obiettivo di questo modulo è dotare il rover di un "cervello" reattivo, sostituendo i semplici script sequenziali (`delay()`) con architetture decisionali robuste.
- [ ] **Finite State Machine (FSM):** Progettazione e codifica di una Macchina a Stati Finiti per la gestione dei comportamenti (es. `Stato_Esplorazione`, `Stato_Ostacolo_Rilevato`, `Stato_Evasione`).
- [ ] **Timer Non Bloccanti:** Sostituzione di tutte le attese bloccanti con delta-time basati sul clock di sistema (es. `millis()`), garantendo che il rover possa ascoltare sensori e muovere motori simultaneamente.
- [ ] **Safety & Fail-Safe:** Implementazione di logiche di sicurezza (es. spegnimento istantaneo dei motori se le letture dei sensori impazziscono o se la connessione cade).

### Modulo 4: Telemetria e Integrazione PC (Ground Station)
L'obiettivo finale è chiudere il cerchio dell'intero ecosistema sviluppato finora: far dialogare il rover fisico (Fase 3) con la dashboard WPF sul PC (Fase 1).
- [ ] **Design del Protocollo Seriale:** Creazione di un protocollo a pacchetti custom e leggero (es. `<START_BYTE> <COMANDO> <PAYLOAD> <CHECKSUM> <END_BYTE>`) per inviare dati senza corruzione.
- [ ] **Data Streaming (Rover -> PC):** Trasmissione in tempo reale via cavo o Bluetooth delle metriche interne (distanza ostacoli, velocità motori, stato FSM).
- [ ] **WPF Telemetry Integration:** Aggiornamento del progetto C# (Fase 1) per aprire la porta COM, decodificare i pacchetti seriali del rover e tracciare le misurazioni fisiche sul grafico dinamico in sostituzione dei dati WMI.
