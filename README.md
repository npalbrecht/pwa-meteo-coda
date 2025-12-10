# 🌤️ MétéoPWA - Correction TP3

Application météo Progressive Web App (PWA) complète avec notifications.

## 📋 Fonctionnalités implémentées

### Fonctionnalités de base
- ✅ Recherche de ville avec géocodage
- ✅ Affichage de la météo actuelle (température, vent, humidité, ressenti)
- ✅ Prévisions sur 4 heures
- ✅ API Open-Meteo intégrée

### Notifications (Exigence TP)
- ✅ Demande de permission sur action utilisateur
- ✅ Notification si **pluie prévue** dans les 4 prochaines heures
- ✅ Notification si **température > 10°C** prévue

### PWA Complète
- ✅ `manifest.json` avec tous les champs requis
- ✅ `service-worker.js` avec stratégie Cache-First
- ✅ Fonctionnement hors-ligne
- ✅ Installable sur mobile et desktop
- ✅ Icônes en 8 tailles (72 à 512px)

### BONUS implémentés
- ✅ **Dark mode** avec toggle et persistance
- ✅ **Villes favorites** sauvegardées en localStorage
- ✅ Design responsive

## 📁 Structure des fichiers

```
meteo-pwa/
├── index.html          # Page principale
├── style.css           # Styles + Dark mode
├── app.js              # Logique applicative
├── service-worker.js   # SW pour mode hors-ligne
├── manifest.json       # Configuration PWA
└── icons/
    ├── icon.svg        # Source vectorielle
    ├── icon-72.png
    ├── icon-96.png
    ├── icon-128.png
    ├── icon-144.png
    ├── icon-152.png
    ├── icon-192.png
    ├── icon-384.png
    └── icon-512.png
```

## 🚀 Déploiement sur GitHub Pages

### Étapes

1. **Créer un repo GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit - MétéoPWA"
   ```

2. **Pousser sur GitHub**
   ```bash
   git remote add origin https://github.com/VOTRE_USERNAME/meteo-pwa.git
   git branch -M main
   git push -u origin main
   ```

3. **Activer GitHub Pages**
   - Aller dans Settings → Pages
   - Source: Deploy from a branch
   - Branch: main, /(root)
   - Save

4. **Accéder à l'application**
   - URL: `https://VOTRE_USERNAME.github.io/meteo-pwa/`

## 🔍 Vérification Lighthouse

Pour obtenir 90%+ sur Lighthouse :

1. Ouvrir Chrome DevTools (F12)
2. Aller dans l'onglet **Lighthouse**
3. Sélectionner : Performance, Accessibility, Best Practices, SEO, PWA
4. Cliquer sur **Analyze page load**

### Points de vigilance
- ✅ HTTPS obligatoire (GitHub Pages le fournit)
- ✅ Manifest valide
- ✅ Service Worker enregistré
- ✅ Icônes 192px et 512px présentes
- ✅ Meta viewport et theme-color

## 📝 Grille d'évaluation suggérée

| Critère | Points | Détails |
|---------|--------|---------|
| **Recherche ville** | 3 | Géocodage + affichage météo |
| **Notifications pluie** | 3 | Permission + alerte si pluie < 4h |
| **Notifications température** | 2 | Alerte si T° > 10°C |
| **Service Worker** | 3 | Cache + mode offline |
| **Manifest.json** | 2 | Complet et valide |
| **Icônes PWA** | 2 | 192px et 512px minimum |
| **BONUS: Dark mode** | +2 | Toggle + persistance |
| **BONUS: Favoris** | +2 | localStorage |
| **BONUS: Lighthouse 90%+** | +2 | Tous critères |
| **Total** | 15 (+6 bonus) | |

## 🔧 Points techniques clés

### Service Worker - Stratégie de cache
```javascript
// Cache-First pour les assets statiques
// Network-Only pour les API (données fraîches)
```

### Notifications - Code essentiel
```javascript
// 1. Demander permission (sur clic utilisateur)
const permission = await Notification.requestPermission();

// 2. Vérifier l'état
if (Notification.permission === 'granted') {
    // 3. Envoyer la notification
    new Notification('Alerte Météo', {
        body: 'Pluie prévue dans 2h !',
        icon: 'icons/icon-192.png',
        tag: 'weather-alert'  // Évite les doublons
    });
}
```

### Codes météo indiquant la pluie (Open-Meteo)
```javascript
const RAIN_CODES = [51, 53, 55, 56, 57, 61, 63, 65, 66, 67, 
                   71, 73, 75, 77, 80, 81, 82, 85, 86, 95, 96, 99];
```

## 🐛 Problèmes courants

| Problème | Solution |
|----------|----------|
| SW pas enregistré | Vérifier HTTPS ou localhost |
| Notifications bloquées | Paramètres navigateur |
| Cache périmé | Incrémenter `CACHE_NAME` version |
| Icônes pas affichées | Vérifier chemins relatifs |

## 📚 Ressources

- [Open-Meteo API Docs](https://open-meteo.com/en/docs)
- [MDN - Service Workers](https://developer.mozilla.org/fr/docs/Web/API/Service_Worker_API)
- [MDN - Notification API](https://developer.mozilla.org/fr/docs/Web/API/Notification)
- [web.dev - PWA](https://web.dev/progressive-web-apps/)

---

**Auteur**: Correction TP3 - Cours PWA B2 -- Nicolas-Paul ALBRECHT 
**Date**: Décembre 2025
