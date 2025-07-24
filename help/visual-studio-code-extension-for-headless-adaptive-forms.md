---
title: Visual Studio Code extension for Headless adaptive forms
description: Visual Studio Code extension for Headless adaptive forms
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, adaptive forms, Visual Studio Code extension
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Microsoft Visual Studio Code-tillägg för Headless adaptive forms

Om du använder Microsoft® Visual Studio Code som IDE (Integrated Development Environment) kan du använda det adaptiva Forms-tillägget för Microsoft Visual Studio Code. Tillägg:

* Lägger till IntelliSense-funktioner för Adaptive Forms i Visual Studio Code.
* Hjälper till att validera och komplettera JSON-syntaxen automatiskt för komponenter i Headless-anpassade formulär.
* Navigerar enkelt strukturen i ett headless adaptivt formulär via en panel.
* Hjälper till att översätta en Headless-anpassningsbar form.

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Förutsättningar

* Hämta och installera [Microsoft Visual Studio Code 1.62.0 eller senare](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Om du har en äldre version eller ingen version installerad hämtar du den senaste versionen från [Microsoft webbplats](https://code.visualstudio.com/docs/setup/setup-overview). Information om hur du använder Visual Studio från kommandoraden i Apple macOS finns i [Starta från kommandoraden](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Hämta tillägget [Adaptiv formulärbyggare](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Installera tillägget

1. Öppna kommandotolken och navigera till katalogen som innehåller den hämtade tilläggsfilen, *adaptive-form-builder-[version].vsix*.

1. Kör följande kommando för att installera tillägget:

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Installerar tillägg](/help/assets/install-extension.png)


   Mer information om VSX-filer finns i [Microsoft Visual Studio Code Help](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix).
