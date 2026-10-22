# Groupie Tracker

Application de bureau en **Go** (GUI **Fyne**) qui consomme l'API [Groupie Trackers](https://groupietrackers.herokuapp.com/api) : liste d'artistes, fiche détaillée, filtres, recherche et **carte des lieux de concert**.

## ✨ Fonctionnalités

- Liste des artistes avec image, membres et année de création
- Fiche détaillée : concerts, dates et relations dates/lieux
- Recherche instantanée (nom, membre, lieu…)
- Filtres (date de création, premier album, nombre de membres, localisation)
- Carte interactive des lieux de concert (markers géocodés)

## 🧱 Architecture

```
main.go        # point d'entrée
api/           # appels HTTP vers l'API Groupie Trackers
models/        # structures de données (artist, date, location, relation)
services/      # logique métier (filtres, recherche)
ui/            # interface Fyne (home, détail, filtres, carte, markers)
```

## 🚀 Lancer le projet

```bash
go mod download
go run .
```

> Prérequis : Go 1.25+ et les dépendances système de [Fyne](https://docs.fyne.io/started/).

## 🛠️ Stack

Go · Fyne v2 · API REST Groupie Trackers

## 👤 Auteur

Konaté Adama (**[@DaskoStudio](https://github.com/DaskoStudio)**) — Ynov Campus
