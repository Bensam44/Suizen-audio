# DEV.md – Guide technique et émotionnel pour l’intégration SuiZen

Ce document définit les règles techniques, la logique émotionnelle et les contraintes d’intégration pour tous les modules audio de l’app SuiZen.  
Chaque fichier est un refuge guidé. Chaque règle protège la sécurité émotionnelle de l’utilisateur.

---

## 🔁 Règles de lecture audio

- Tous les fichiers sont en `.mp3`, intégrés localement dans l’app (aucun streaming)
- La lecture doit être **instantanée**, même en mode avion
- Les ambiances sont mixées pour un **bouclage fluide**, sans coupure ni artefact
- La narration et l’ambiance doivent **démarrer ensemble**, jamais en décalé

---

## 🧩 Architecture modulaire

Chaque module est autonome et émotionnellement complet :

- ✅ Contient narration + ambiance + logique émotionnelle
- ❌ Ne dépend jamais d’un autre module ou d’un placeholder
- 🧠 Conçu pour une progression guidée et une clôture émotionnelle

---

## 📜 Convention de nommage des fichiers

Nommage strict pour éviter les erreurs de routage :


Exemples :
- `calme-ancre.mp3`
- `sos-refuge-v1.mp3`
- `souffle_fem_voix1.mp3`

---

## 🧪 Validation de lecture

Tous les fichiers sont testés pour :

- Compatibilité Android, iOS et web (Base44)
- Type MIME : `audio/mpeg`
- Absence d’erreurs CORS ou 404
- Logique de repli en cas d’échec :

```js
const audio = new Audio('assets/audio/sos-refuge-v1.mp3');
audio.play().catch(() => {
  const fallback = new Audio('assets/audio/calme-ancre.mp3');
  fallback.play();
});
