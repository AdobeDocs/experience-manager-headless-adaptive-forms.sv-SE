---
title: AEM Headless Adaptive Forms - översikt
description: Översikt över formulär som kan anpassas efter AEM Headless.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 3%

---


# Versionsinformation

Välkommen till Experience Manager Headless adaptive forms tidig adopter release. Läs vidare för att få resurser och instruktioner för att komma igång och få det bästa i releasen.

Använd Adobe Experience Manager headless adaptive forms för att skapa blankettapplikationer med ramverk som React, Angular med flera. Använd Adaptive Forms Web SDK för statshantering, validering och integration med ytterligare kontaktytor.


Den tidiga utgåvan av en användare ger dig tillgång till formulär som kan användas utan Headless-funktioner i en [lokal utvecklingsmiljö](setup-development-environment.md). Du kan använda den lokala utvecklingsmiljön för att skapa och testa Headless-formulär.

Headless adaptive forms receive improvements on the current-basis. Besök sidan regelbundet för att hålla dig uppdaterad om den senaste utvecklingen. Den här sidan innehåller information om följande:

* tidig åtkomst
* senaste releaser
* nya funktioner
* förbättringar
* felkorrigeringar
* inaktuell funktion
* specialinstruktioner
* Framtida planer för ändringar

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefakter som är tillgängliga i tidiga versioner av användare

I den tidiga releasen av Adobe Experience Manager Headless finns följande artefakter:

### AEM Forms as a Cloud Service SDK

AEM Forms as a Cloud Service SDK hjälper dig att skapa, lagra och hämta Headless-formulär. Den kan även tillhandahålla förifyllning, validering av regler på serversidan och skicka-tjänster för formulär utan Headless-funktionalitet.

### Forms Web SDK

Forms Web SDK innehåller API:er för att validera begränsningar som tillämpas på olika fält i ett formulär och kopplingar för att ansluta formulärets JSON-struktur till gränssnittets ramverk. Den innehåller även &#x200B; React Renderer för Headless-adaptiva formulär som hjälper dig att integrera ett Headless-adaptivt formulär i programmet. Följande komponenter i Web SDK är tillgängliga:

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) innehåller en översikt över de olika komponenterna i formulär som kan anpassas efter Headless. Den innehåller också en lista över alla komponenter som stöds, deras motsvarande egenskaper och begränsningar.

### Forms Core Component

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

De centrala komponenterna är en uppsättning standardiserade WCM-komponenter (Web Content Management) som hjälper dig att snabba upp utvecklingsarbetet och minska underhållskostnaderna för formulären. Forms Container-komponenten är en kärnkomponent. Det hjälper dig att bädda in och återge en JSON-struktur av Headless adaptive form i Adaptive Forms Editor i Forms as a Cloud Service SDK.

### Adaptiva Forms V2-specifikationer

Headless adaptive forms specification provides detailed information on all the components, constraints, and methods available to define Headless adaptive forms. Specifikationen är tillgänglig i formatet [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

### HTTP och JS API

[HTTP-API:er](https://opensource.adobe.com/aem-forms-af-runtime/api/) gör att du kan visa, hämta, validera, skicka och spåra status för headless-formulär. <!-- URL is 404! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

### Visual Studio Code Extension

[Visual Studio Code extension](visual-studio-code-extension-for-headless-adaptive-forms.md) om du vill skapa en giltig JSON-struktur. Den har IntelliSense-stöd och -validering för JSON-formulärstruktur tillsammans med vanliga funktioner som att lägga till, ta bort eller byta namn på komponenter i en JSON-struktur.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->