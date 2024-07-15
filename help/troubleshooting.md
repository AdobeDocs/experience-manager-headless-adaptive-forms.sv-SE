---
title: Headless Adaptive Forms Troubleshooting
description: Headless Adaptive Forms Troubleshooting
keywords: headless, adaptive form, Troubleshoot
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Felsökning

## Det gick inte att distribuera Archetype-projektet på den lokala utvecklingsmiljön

### Problem

När du använder `mvn -PautoInstallPackage clean install` eller liknande kommandon för att distribuera ett AEM Archeype-projekt misslyckas projektet med distributionen.

### Orsak

Det kan inträffa på grund av en version som inte stöds eller en skadad installation av node.js eller NPM.

### Lösning

1. [Ta bort befintliga installationer av Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) helt från din miljö.

1. Installera Node.JS 16.13.0 eller senare med NPM.

1. Starta om datorn.


## Kommandot `mvn clean install` kan inte köras

### Problem

När du använder `mvn clean install` eller liknande kommandon för att distribuera ett AEM Archeype-projekt kan kommandot inte köras.

### Orsak

Det kan hända om Git inte är installerat.

### Lösning

Hämta och installera den [senaste versionen av Git](https://git-scm.com/downloads). Om du inte har använt Git tidigare läser du [Installera Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
