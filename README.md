# Examen blanc — Permis (Flutter / Dart)

Application desktop/mobile de conduite d'examens blancs du permis, reproduisant
la grille officielle d'évaluation ECF avec notation en temps réel, verdict
automatique, annotations par ligne, import/export des données et génération d'un
rapport PDF à envoyer à l'agence.

## Fonctionnalités

- **Encart candidat** : Nom, Prénom, N° NEPH, Filière (TRAD / ACC / CS),
  Boîte (BVM / BVA), formateur, date.
- **Encart logo** ECF (`assets/ecf_logo.png`).
- **Grille officielle** en blocs de compétences :
  - Connaître et maîtriser son véhicule
  - Appréhender la route
  - Partager la route avec les autres usagers
  - Autonomie — conscience du risque
  - Attitudes (bonus +1 : Courtoisie / Conduite économique)
- **Notation par ligne** : bouton **E** (éliminatoire) + boutons **0/1/2/3**,
  ou **+1** pour les critères bonus.
- **Annotation libre** sous chaque critère.
- **Pastille de verdict** dans l'en-tête : vert (FAVORABLE) si total ≥ 20,
  rouge (INSUFFISANT) sinon, "E" si erreur éliminatoire active.
- **Sous-totaux** par bloc et **total** affiché sur `/31` (seuil 20).
- **Import / Export** des données au format JSON.
- **Rapport PDF** (mise en page complète) via la feuille d'impression/partage,
  pour transmission à l'agence (mail, enregistrement, etc.).

## Prérequis

- Flutter SDK ≥ 3.0 (`flutter --version`).

## Installation

```bash
flutter pub get
flutter run           # sur un appareil/simulateur connecté
```

Cibles possibles : `flutter run -d windows|macos|linux|chrome|android|ios`.

## Build de production

```bash
flutter build apk          # Android
flutter build ios          # iOS
flutter build windows      # Windows
flutter build macos        # macOS
flutter build linux        # Linux
```

## Structure

```
lib/
  main.dart                     Point d'entrée
  models/grille.dart            Modèle de données + grille officielle
  services/stockage.dart        Import / export JSON
  services/rapport.dart         Génération du rapport PDF
  screens/accueil.dart          Écran principal
  widgets/encart_candidat.dart  Encart identité + logo
  widgets/ligne_critere.dart    Ligne de notation + annotation
  widgets/pastille_verdict.dart Indicateur de verdict
assets/ecf_logo.png             Logo ECF
```

## Notes

- Le barème effectif atteignable est de 22 points ; l'affichage du
  dénominateur reste `/31` conformément à la grille papier (paramétrable dans
  `Examen.denominateur`).
- L'option « Examen non mené à son terme » reste une décision manuelle du
  formateur (verdict `Verdict.nonTermine`).
# ECF_ExamB
