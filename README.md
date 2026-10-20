# ChordStream

**An Android songbook for rehearsals and live performance.**

Organize songs, adapt chord charts to each musician, and keep the setlist ready
to play. ChordStream combines a local song library with collaborative workspaces.

<p align="center">
  <img src="docs/assets/00_portada_chordstream.png" alt="ChordStream library, live reader, and music editor" width="540">
</p>

**Created by [José Pablo Quirós Vásquez](https://github.com/jquirosv).**

This repository is the public case study for ChordStream. The application source
code, tests, and development history are maintained in a separate private
repository. This showcase contains documentation and demonstration images.

## The problem

Musicians often prepare a repertoire across PDFs, screenshots, and messages.
Keys change, versions drift apart, and singers and instrumentalists need different
views of the same song. ChordStream keeps one structured song and derives the
reading view from its musical content and the player's instrument.

## What I built

- A Flutter application for Android, including the library, editor, reader,
  setlists, and instrument-specific views.
- A Dart music engine with a lexer, parser, musical tree, transposition, and filters.
- Local SQLite persistence, drafts, backup import/export, and recoverable deletion.
- A PHP/MySQL API for accounts, group permissions, shared songs, and synchronization.

## Main features

| Area | Capabilities |
| --- | --- |
| Library | Search, tags, covers, sorting, and song organization. |
| Editor | Syntax highlighting, validation, preview, and draft recovery. |
| Reader | Chord-aligned lyrics, transposition, auto-scroll, sections, and metronome. |
| Instruments | Guitar, bass, vocals, harmony, custom tunings, and chord diagrams. |
| Tablatures | Text tabs and a visual tablature builder. |
| Setlists | Song ordering and performance settings. |
| Collaboration | Groups, invitations, roles, and revision conflict handling. |
| Portability | ChordPro conversion and native backup import/export. |

Individual mode works locally without an account or Internet connection.
Group changes require connectivity and confirmation from the server.

## Screenshots

Real Flutter widgets with original demonstration content and fictional data.

| Library | Live reader | Editor |
| :---: | :---: | :---: |
| ![Song library](docs/assets/01_biblioteca_musical.png) | ![Live reader](docs/assets/02_lector_en_vivo.png) | ![Music editor](docs/assets/03_editor_musical.png) |

| Setlists | Visual tablature | Chord dictionary |
| :---: | :---: | :---: |
| ![Setlists](docs/assets/04_setlists.png) | ![Visual tablature](docs/assets/05_editor_vtab.png) | ![Chord dictionary](docs/assets/06_diccionario_acordes.png) |

[Group collaboration](docs/assets/07_colaboracion.png) ·
[Image provenance](docs/assets/README.md)

## Technologies

| Layer | Technologies |
| --- | --- |
| Application | Flutter, Dart, Material, Provider, Canvas/CustomPainter |
| Music engine | Dart lexer/parser, musical tree, validation, and transposition |
| Local data | SQLite/sqflite, secure storage, files, and compressed backups |
| Backend | PHP, PDO, MySQL, REST, and JSON |
| Engineering | Git, Flutter Test, PHP tests, OpenAPI, and GitHub Actions |

## Engineering decisions

- **Preserve the original song:** transposition and instrument filtering operate
  on an in-memory musical tree rather than rewriting the user's text.
- **Keep lyrics readable:** chord placement uses a separate layout layer so
  embedded chords do not break words and natural line wrapping.
- **Protect collaborative edits:** API revisions, transactions, and idempotency
  handle concurrent changes and retries.
- **Keep personal work available:** the individual library uses local SQLite;
  group writes are confirmed by the server.

[Architecture](docs/ARCHITECTURE.md) ·
[Technical challenges and decisions](docs/TECHNICAL_NOTES.md)

## Project status

- Code version reviewed: **1.1.1+16**.
- Client platform: **Android 7.0 / API 24 and later**.
- Local verification on October 20, 2026: **282 Flutter tests and 31 PHP tests passed**;
  OpenAPI validation and parity of **60 API operations** also passed.
- The screenshots demonstrate the interface; this repository does not distribute
  application binaries or provide a public demo account.

## Author

[José Pablo Quirós Vásquez](https://github.com/jquirosv) · Costa Rica

This is one project in my portfolio. Visit my profile to explore my background
and other projects.

---

<details>
<summary>Leer en español</summary>

## ChordStream: caso de estudio

ChordStream es un cancionero para Android que permite organizar repertorios,
editar letras y acordes, transponer canciones y preparar setlists. Incluye vistas
por instrumento, tablaturas, desplazamiento automático y funciones colaborativas.

Mi trabajo abarca el cliente Flutter, el motor musical en Dart, la persistencia
local con SQLite y la API PHP/MySQL para cuentas y grupos. Entre los retos se
encuentran alinear acordes sin romper palabras, transformar una canción sin
sobrescribir su fuente y gestionar cambios concurrentes.

Este repositorio es la ficha pública de ChordStream dentro de mi portafolio.
El código, las pruebas y el historial de desarrollo se mantienen en un repositorio
privado independiente. Aquí se muestran la propuesta, las capturas, la arquitectura
y las decisiones técnicas.

La biblioteca individual funciona sin cuenta ni conexión. Los cambios de grupo
requieren conexión y confirmación del servidor. Las capturas utilizan contenido
de demostración y datos ficticios.

</details>

© 2026 José Pablo Quirós Vásquez. See [COPYRIGHT.md](COPYRIGHT.md).
