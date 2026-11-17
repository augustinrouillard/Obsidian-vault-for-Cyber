---
share: true
---
# Obsidian-vault-for-Cyber

## Table of contents

- [About](#about)
- [Architecture](#Architecture)

## [About](#about)

Here is my personal Obsidian vault dedicated to cybersecurity.

It is organized into three main folders:
- **Box**
- **CTF**
- **Personal Docs**
- **Scripts**
- **Systèmes et réseaux**

---

**BOX**
This folder contains write-ups and solutions from cyber plateforms. Some of the box i did are not in the folder (I still need some time to tidy up my notes so that they’re easy to understand).

**CTF**  
This folder contains write-ups and solutions from various Capture The Flag challenges, categorized by topics such as Cryptography, Forensics, OSINT, Web, etc..

**Personal Docs**  
This folder includes technical datasheets and practical guides for different cybersecurity topics.

**Scripts**  
This folder houses reusable scripts for automation.
There is also a **"To complete..."** folder for resources that are still under learning.
This vault serves as a comprehensive repository for my cybersecurity knowledge and resources.
I've started revising all my CTF and “box” challenge reports, but it's taking me a long time (so not all of them are available yet).
I do this out of passion; I'm not a professional, so it's probably not perfect.

**Systèmes et réseaux**
_(Only available in French, but I’d like to translate it to make it accessible to everyone)_ 
Ce dossier comprend l'ensemble de mes connaissances en réseau.
Je m'en sert à la fois pour mes révisions et comme bibliothèque dans laquelle je trouve des solutions.
J'essaie de mettre les informations à jour mais tout n'est peut-être pas optimisé (je vous invite à vérifier par vous même sans prendre ce que vous trouverez ici comme vérité absolue).
Ici comme pour le reste des dossiers, je l'ai construit par passion et je suis conscient d'avoir encore beaucoup à apprendre :) .

---

## [Architecture](#Architecture)

```text

┌────────────────────────────────────────────────────────────────────────────────┐
│ CYBERSECURITY VAULT ARCHITECTURE                                               │
├──────────────────┬──────────────────────────────┬──────────────────────────────┤
│ Folders          │ Categories                   │ Purpose                      │
├──────────────────┼──────────────────────────────┼──────────────────────────────┤
|  /Box            | • TryHackMe                  |  Write-ups and solutions     |
|                  | • Rootme                     |  from training web plateforms|
|                  | • HacktheBox                 |  (I need some time to get    |
|                  |                              |  them back into shape)       |
├──────────────────┼──────────────────────────────┼──────────────────────────────┤
│ /CTF             │ • Cryptography               │ Write-ups and solutions      │
│                  │ • Forensics                  │ from CTF challenges          │
│                  │ • Misc                       │                              │
│                  │ • OSINT                      │                              │
│                  │ • Web                        │                              │
├──────────────────┼──────────────────────────────┼──────────────────────────────┤
│ /Personnal Docs  │ • Crypto (encryption)        │ Technical datasheets         │
│                  │ • Forensic (disks, DB)       │ and practical guides         │
│                  │ • Languages (Bash)           │ for cybersecurity            │
│                  │ • Memory (dumps)             │                              │
│                  │ • OSINT (Exiftool, etc.)     │                              │
│                  │ • Stegano (checklists)       │                              │
│                  │ • Web (bruteforce, scans)    │                              │
├──────────────────┼──────────────────────────────┼──────────────────────────────┤
│ /Scripts         │ Extract red bytes            │ Reusable scripts             │
│                  │ Other utilities              │ for automation               │
├──────────────────┼──────────────────────────────┼──────────────────────────────┤
│ /Systèmes et     │ • Distribution Linux et GNU  │ Ma propre bibliothèque de    │
|  Réseaux         | • Les bases du réseau        | notes sur le système réseau  |
│ (Only in French  │ • Microsoft et outils colla- │                              │
|  for now)        |   boratifs                   |                              |
|                  | • Powershell                 |                              |
|                  | • Systèmes clients Microsoft |                              |
└──────────────────┴──────────────────────────────┴──────────────────────────────┘
```
