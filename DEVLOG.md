# 🛠️ Development Log - Engineering RoadMap 2k26

---

## [16 Giugno 2026] - Sessione 1: Restyling UI Completo e Architettura Schermate

### 🚀 Cosa è stato fatto:
- **Interfaccia Borderless & Custom:** Rimossa la barra del titolo nativa e bianca di Windows. Creata una barra del titolo XAML personalizzata (Total Dark) con supporto al trascinamento della finestra (`DragMove`) e pulsanti custom per ridurre a icona e chiudere l'app.
- **Finestra Stondata (Stile Windows 11):** Arrotondati gli angoli dell'intera applicazione a `12px` usando `Border.Clip` e `RectangleGeometry`. Impostata la trasparenza nativa (`AllowsTransparency="True"`) per eliminare i glitch visivi (i triangolini grigi negli angoli).
- **Sincronizzazione Risorse (`App.xaml`):** Centralizzata la gestione grafica. Creata una palette colori scura (Sfondi, Colore Accento Azzurro, Testo Principale Bianco e Testo Secondario Grigio).
- **Stili Tipografici e Componenti:** Creati gli stili riutilizzabili `StyleBottoni` (con effetto Hover dinamico azzurro e cursore a manina), `StyleTestoPrincipale` e `StyleTestoSecondario`.
- **Navigazione Dinamica:** Collegata la `SchermataGenerale` (dashboard a 4 quadranti) al `ContentControl` della finestra principale, forzando il caricamento automatico della dashboard già al primo avvio dell'app.


---
---
___

### 📈 Stato Attuale:
La "scocca" visiva e l'architettura di navigazione della dashboard sono complete al 100% e rispondono ai comandi. Il look è moderno, coerente e ad alte prestazioni.

### 🔮 Prossimi Passaggi:
- Importazione della libreria `LibreHardwareMonitor` tramite NuGet.
- Sviluppo del motore C# in background per leggere i sensori reali di CPU, GPU, RAM e Dischi e mapparli sulle ProgressBar e sui testi della UI.