---
title: Kända fel i Headless adaptive forms
description: Kända fel i Headless adaptive forms
keywords: headless, adaptive form, known issues
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Kända fel {#known-issues}

* Redigerings-, visnings- och datamönster stöds inte. (CQ-4327047)
* minItems-begränsningen kan inte ändras dynamiskt. (CQ-4342499)
* Valideringar på panelnivå genererar inga fel om de överträds. (CQ-4342373)
* Filvalideringar, om de överträds, genererar inga fel. (CQ-4342372)
* Anpassade egenskaper är inte dynamiska. (CQ-4342376)
* Om du ändrar fildata dynamiskt vid en change-händelse med uttryck blir en oändlig slinga. (CQ-4342377)
* Bifogad fil stöder inte hjälptext. (CQ-4342370)
* Kryssrutan som krävs visar inte fel vid sändning, om den inte är markerad. (CQ-4342371)
* aria-label läggs inte till i den bifogade filen. (CQ-4341494)
