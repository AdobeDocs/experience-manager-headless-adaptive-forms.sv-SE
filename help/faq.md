---
title: Vanliga frågor
description: Vanliga frågor
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, adaptive form, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# Vanliga frågor och svar {#headless-adaptive-forms-faq}

## Ska jag känna till React.js för att använda Headless adaptive-formulär?

Du kan använda vilket ramverk, bibliotek eller språk som helst för att återge formulär som kan anpassas utan Headless och använda våra REST API:er för att validera och skicka formulären. AF-core-biblioteket, som tillhandahålls av OTB, är ramverksoberoende. Bibliotek för React Render och React Component (React-Render och React-komponenter), förutsatt att OTB finns, är till din bekvämlighet. Du kan utveckla egna komponenter och är inte begränsad till dessa.

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Kräver jag att Forms as a Cloud Service sandlåda använder Headless-formulär?

Du kan använda startappen för att börja utveckla och formatera dina Headless-formulär. Du behöver Forms as a Cloud Service för att hantera Headless-anpassade formulär tillsammans med backend-formulärfunktioner.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Var kan jag förhandsgranska en Headless-blankett? {#storybook-example}

Du kan använda startappen för att återge och förhandsgranska ett anpassat Headless-formulär. Du kan också ändra en [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) exempel för att förhandsgranska ett Headless-formulär.

![](/help/assets/storybook-example.png)

## Går det att använda Headless-anpassade formulär med anpassade ramverk?

Headless adaptive forms are based on [standardspecifikation](/help/assets/Headless-Adaptive-Form-Specification.pdf). Du kan utöka specifikationen och använda den för att skapa anpassade komponenter. Exempel: komponenter för Chakra-gränssnittet, Vue.js med flera.

## Har Headless adaptive forms stöd för överlappande fält?

I överlappande fält beror innehållet i det andra fältet på det innehåll som väljs i det första fältet. The [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behavior—options&amp;args=formJson.items[0].fieldType:drop down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items son.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) innehåller ett exempel på överlappande fält.

## Kan man med Headless-anpassade blanketter förifylla blanketter med skräddarsydda data?

Headless adaptive forms allows prefill forms with personalized data. The [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) innehåller ett exempel på hur du förifyller en Headless-blankett.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Kan jag använda Headless-anpassade formulär med Angular SPA?

Du kan använda Web SDK för att integrera Headless-anpassade formulär med Angular SPA. Den är oberoende av alla ramverk. Du kan använda React SDK som referens.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Finns det någon plugin som underlättar utvecklingen för Headless AF?

Ja, det finns ett tillägg för Microsoft Visual Studio Code. Det är ett bekvämt sätt att manuellt skapa Headless-anpassade JSON-formulär.

## Kan ett Headless-anpassat formulär ansluta till någon CRM för att läsa eller skriva data?

Du kan använda Microsoft Dynamics och Salesforce för att skicka eller förifylla ett Headless-formulär. Förutom CRM:er har Headless adaptive forms stöd för att skicka eller förifylla med REST-slutpunkter, e-post och anpassade skicka-åtgärder.
