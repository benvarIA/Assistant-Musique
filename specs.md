# Assistant Musique — Specs techniques, UI/UX & fonctionnelles

> Suite d'outils d'assistance à la **production musicale et à la gestion de samples** : assistant au mixage/mastering, gestionnaire de samples, et extracteur de samples.

**Date de rédaction :** 2026-06-03
**Statut :** Phase d'idéation (3 projets identifiés, aucun démarré)

---

## 1. Contexte

Ce dossier regroupe des projets d'outils autour de la production musicale. Trois idées sont définies, à prioriser et développer séparément (ou en app unifiée).

---

## 2. Projets identifiés

### 2.1 Assistant Mixage / Mastering
> Voir le projet dédié **Mixage-Mastering-IA** (`/Volumes/NAS/Apps/Mixage-Mastering-IA/`) — déjà en développement avec un déroulé complet spécifié.
>
> Ce module pourrait être intégré ou lié à l'Assistant Musique global, ou rester un projet indépendant.

---

### 2.2 SampleManager

**Objectif :** gérer, organiser, tagger et retrouver facilement une bibliothèque de samples audio.

**Problème :** les samples (loops, one-shots, présets) s'accumulent dans des dossiers non organisés, sans tags homogènes, difficiles à retrouver au moment de la production.

**Fonctionnalités envisagées :**
- [ ] Scan de dossiers → import de la bibliothèque de samples
- [ ] Tags automatiques par analyse audio (BPM, tonalité, type : loop/one-shot/pad…)
- [ ] Tags manuels (instrument, mood, projet…)
- [ ] Recherche et filtres (BPM, tonalité, durée, tags)
- [ ] Lecture préview directement dans l'app (sans ouvrir un DAW)
- [ ] Favoris et listes de recherche sauvegardées
- [ ] Intégration drag & drop vers Ableton / Finder

**Stack envisagée :** à définir (Electron ou app web locale avec serveur Node + ffprobe pour l'analyse audio)

---

### 2.3 Extracteur de Samples

**Objectif :** extraire automatiquement des samples (loops, one-shots) depuis des morceaux audio existants ou des enregistrements.

**Fonctionnalités envisagées :**
- [ ] Import d'un fichier audio (WAV / MP3 / AIFF)
- [ ] Détection de transients → découpage automatique en segments (one-shots potentiels)
- [ ] Détection de zones répétitives → suggestion de loops
- [ ] Paramètres : seuil de transient, taille min/max de segment, fade in/out
- [ ] Préview de chaque extrait + validation manuelle
- [ ] Export des extraits (nommage automatique)

**Stack envisagée :** Python (librosa / pydub pour l'analyse audio) + UI web simple ou Streamlit

---

## 3. Questions à trancher

- **App unifiée ou 3 projets séparés ?**
  - Unifié : une seule interface, navigation entre les outils
  - Séparé : chaque outil reste autonome, intégrable à l'App Manager V2
- **Priorité de démarrage** : SampleManager (valeur immédiate pour la production) vs Extracteur de Samples ?
- **Stack** : Electron (desktop, accès natif au filesystem) vs webapp locale (Node + React) ?

---

## 4. Hors scope / roadmap lointaine

- Synchronisation cloud de la bibliothèque
- Analyse musicale avancée (chord detection, stem separation)
- Plugin DAW (VST/AU/Max for Live natif) — voir BenvariForLive pour les Max for Live devices
