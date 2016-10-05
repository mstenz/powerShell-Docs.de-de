---
title: Verbesserungen beim Debuggen von DSC-Ressourcen
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: 33c3fcffdeb281b205ecc48f7cdd470b79e9e068

---


## Verbesserungen beim Debuggen von DSC-Ressourcen

In WMF 5.0 hat der PowerShell-Debugger bisher nicht direkt an der Klassenressourcenmethode (Get/Set/Test) angehalten.
Wir haben dieses Problem behoben, und der Debugger hält nun bei der Klassenressourcenmethode an, ebenso wie bei den MOF-basierten Ressourcenmethoden.



<!--HONumber=Aug16_HO3-->


