---
title: Kända problem med Headless Adaptive Forms
description: Kända fel i Headless adaptive forms.
keywords: headless, adaptive form, known issues
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Kända fel {#known-issues}

* Redigerings-, visnings- och datamönster stöds inte. (CQ-4327047)
* minItems-begränsningen kan inte ändras dynamiskt. (CQ-4342499)
* Valideringar på panelnivå genererar inga fel om de överträds. (CQ-4342373)
* Filvalideringar, om de överträds, genererar inga fel. (CQ-4342372)
* Anpassade egenskaper är inte dynamiska. (CQ-4342376)
* Om du ändrar fildata dynamiskt för en change-händelse med uttryck blir en oändlig slinga. (CQ-4342377)
* Den bifogade filen stöder inte hjälptext. (CQ-4342370)
* Den obligatoriska kryssrutan visar inte fel vid sändning, om den inte är markerad. (CQ-4342371)
* aria-label läggs inte till i den bifogade filen. (CQ-4341494)
