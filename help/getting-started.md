---
title: Komma igång med Headless Adaptive Forms
description: Komma igång med Headless Adaptive Forms
keywords: headless, adaptive form, självstudiekurs
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Komma igång med Headless Adaptive Forms

I den här självstudiekursen får du ett komplett ramverk för att skapa ett Headless-formulär. Självstudiekursen är indelad i ett användningsfall och i flera guider. Varje guide hjälper dig att lära dig mer och lägga till nya funktioner i det Headless-anpassade formulär som skapas i kursen. Du har en fungerande Headless-anpassningsbar form efter varje guide. I slutet av den här självstudiekursen kan du:

* Skapa ett Headless-formulär
* Lägg till affärsregler i formuläret
* Använd Google materialgränssnitt för att formatera formulär
* Fyll i formuläret i förväg 
* Bädda in formuläret på en webbsida

Du kommer också att bygga upp en förståelse för arkitektur, tillgängliga artefakter och JSON-strukturen för Headless-adaptiva formulär.

**Resan börjar med att lära sig användningsexemplet**:

Raya Tan, som är medlem av en utländsk avdelning i ett land som är känt för sin naturliga skönhet och en livskraftig turistekonomi, ansvarar för fördelningen av viseringsformulär till turister. Dessa formulär finns på avdelningens webbplats, i mobilappar och i PDF-format, med flera språkalternativ att välja mellan för turister. Att hantera och skala dessa formulär över olika plattformar och tekniker kan dock vara en utmaning.

För att förbättra effektiviteten och flexibiliteten i deras viseringsansökningsprocess har den utländska avdelningen beslutat att anta en strategi för headless adaptive forms. Denna frikopplade arkitektur separerar frontend från backend-systemet, vilket ger större anpassning och skalbarhet. Avdelningen planerar att använda React-komponenterna i Google Material UI för att förbättra användarupplevelsen av formulären samtidigt som man använder backend-funktioner som digitala signaturer, dataintegrering, hantering av affärsprocesser, urkunder och användningsanalys.

Den vanligaste formen bland turister är&quot;Kontakta oss&quot;, som används för att ställa olika frågor och frågor. Den utländska avdelningen har därför valt att börja implementera den Headless adaptive forms-strategi med detta formulär. I den här självstudiekursen får du hjälp med att skapa formuläret Kontakta oss med den nya arkitekturen. Slutresultatet kommer att se ut så här:

![Kontakta US Headless adaptive form](assets/contact-us-headless-adaptive-forms.png)