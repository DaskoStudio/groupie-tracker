# Groupie Tracker

> A desktop application written in Go with the Fyne toolkit that browses artists from the public Groupie Trackers API: search, advanced filters, concert details and a map of concert locations.

![Go](https://img.shields.io/badge/Go-1.25-00ADD8?style=flat-square&logo=go&logoColor=white)
![Fyne](https://img.shields.io/badge/Fyne-v2-1e88e5?style=flat-square)
![API](https://img.shields.io/badge/API-REST-38f0c0?style=flat-square)

---

## Table of contents

- [Features](#features)
- [How it works](#how-it-works)
- [Architecture](#architecture)
- [Getting started](#getting-started)
- [Tech stack](#tech-stack)
- [Notes](#notes)

## Features

- **Artist browser** — cards with picture, name, members and creation year.
- **Instant search** with deduplicated suggestions as you type.
- **Advanced filters** — creation-year range, first-album range, number of members, concert location.
- **Detail view** — creation date, first album, members, concert dates and the relation between dates and places.
- **Concert map** — locations are geocoded (Nominatim) and rendered as an OpenStreetMap image with markers, with a button that opens the first location on OpenStreetMap.
- **Spotify shortcut** — opens a Spotify search for the selected artist.

## How it works

The app fetches four resources from <https://groupietrackers.herokuapp.com/api> — artists, locations, dates and relations — and combines them in memory. Filtering and searching run locally on the loaded data, so the UI stays responsive after the initial load.

## Architecture

```text
main.go        Entry point
api/           HTTP calls to the Groupie Trackers API
models/        Data structures (artist, date, location, relation)
services/      Business logic (filtering, search)
ui/            Fyne interface (home, detail, filters, search, markers, map)
```

The code follows a simple separation: `api` knows the network, `models` know the data shape, `services` and `ui/filters` hold the rules, and `ui` only renders.

## Getting started

**Prerequisites:** Go 1.25+ and the system dependencies required by [Fyne](https://docs.fyne.io/started/). An internet connection is required (API, images, geocoding and map).

```bash
git clone https://github.com/DaskoStudio/groupie-tracker.git
cd groupie-tracker
go mod download
go run .
```

## Tech stack

Go · Fyne v2 · REST API · OpenStreetMap / Nominatim

## Notes

- The map is a **static OpenStreetMap image** with markers, not an embedded interactive map; the button opens the full interactive map in your browser.
- The app depends on third-party services (the Groupie Trackers API and OpenStreetMap services). If one is unavailable, the related part of the UI shows a placeholder.

---

**Author** — Konaté Adama · [github.com/DaskoStudio](https://github.com/DaskoStudio)
