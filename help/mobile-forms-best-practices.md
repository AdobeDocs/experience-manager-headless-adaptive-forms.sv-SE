---
title: Bästa praxis för mobilformulär
description: För användning av mobilformulär och offlineformulär kan du bygga en egen app och hämta formulärdefinitioner via det Headless Adaptive Forms API. Rekommenderat tillvägagångssätt för inbyggda mobilappar.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: mobilformulär, inbyggda appar, offlineformulär, headless API
hide: false
exl-id: b8e2f1a4-5c6d-4e2a-9f3b-1d4e5a6c7b8d
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Bästa praxis för mobilformulär {#mobile-forms-best-practices}

För användning av mobilformulär och offlineformulär rekommenderar vi att du bygger en egen app och hämtar formulärdefinitioner via det Headless Adaptive Forms API. Detta ger er full kontroll över den mobila upplevelsen och säkerställer kontinuerlig support när mobilplattformarna utvecklas.

## Rekommenderad metod {#recommended-approach}

Bygg ett mobilprogram (iOS eller Android) som:

1. **Hämtar formulärdefinitionen utan rubrik** - Använd [Headless Adaptive Forms API:er](https://opensource.adobe.com/aem-forms-af-runtime/api/) för att hämta formulär-JSON vid behov (t.ex. när användaren öppnar ett formulär eller navigerar till det i din app). Du kan lista tillgängliga formulär och sedan hämta formulärdefinitionen med ID.

2. **Återger formuläret i din app** - Använd det användargränssnitt (till exempel React Native eller inbyggda vyer) som du föredrar för att återge formuläret från JSON. Du kan använda Forms Web SDK och befintliga Headless-formulär Reagera-komponenter där de passar i högen, eller skapa en egen renderare som använder samma JSON-struktur.

3. **Alternativt stöd för offline** - Implementera lokal lagring och synkronisering i din app. Du kan till exempel cachelagra formulärdefinitioner när du är online, spara utkast lokalt och skicka eller synkronisera data när enheten är online igen.

På så sätt kan du behålla appen när Android och iOS förändras och använder den Headless Adaptive Forms-plattform som stöds för att skapa, validera och skicka formulär.

## Komma igång {#getting-started}

* [AEM Headless adaptive forms overview](overview.md) - Capabilities and concepts.
* [Headless adaptive forms APIs](https://opensource.adobe.com/aem-forms-af-runtime/api/) - Visa, hämta, validera och skicka formulär programmatiskt.
* [Arkitektur](architecture.md) - Hur Headless adaptive forms fungerar och hur front-end-appar använder dem.

Stegvis integrering finns i [Skapa och publicera ett headless-formulär](create-and-publish-a-headless-form.md) och [Developer Portal](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=sv-SE).
